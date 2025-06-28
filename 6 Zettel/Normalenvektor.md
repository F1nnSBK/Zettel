#Note
2025-05-15

Tags: [[Normalenvektor]], [[Vektoren]], [[Ebenen]], [[Koordinatenform]], [[Kreuzprodukt]], [[Analytische Geometrie]]

---

Ein Normalenvektor ist ein spezieller [[Vektoren|Vektor]], der **orthogonal (senkrecht)** auf einem geometrischen Objekt steht, wie z. B. einer [[Ebenen|Ebene]] oder einer Fläche.

**Rolle und Bedeutung:**

Der Normalenvektor $\vec{n}$ gibt die "Ausrichtung" oder "Richtung" an, in die das Objekt im Raum "schaut". Er ist von zentraler Bedeutung für die [[Koordinatenform]] einer Ebene. In der Koordinatenform $n_1 x_1 + n_2 x_2 + n_3 x_3 = n_0$ sind die Koeffizienten $n_1, n_2, n_3$ die Komponenten des Normalenvektors $\vec{n} = \begin{pmatrix} n_1 \\ n_2 \\ n_3 \end{pmatrix}$.

**Bestimmung (für eine Ebene im $\mathbb{R}^3$):**

Wenn eine [[Ebenen|Ebene]] in [[Parameterdarstellung]] durch einen Stützvektor $\vec{p}$ und zwei linear unabhängige Richtungsvektoren $\vec{q}$ und $\vec{r}$ gegeben ist ($\vec{x} = \vec{p} + \lambda \cdot \vec{q} + \mu \cdot \vec{r}$), kann ein Normalenvektor $\vec{n}$ mithilfe des [[Kreuzprodukt]]s der beiden Richtungsvektoren berechnet werden (dies gilt speziell im dreidimensionalen Raum $\mathbb{R}^3$):
$$\vec{n} = \vec{q} \times \vec{r}$$
Das Ergebnis des Kreuzprodukts ist ein Vektor, der per Definition senkrecht auf beiden Vektoren $\vec{q}$ und $\vec{r}$ steht und somit senkrecht auf der von ihnen aufgespannten Ebene.

Jedes skalare Vielfache $k \cdot \vec{n}$ (mit $k \neq 0$) ist ebenfalls ein Normalenvektor derselben Ebene, hat aber eine andere Länge oder zeigt in die entgegengesetzte Richtung. Oft verwendet man einen normierten Normalenvektor (Einheitsvektor der Länge 1).

---

## Verwendung:

```dataview
list from [[Normalenvektor]]
```