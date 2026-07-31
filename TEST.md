## Mathematische und Systemische Argumentation: Zero-Copy FPGA-Beschleunigung Binarisierter Vektoren in Pithos

Bevor die konkrete Hardware-Implementierung betrachtet wird, ist eine grundlegende mathematische und systemtheoretische Unterscheidung zwischen **metrischer Äquivalenz** (Invarianz des Suchraums) und **Hardware-Bandbreiteneffizienz** erforderlich.

### Mathematische Äquivalenz und Isometrie (Charikar's Theorem)

Sei der hochdimensionale Vektorraum definiert als $x, q \in \mathbb{R}^d$ mit $\Vert{}x\Vert{}_2 = \Vert{}q\Vert{}_2 = 1$. Die klassische Ähnlichkeitssuche basiert auf der Cosinus-Ähnlichkeit:

$$S_C(q, x) = \langle q, x \rangle = \cos(\theta)$$

Die Binarisierung in Pithos kombiniert eine Rademacher-Preconditioning-Matrix $\mathbf{D} = \operatorname{diag}(\pm 1)$ mit einer ortogonalen Fast Walsh-Hadamard-Transformation $\mathbf{H}_d \in \mathbb{R}^{d \times d}$:

$$\tilde{q} = \mathbf{H}_d \mathbf{D} q$$

Durch die Orthogonalität von $\mathbf{H}_d$ bleibt die $L_2$-Norm invariant. Die anschließende Binarisierung entspricht einer Vorzeichen-Quantisierung:

$$q_{\text{bin}} = \operatorname{sign}(\tilde{q}) \in \{-1, +1\}^d \cong \{0, 1\}^d$$

Nach dem Theorem der zufälligen Hyperebenen-Projektion (Charikar, 2002) entspricht die Wahrscheinlichkeit, dass zwei Komponenten nach der Vorzeichen-Quantisierung unterschiedliche Bits aufweisen, exakt dem Winkel $\theta$ zwischen den Vektoren:

$$\mathbb{P}(q_{\text{bin}, i} \neq x_{\text{bin}, i}) = \frac{\theta}{\pi} = \frac{\arccos(S_C(q, x))}{\pi}$$

Der Erwartungswert der **Hamming-Distanz** $D_H(q_{\text{bin}}, x_{\text{bin}}) = \operatorname{popcount}(q_{\text{bin}} \oplus x_{\text{bin}})$ ist somit eine streng monotone, winkeltreue Transformation der ursprünglichen Cosinus-Distanz:

$$\mathbb{E}[D_H(q_{\text{bin}}, x_{\text{bin}})] = d \cdot \frac{\arccos(\langle q, x \rangle)}{\pi}$$

**Daraus folgt unmittelbar:**

Die Binarisierung stellt keine heuristische Näherung dar, die die geometrische Topologie verwirft. Sie bildet die kontinuierliche Cosinus-Mannigfaltigkeit Isomorph auf einen binären Hamming-Würfel $\mathbb{F}_2^d$ ab. Das relative Ranking (K-Nearest-Neighbors) bleibt in der Ordnungserwartung vollständig erhalten.

### Das Bandbreiten-Paradoxon und die Memory Wall

Bei einer Skalierung auf $N = 3{,}2 \cdot 10^8$ Vektoren (320 Mio.) bei $d = 384$ ergeben sich folgende Speichermuster:

1. **FP32-Repräsentation:**
    
    $$3{,}2 \cdot 10^8 \times 384 \times 4 \text{ Bytes} \approx 491{,}52 \text{ GB}$$
    
    Ein vollständiger Durchlauf erfordert Fließkomma-Rechenleistung ($1{,}22 \cdot 10^{11}$ FLOPs) und scheitert am Hauptspeicher-Durchsatz (Memory Wall).
    
2. **Pithos 1-Bit-Repräsentation:**
    
    $$3{,}2 \cdot 10^8 \times 384 \text{ Bits} = 3{,}2 \cdot 10^8 \times 48 \text{ Bytes} \approx 15{,}36 \text{ GB}$$
    

Durch die Binarisierung sinkt der Speicherbedarf exakt um den Faktor **32**. Der gesamte Datensatz von 320 Mio. Vektoren schrumpft auf **15,36 GB** und passt vollständig in den physischen RAM des Host-Systems.

Die mathematische Komplexität reduziert sich von Fließkomma-Multiplikationen auf bitweise Vektoroperationen:

$$D_H(q_{\text{bin}}, x_{\text{bin}}) = \sum_{j=1}^{d/64} \operatorname{popcount64}\left(q_{\text{bin}, j} \oplus x_{\text{bin}, j}\right)$$

Anstelle von 384 FP32-Multiplikationen genügen **6 Integer-XOR- und Popcount-Befehle** pro Vektor.

### Asymmetrisches Hardware/Software Co-Design

Der Gesamtablauf teilt die Berechnungen strikt nach den Stärken der jeweiligen Hardware-Substrate auf.

