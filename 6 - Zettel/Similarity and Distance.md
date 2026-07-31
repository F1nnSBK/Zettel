#Note

2026-06-24

Tags: [[Unsupervised Learning]], [[Distance Metrics]], [[Feature Space]]
#UL

---

## Kapitel 1 – Similarity and Distance

> *"Enter the Feature Space"*

### The Why

Im Gegensatz zum **Supervised Learning**, bei dem Daten $x$ mit Ground-Truth-Labels $\tilde{y}$ vorliegen und ein Modell $\theta$ die Abbildung $\theta(x) \approx \tilde{y}$ lernt, fehlen im Unsupervised Learning die Labels. Das Ziel ist es, inhärente Strukturen und Muster in den Daten selbst zu entdecken.

**Lernziele:**
- Verständnis der zentralen Rolle von Distanz und Ähnlichkeit im Unsupervised Learning
- Berechnung und Interpretation gängiger Distanzmetriken (Euklidisch, Manhattan, Cosinus, Mahalanobis)
- Anwendung geeigneter Normalisierungs- und Skalierungsstrategien

---

### Theorie

#### Distanzfunktion

Eine Distanzfunktion $d: X \times X \to \mathbb{R}_{\geq 0}$ muss folgende Eigenschaften erfüllen:

| Eigenschaft | Formal |
|---|---|
| Nicht-Negativität | $d(x, y) \geq 0$ |
| Identität | $d(x, y) = 0 \iff x = y$ |
| Symmetrie | $d(x, y) = d(y, x)$ |
| Dreiecksungleichung | $d(x, z) \leq d(x, y) + d(y, z)$ |

#### Euklidische Distanz (L2)

$$d_{\text{Euclidean}}(x, y) = \sqrt{\sum_{i=1}^{n} (x_i - y_i)^2} = \|x - y\|_2$$

Annahme: Alle Dimensionen gleich wichtig und in gleichen Einheiten gemessen.

**Beispiel:** $A=(3,1), B=(6,8)$: $d(A,B) = \sqrt{9 + 49} = \sqrt{58} \approx 7.62$

#### Manhattan Distanz (L1)

$$d_{\text{Manhattan}}(x, y) = \sum_{i=1}^{n} |x_i - y_i| = \|x - y\|_1$$

Misst die achsenparallele Wegstrecke entlang eines Gitters. Robuster gegenüber Ausreißern.

#### Cosinus-Ähnlichkeit

$$\cos(x, y) = \frac{x \cdot y}{\|x\| \cdot \|y\|}$$

Misst den Winkel zwischen Vektoren statt die absolute Distanz. Magnitude wird ignoriert.
- $\cos = 1$: identisch (gleiche Richtung)
- $\cos = 0$: orthogonal
- $\cos = -1$: entgegengesetzt

**Anwendung:** NLP, Embeddings, semantische Ähnlichkeit.

#### Mahalanobis-Distanz

$$d_M(x, y) = \sqrt{(x-y)^T \Sigma^{-1} (x-y)}$$

Berücksichtigt die Kovarianzstruktur $\Sigma$ der Daten. Normalisiert für unterschiedliche Skalierungen und Korrelationen. Ist invariant unter linearen Transformationen des Feature-Raums.

---

### Normalisierung

**Z-Score-Normalisierung:** $x' = \frac{x - \mu}{\sigma}$ – Mittelwert 0, Standardabweichung 1.

**Min-Max-Skalierung:** $x' = \frac{x - x_{\min}}{x_{\max} - x_{\min}}$ – Skaliert auf $[0, 1]$.

**Wann notwendig:** Bei Distanzmetriken die von der Skalierung abhängen (Euklidisch, Manhattan). Cosinus-Ähnlichkeit und Mahalanobis sind relativ robust.

---

### Übungen

#### Aufgabe 1
Berechne die euklidische und Manhattan-Distanz zwischen $A = (1, 2)$ und $B = (4, 6)$.

**Lösung:**
- Euklidisch: $d = \sqrt{(4-1)^2 + (6-2)^2} = \sqrt{9+16} = \sqrt{25} = 5$
- Manhattan: $d = |4-1| + |6-2| = 3 + 4 = 7$

#### Aufgabe 2
Warum versagt die Euklidische Distanz bei Features mit unterschiedlichen Einheiten (z.B. Alter und Einkommen)?

**Lösung:**
Euklidische Distanz behandelt alle Dimensionen als gleichwertig. Einkommen in Tausend Euro dominiert die Distanz gegenüber Alter in Jahren, obwohl Alter semantisch genauso relevant sein kann. Z-Score-Normalisierung korrigiert das.

#### Aufgabe 3
Wann ist Cosinus-Ähnlichkeit gegenüber Euklidischer Distanz zu bevorzugen?

**Lösung:**
Wenn die Richtung (Orientierung) des Vektors wichtiger ist als seine Magnitude. Typisch in NLP: Dokumente mit gleicher Thematik aber unterschiedlicher Länge haben einen ähnlichen Winkel, aber unterschiedliche Längen. Cosinus ignoriert die Länge und fokussiert auf die Richtungsstruktur.

---

#### Flashcards

Welche vier Eigenschaften muss eine Distanzfunktion erfüllen?::Nicht-Negativität, Identität, Symmetrie, Dreiecksungleichung

Was ist der Unterschied zwischen L1 und L2 Distanz?::L1 (Manhattan) summiert absolute Differenzen, L2 (Euklidisch) nimmt die Wurzel der Summe der quadrierten Differenzen. L2 bestraft große Abweichungen stärker.

Was berücksichtigt die Mahalanobis-Distanz gegenüber der Euklidischen?
?
Die Kovarianzstruktur der Daten ($\Sigma^{-1}$). Sie normalisiert für unterschiedliche Skalierungen und Korrelationen zwischen Features. $d_M(x, y) = \sqrt{(x-y)^T \Sigma^{-1} (x-y)}$

Wann sollte Cosinus-Ähnlichkeit statt Euklidischer Distanz verwendet werden?::Wenn die Richtung des Vektors (semantische Ausrichtung) wichtiger ist als seine Magnitude – typisch in NLP und Embedding-Räumen.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[01 Similarity and Distance]]
SORT file.mtime DESC
```
