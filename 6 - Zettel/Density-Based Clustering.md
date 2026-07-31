#Note

2026-06-24

Tags: [[Unsupervised Learning]], [[Clustering]], [[DBSCAN]]
#UL

---

## Kapitel 4 – Density-Based Clustering

> *"It is all about that space, about that space."*

### The Why

K-Means und Hierarchical Clustering weisen **jeden** Punkt einem Cluster zu. Reale Daten enthalten Rauschen: GPS-Ausreißer, Sensor-Dropouts, echte Anomalien. Density-based Clustering kann Punkte als **Rauschen** labeln, statt sie zu erzwingen.

**Vorteile gegenüber K-Means / Hierarchical:**
- Beliebig geformte Cluster (nicht nur sphärisch)
- Automatische Bestimmung von K aus den Daten
- Explizite Rausch-Erkennung
- Keine Centroid-Annahme

**Lernziele:**
- DBSCAN per Hand tracen; $\varepsilon$ und $n_{\min}$ aus den Daten bestimmen
- Core-, Border- und Noise-Punkte formalisieren
- Versagensfälle von DBSCAN erkennen

---

### Theorie

#### Parameter

- $\varepsilon$: Radius der Nachbarschaft
- $n_{\min}$: Mindestanzahl Punkte für einen Core-Point (inkl. sich selbst)

#### Punkt-Klassifikation

$$N_\varepsilon(p) = \{q \in X : d(p, q) \leq \varepsilon\}$$

| Typ | Bedingung |
|---|---|
| **Core Point** $p_c$ | $|N_\varepsilon(p_c)| \geq n_{\min}$ |
| **Border Point** $p_b$ | $|N_\varepsilon(p_b)| < n_{\min}$ aber $p_b \in N_\varepsilon(p_c)$ für einen Core Point $p_c$ |
| **Noise Point** $p_n$ | Weder Core noch Border |

#### Dichte-Erreichbarkeit

- **Density-reachable:** $q$ ist von $p$ erreichbar, wenn es eine Kette $p = p_1, p_2, \ldots, p_m = q$ gibt, wobei jedes $p_i$ ein Core Point ist und $p_{i+1} \in N_\varepsilon(p_i)$.
- **Nicht symmetrisch:** $p_b$ ist von $p_c$ erreichbar, aber nicht umgekehrt.
- **Density-connected:** $p$ und $q$ sind verbunden, wenn es einen $o$ gibt von dem beide erreichbar sind.

#### Der Algorithmus

```
Für jeden Punkt p in X:
  Wenn p schon gelabelt: skip
  Berechne N_ε(p)
  Wenn |N_ε(p)| < n_min: label p als Noise (vorläufig)
  Sonst: starte neuen Cluster C
    Füge alle Punkte in N_ε(p) zur Queue
    Für jedes q in Queue:
      Wenn q Noise war: ändere zu Border in C
      Wenn q noch unlabelt: label q als C
        Wenn |N_ε(q)| ≥ n_min: füge N_ε(q) zur Queue
```

#### Komplexität

- Mit Spatial Index (k-d-tree): $O(n \log n)$
- Ohne Index: $O(n^2)$

---

### Parameter-Wahl

#### $\varepsilon$ aus k-Distance-Plot

1. Für jeden Punkt: berechne Distanz zum $k$-ten Nachbarn ($k = n_{\min} - 1$)
2. Sortiere absteigend, plotte
3. **Knick** im Plot = guter $\varepsilon$-Wert (Übergang dicht→dünn)

#### $n_{\min}$ Faustregeln

- $n_{\min} \geq d + 1$ (wobei $d$ = Dimensionalität)
- Für verrauschte Daten: höher wählen
- Standard: $n_{\min} = 4$ oder $2 \cdot d$

---

### Grenzen von DBSCAN

| Problem | Ursache |
|---|---|
| Variierende Dichte | Ein globales $\varepsilon$ passt nicht zu Clustern unterschiedlicher Dichte |
| Hohe Dimensionalität | Curse of Dimensionality: alle Abstände konvergieren, $\varepsilon$-Nachbarschaften leeren sich |
| Cluster gleicher Dichte mit Brücken | Dünne Verbindung kann zwei Cluster fusionieren |

**OPTICS** (Ordering Points To Identify the Clustering Structure): Erweiterung für variierende Dichten – erstellt Reachability-Plot statt flacher Partition.

---

### Übungen

#### Aufgabe 1
Gegeben 7 Punkte mit $\varepsilon = 2.5$, $n_{\min} = 3$. $x_7 = (4,5)$ hat nur sich selbst in $N_\varepsilon$. Welcher Typ ist $x_7$?

**Lösung:**
$|N_\varepsilon(x_7)| = 1 < 3 = n_{\min}$ → $x_7$ ist kein Core Point. Da kein Core Point $x_7$ in seiner $\varepsilon$-Nachbarschaft hat, ist $x_7$ auch kein Border Point. → $x_7$ ist ein **Noise Point** $p_n$.

#### Aufgabe 2
Warum ist Dichte-Erreichbarkeit nicht symmetrisch?

**Lösung:**
Erreichbarkeit propagiert nur von Core Points ausgehend. Ein Border Point $p_b$ kann von einem Core Point $p_c$ aus erreichbar sein ($p_b \in N_\varepsilon(p_c)$), aber $p_c$ ist nicht von $p_b$ aus erreichbar, weil $p_b$ kein Core Point ist und Erreichbarkeit nur von Core Points ausgeht.

---

#### Flashcards

Was ist der Unterschied zwischen Core-, Border- und Noise-Punkt?
?
- **Core:** $|N_\varepsilon(p)| \geq n_{\min}$ – dicht genug um Cluster zu starten
- **Border:** Nicht dicht genug, aber in der Nachbarschaft eines Core Points
- **Noise:** Weder Core noch Border – isolierter Ausreißer

Wie wählt man $\varepsilon$ bei DBSCAN?::Mit dem k-Distance-Plot: Distanz zum k-ten Nachbarn für alle Punkte sortiert plotten. Der Knick (starker Anstieg) zeigt den Übergang von dicht zu dünn – das ist ein guter $\varepsilon$-Wert.

Wann versagt DBSCAN?::Bei stark variierenden Dichten (ein globales $\varepsilon$ passt nicht zu allen Clustern gleichzeitig) und bei hoher Dimensionalität (Curse of Dimensionality leert die Nachbarschaften).

Was ist der Vorteil von OPTICS gegenüber DBSCAN?::OPTICS erzeugt keinen globalen $\varepsilon$-Parameter, sondern einen Reachability-Plot der Cluster verschiedener Dichten in einer Struktur kodiert. Man kann nachträglich verschiedene Dichte-Schwellen auslesen.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[04 Density-Based Clustering]]
SORT file.mtime DESC
```
