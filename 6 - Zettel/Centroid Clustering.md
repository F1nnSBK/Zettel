#Note

2026-06-24

Tags: [[Unsupervised Learning]], [[Clustering]], [[K-Means]]
#UL

---

## Kapitel 2 – Centroid Clustering

> *"Same Same but Different."*

### The Why

Nachdem Kapitel 1 Distanz als engineerbares Konzept eingeführt hat, stellt sich die Frage: Wie formalisiert man Cluster mathematisch? **K-Means** produziert eine *harte Partition* – jeder Punkt gehört zu genau einem Cluster.

**Lernziele:**
- K-Means Zielfunktion und Algorithmus verstehen, inkl. Konvergenz
- Initialisierungsstrategien und K-Auswahl anwenden
- Erkennen, wann K-Means versagt und warum

---

### Theorie

#### Definitionen

- **Datenpunkt:** $x_i \in \mathbb{R}^d$, $i = 1, \ldots, n$
- **Cluster:** nicht-leere Teilmenge $C_k \subseteq \{x_1, \ldots, x_n\}$, disjunkt: $C_j \cap C_k = \emptyset$
- **Clustering:** Kollektion $\{C_1, \ldots, C_K\}$ mit $\bigcup_{k=1}^K C_k = \{x_1, \ldots, x_n\}$
- **Centroid:** $\mu_k = \frac{1}{|C_k|} \sum_{x_i \in C_k} x_i$ (Schwerpunkt, muss kein Datenpunkt sein)

#### Zielfunktion: Inertia / WCSS

$$J = \sum_{k=1}^{K} \sum_{x_i \in C_k} \|x_i - \mu_k\|^2$$

Minimierung ist NP-schwer → K-Means findet nur **lokales Optimum**.

#### Der Algorithmus (Lloyd's Algorithm)

```
Initialisiere K Zentroiden μ₁, ..., μ_K
Wiederhole:
  Assignment: c_i ← argmin_k ‖x_i - μ_k‖²  (für jedes x_i)
  Update:     μ_k ← Mittelwert aller x_i mit c_i = k
Bis Zuweisungen unverändert
```

**Konvergenz:** Garantiert (J sinkt monoton), aber nicht zum globalen Minimum.
**Komplexität:** $O(n \cdot K \cdot d)$ pro Iteration.

---

### Initialisierung

| Methode | Beschreibung | Nachteil |
|---|---|---|
| Random | Zufällige Punkte als Startzentroiden | Sehr sensitiv, viele Neustarts nötig |
| K-Means++ | Nächster Zentroid wird proportional zu $d^2$ gewählt | Standard heute, besser verteilt |
| Forgy | Wählt K zufällige Datenpunkte | Besser als Random |

#### K-Auswahl: Elbow-Methode

Plotte J gegen K. Der „Knick" (Elbow) markiert den sinnvollen K-Wert.
Algorithmisch: **Kneedle**-Algorithmus (Satopaa et al., 2011) – normalisiert beide Achsen, findet das Maximum der Kurven-Diagonalen-Differenz.

#### Silhouette-Koeffizient

$$s(i) = \frac{b(i) - a(i)}{\max(a(i), b(i))}$$

- $a(i)$: mittlere Distanz zu Punkten im eigenen Cluster
- $b(i)$: mittlere Distanz zum nächsten fremden Cluster
- $s \in [-1, 1]$: je näher 1, desto besser

---

### Grenzen von K-Means

| Problem | Ursache |
|---|---|
| Nicht-konvexe Cluster | Centroid-Annahme erzwingt sphärische Cluster |
| Ausreißer-Sensitivität | Ausreißer ziehen Zentroiden stark zu sich |
| K muss vorgegeben werden | Keine automatische Cluster-Anzahl |
| Nicht-deterministisch | Initialisierung beeinflusst Ergebnis |

---

### Übungen

#### Aufgabe 1
Trace K-Means auf 3 Punkten $x_1=(1,3), x_2=(3,2), x_3=(4,3)$ mit $K=2$, Startzentroiden $\mu_1=(1,4), \mu_2=(4,1)$.

**Lösung:**

*Iteration 1 – Assignment:*
- $d(x_1, \mu_1) = \sqrt{0+1} = 1$, $d(x_1, \mu_2) = \sqrt{9+4} = 3.6$ → $x_1 \to C_1$
- $d(x_2, \mu_1) = \sqrt{4+4} = 2.83$, $d(x_2, \mu_2) = \sqrt{1+1} = 1.41$ → $x_2 \to C_2$
- $d(x_3, \mu_1) = \sqrt{9+1} = 3.16$, $d(x_3, \mu_2) = \sqrt{0+4} = 2$ → $x_3 \to C_2$

*Iteration 1 – Update:*
- $\mu_1 = (1,3)$, $\mu_2 = (3.5, 2.5)$

*Iteration 2 – Assignment:* Gleiche Zuweisungen → **Konvergenz.**

#### Aufgabe 2
Warum ist Minimierung von J NP-schwer? Warum konvergiert K-Means trotzdem?

**Lösung:**
NP-schwer weil es $K^n$ mögliche Partitionen gibt (exponentiell). K-Means konvergiert weil jeder Schritt J monoton senkt (Assignment-Schritt: jeder Punkt zum nächsten Zentroiden; Update-Schritt: Mittelwert minimiert quadratischen Abstand). Endlich viele Partitionen → terminiert. Aber lokales, nicht globales Minimum.

---

#### Flashcards

Was minimiert K-Means?::Die Inertia $J = \sum_k \sum_{x_i \in C_k} \|x_i - \mu_k\|^2$ (Within-Cluster Sum of Squares).

Warum ist K-Means nicht-deterministisch?::Die Initialisierung der Zentroiden ist zufällig. Verschiedene Startpositionen führen zu verschiedenen lokalen Minima.

Was ist der Unterschied zwischen Assignment- und Update-Schritt?
?
**Assignment:** Jeder Punkt wird dem nächsten Zentroiden zugewiesen: $c_i \leftarrow \arg\min_k \|x_i - \mu_k\|^2$.
**Update:** Jeder Zentroid wird auf den Mittelwert seiner zugewiesenen Punkte gesetzt: $\mu_k \leftarrow \frac{1}{|C_k|} \sum_{x_i: c_i=k} x_i$.

Was ist der Silhouette-Koeffizient und wie wird er interpretiert?::$s(i) = \frac{b(i)-a(i)}{\max(a(i),b(i))}$. Werte nahe 1: gut im eigenen Cluster. Werte nahe 0: auf der Grenze. Werte nahe -1: falsch zugeordnet.

Warum versagt K-Means bei Ring-förmigen Clustern?::K-Means nimmt sphärische, konvexe Cluster an (Centroid = Schwerpunkt). Bei Ring-Formen liegt der Centroid in der Mitte des Rings, wo keine Datenpunkte sind.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[02 Centroid Clustering]]
SORT file.mtime DESC
```
