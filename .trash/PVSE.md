#Note

2026-06-12

Tags: [[]], [[]], [[]]
#

---
Während klassische NoSQL-Datenbanken Daten nach Schlüsseln oder Graphen-Kanten durchsuchen, erfordert das KI-Zeitalter die Suche nach **semantischer Ähnlichkeit**. Die **Pithos Vector Search Engine** ist eine minimalistische, hochperformante Implementierung genau dieses Paradigmas, spezialisiert auf _Lunar Pit Detection_.

Die Mathematik der Vektor-Suche (Vector Similarity)

Ein Embedding ist ein mathematischer Vektor V∈Rd, der die Eigenschaften eines Objekts in einem d-dimensionalen Raum abbildet.

In Standard-Vektordatenbanken wird die Ähnlichkeit zwischen einem Suchvektor Q und einem Datenbankvektor X meist über die **Kosinus-Ähnlichkeit** (Cosine Similarity) berechnet, indem man das Skalarprodukt durch das Produkt der Normen teilt: SC​(Q,X)=∣∣Q∣∣∣∣X∣∣Q⋅X​=∑qi2​![](data:image/svg+xml;utf8,<svg%20xmlns="http://www.w3.org/2000/svg"%20width="400em"%20height="1.5429em"%20viewBox="0%200%20400000%201080"%20preserveAspectRatio="xMinYMin%20slice"><path%20d="M95,702%0Ac-2.7,0,-7.17,-2.7,-13.5,-8c-5.8,-5.3,-9.5,-10,-9.5,-14%0Ac0,-2,0.3,-3.3,1,-4c1.3,-2.7,23.83,-20.7,67.5,-54%0Ac44.2,-33.3,65.8,-50.3,66.5,-51c1.3,-1.3,3,-2,5,-2c4.7,0,8.7,3.3,12,10%0As173,378,173,378c0.7,0,35.3,-71,104,-213c68.7,-142,137.5,-285,206.5,-429%0Ac69,-144,104.5,-217.7,106.5,-221%0Al0%20-0%0Ac5.3,-9.3,12,-14,20,-14%0AH400000v40H845.2724%0As-225.272,467,-225.272,467s-235,486,-235,486c-2.7,4.7,-9,7,-19,7%0Ac-6,0,-10,-1,-12,-3s-194,-422,-194,-422s-65,47,-65,47z%0AM834%2080h400000v40h-400000z"></path></svg>)​∑xi2​![](data:image/svg+xml;utf8,<svg%20xmlns="http://www.w3.org/2000/svg"%20width="400em"%20height="1.5429em"%20viewBox="0%200%20400000%201080"%20preserveAspectRatio="xMinYMin%20slice"><path%20d="M95,702%0Ac-2.7,0,-7.17,-2.7,-13.5,-8c-5.8,-5.3,-9.5,-10,-9.5,-14%0Ac0,-2,0.3,-3.3,1,-4c1.3,-2.7,23.83,-20.7,67.5,-54%0Ac44.2,-33.3,65.8,-50.3,66.5,-51c1.3,-1.3,3,-2,5,-2c4.7,0,8.7,3.3,12,10%0As173,378,173,378c0.7,0,35.3,-71,104,-213c68.7,-142,137.5,-285,206.5,-429%0Ac69,-144,104.5,-217.7,106.5,-221%0Al0%20-0%0Ac5.3,-9.3,12,-14,20,-14%0AH400000v40H845.2724%0As-225.272,467,-225.272,467s-235,486,-235,486c-2.7,4.7,-9,7,-19,7%0Ac-6,0,-10,-1,-12,-3s-194,-422,-194,-422s-65,47,-65,47z%0AM834%2080h400000v40h-400000z"></path></svg>)​∑i=1d​qi​xi​​

**Der Pithos-Vorteil (Binary Embeddings):** Da Fließkomma-Berechnungen (Float32) bei Milliarden von Vektoren zu Memory- und CPU-Bottlenecks führen, arbeitet Pithos mit **binären Embeddings** B∈{0,1}d. Hier transformiert sich die komplexe Kosinus-Ähnlichkeit in die rasend schnelle **Hamming-Distanz** DH​. Die Distanz ist schlichtweg die Anzahl der Bits, in denen sich zwei Vektoren voneinander unterscheiden. Auf Prozessor-Ebene (ALU) lässt sich dies maschinennah in sehr wenigen Takt-Zyklen berechnen: DH​(Q,X)=POPCOUNT(Q⊕X) _(Wobei_ ⊕ _das logische, bitweise XOR darstellt und POPCOUNT die Anzahl der resultierenden Einsen / gesetzten Bits zählt)._

Matryoshka Representation Learning (MRL)

Pithos nutzt Matryoshka-strukturierte Embeddings. Bei klassischen Embeddings ist die Information gleichmäßig über alle Dimensionen d verteilt. MRL zwingt das neuronale Netz beim Training, die wichtigste Varianz (Information) konzentriert in die vordersten Dimensionen zu packen.

Mathematisch wird dies durch eine verschachtelte Verlustfunktion (Nested Loss Function) beim Training des Modells erreicht: LMRL​=∑m∈M​cm​L(m) _(Wobei_ M _die Teilmengen der Dimensionen z. B._ {8,16,32,...,d} _sind und_ cm​ _die jeweilige Gewichtung darstellt)._

**Der architektonische Hebel:** Für Pithos bedeutet das: Wenn der Arbeitsspeicher für eine _Exhaustive Search_ (O(N×d)) nicht ausreicht, kann Pithos den Vektor X einfach bei einer Dimension m<d abschneiden, ohne dass die Ähnlichkeitssuche völlig in sich zusammenbricht. Das System kann so einen Trade-off zwischen Such-Präzision und RAM-Limitierungen steuern.

Hardware-Software-Co-Design

Um den Garbage-Collector von klassischen Hochsprachen zu umgehen und das Maximum an I/O-Performance herauszuholen, ist Pithos extrem Hardware-nah konstruiert. Durch Schnittstellen wie die **GraalVM C-API** kann das System den Speicher direkt verwalten (z.B. über Memory-Mapped Files oder direkte Pointer), was es von klassischen Backend-Datenbanken radikal unterscheidet.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[PVSE]]
SORT file.mtime DESC
```