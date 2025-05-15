#Note
2025-05-15

Tags: [[Ebenen]], [[Vektoren]], [[Parameterdarstellung]], [[Koordinatenform]], [[Normalenvektor]], [[Analytische Geometrie]], [[Lineare Algebra]]

---

Ebenen im dreidimensionalen Raum können mit Vektoren beschrieben werden, meist durch die Parameterdarstellung oder die Koordinatenform.

**Parameterdarstellung einer Ebene:**

Eine Ebene E kann durch die Gleichung beschrieben werden:
$$\vec{x} = \vec{p} + \lambda \cdot \vec{q} + \mu \cdot \vec{r}, \quad \lambda, \mu \in \mathbb{R}$$

Dabei gilt:
* $\vec{x}$ ist der Ortsvektor zu einem beliebigen Punkt auf der Ebene.
* $\vec{p}$ ist der **Stützvektor** (Ortsvektor zu einem Punkt auf der Ebene).
* $\vec{q}$ und $\vec{r}$ sind zwei **linear unabhängige Richtungsvektoren**, die die Ebene aufspannen.
* $\lambda$ (Lambda) und $\mu$ (My) sind **Parameter**, die die Lage eines Punktes auf der Ebene bestimmen.

**Koordinatenform einer Ebene:**

Eine Ebene kann auch durch eine lineare Gleichung dargestellt werden:
$$n_1 x_1 + n_2 x_2 + n_3 x_3 = n_0$$
Diese Form wird oft als Skalarprodukt geschrieben: $\vec{n} \cdot \vec{x} = n_0$.

**Normalenvektor:**

Der Vektor $\vec{n} = \begin{pmatrix} n_1 \\ n_2 \\ n_3 \end{pmatrix}$ ist der **Normalenvektor** der Ebene und steht senkrecht auf dieser. Wenn die Ebene durch Richtungsvektoren $\vec{q}$ und $\vec{r}$ gegeben ist, kann ein Normalenvektor durch das **Kreuzprodukt** gefunden werden (im $\mathbb{R}^3$):
$$\vec{n} = \vec{q} \times \vec{r}$$

**Bestimmung von $n_0$:**

Der Wert $n_0$ wird berechnet, indem man den Normalenvektor mit dem Stützvektor (oder einem beliebigen Punkt auf der Ebene) als Skalarprodukt multipliziert:
$$n_0 = \vec{n} \cdot \vec{p}$$
$n_0$ gibt den "Abstand" oder die Lage der Ebene zum Ursprung entlang der Richtung des Normalenvektors an.

---

## Verwendung:

```dataview
list from [[Ebenen]]
```