```
+--------------------------------------------------------------------------+
| HOST CPU (Pithos Engine / Java 25 Native)                                |
|                                                                          |
|  Query q in R^384 --> [FWHT + Sign] --> Query Bitvector q_bin (48 Bytes) |
|                                              |                           |
|  Off-Heap Memory (FFM Mapped via POSIX mmap):|                           |
|  [Contiguous Tier 0 Buffer (15.36 GB)] <-----+                           |
|         ^                                    | (PCIe BAR Register)       |
+---------|------------------------------------|---------------------------+
          | PCIe DMA Read Stream               v
+---------|----------------------------------------------------------------+
| FPGA HARDWARE ACCELERATOR                                                |
|         |                                                                |
|   +-----v------------------+      +----------------------------------+   |
|   | AXI4-Stream DMA Engine | ---> | Parallel XOR-Popcount PE Array   |   |
|   +------------------------+      | (512-bit / Clock Execution)      |   |
|                                   +----------------+-----------------+   |
|                                                    |                     |
|                                                    v                     |
|                                   +----------------------------------+   |
|                                   | Hardware Top-K Min-Heap Tree     |   |
|                                   +----------------+-----------------+   |
|                                                    |                     |
|   Return Top-K Indices & Distances <---------------+                     |
+--------------------------------------------------------------------------+
```

#### 1. Host-CPU (Aufbereitung)

Für den einzelnen Suchvektor $q \in \mathbb{R}^{384}$ führt die CPU die Transformation aus:

$$\tilde{q} = \mathbf{H}_{384} \mathbf{D} q \implies q_{\text{bin}} = \operatorname{sign}(\tilde{q})$$

Da $d = 384$ klein ist, benötigt die CPU für diesen Schritt via Fast Walsh-Hadamard Transformation $O(d \log d)$ weniger als **$1\,\mu\text{s}$**.

#### 2. FPGA (Massive Streaming Search)

Die CPU übergibt lediglich das 48-Byte-Ergebnis $q_{\text{bin}}$ und die off-heap Speicheradresse an den FPGA. Der FPGA übernimmt das Durchsuchen des 15,36-GB-Puffers:

- **Zero-Copy DMA:** Über die Funktion `vdb_get_tier_address` erhält der FPGA-DMA-Controller die direkte physische/virtuelle RAM-Adresse des speicherintegrierten Index. Es findet **kein Umkopieren** im Host-Speicher statt (Zero-Copy).
    
- **Line-Rate Pipeline:** Der FPGA liest den RAM über PCIe-DMA mit voller Bus-Bandbreite (z. B. PCIe Gen4 $\approx 31{,}5 \text{ GB/s}$) als kontinuierlichen AXI4-Stream.
    
- **Parallel Execution Elements (PEs):** Bei einer Busbreite von $512 \text{ Bits}$ verarbeitet das FPGA-Fabric pro Taktzyklus mehr als einen vollständigen 384-Bit-Vektor:
    

$$\text{Throughput}_{\text{FPGA}} = f_{\text{clk}} \times \text{PEs}_{\text{parallel}}$$

Bei $f_{\text{clk}} = 300 \text{ MHz}$ und 64 parallelen PEs verarbeitet der FPGA **19,2 Milliarden Vektortransformationen pro Sekunde**.

- **Top-K Hardware Filtering:** Ein kaskadierter Min-Heap-Sortierer im FPGA-BRAM sammelt während des Streamings direkt die $K$ kleinsten Distanzen.
    

### Einordnung der Systemarchitektur (Pithos Off-Heap Layer)

Eine Entkopplung der CPU-Last wird nicht durch den FPGA alleine erreicht, sondern durch das Speicher-Layout von Pithos:

1. **GC-Bypass & Memory Alignment:**
    
    Das Speicher-Layout nutzt die Java 25 Foreign Function & Memory (FFM) API in Kombination mit POSIX `mmap`. Die Vektoren liegen in contiguen, seiten-ausgerichteten (4KB-aligned) Off-Heap-Speicherblöcken ohne JVM-Garbage-Collection-Overhead.
    
2. **Matryoshka Energy Budget ($\tau$):**
    
    Durch den Spektralzerlegungs-Aufbau der Matryoshka-Embeddings sind die vorderen Bits der Vektoren mit höherer Varianz geladen. Die Hamming-Distanz kann bereits auf Sub-Tiers (z. B. den ersten 128 Bits) evaluiert werden, um Kandidaten frühzeitig zu verwerfen:
    

$$D_H^{(128)}(q_{\text{bin}}, x_{\text{bin}}) > T_{\text{threshold}} \implies \text{Early Pruning}$$

### Zusammenfassung der Argumentation für das Co-Design

Das Gesamtsystem basiert auf einer strikten mathematischen und hardwaretechnischen Aufgaben-Isolation:

1. **Mathematische Verlustfreiheit:** FWHT + Binarisierung überführt Cosinus-Distanzen streng monoton in den Hamming-Raum $\mathbb{F}_2^d$.
    
2. **Speicher-Kompression:** Der Datenstrom schrumpft von 491,5 GB auf 15,36 GB und wird rein sequentiell-dma-fähig.
    
3. **Latenz-Minimierung:** Die CPU berechnet die Abfrage-Transformation in $O(d \log d)$ ($< 1\,\mu\text{s}$), während der FPGA die 15,36 GB Daten ohne CPU-Intervention über PCIe-DMA bei maximaler Bus-Bandbreite in wenigen Millisekunden abgrast.
    

Das System eliminiert die Memory Wall nicht durch höhere Rechenleistung, sondern durch die mathematische Transformation des Metrikraums in Kombination mit physikalischem Zero-Copy-Streaming.