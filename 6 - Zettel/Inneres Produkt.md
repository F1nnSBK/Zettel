#Note

2025-05-18

Tags: [[Inneres Produkt]], [[Vektorräume]], [[Lineare Algebra]], [[Norm]], [[Orthogonalität]], [[Skalarprodukt]], [[Analytische Geometrie]]

---

Ein **Inneres Produkt** ist eine Funktion auf einem [[Vektorräume|Vektorraum]] $V$, die jedem Paar von [[Vektoren]] $v, w \in V$ einen [[Skalar]] zuordnet (typischerweise eine reelle oder komplexe Zahl). Es ist eine Verallgemeinerung des [[Skalarprodukt|Skalarprodukts]] im $\mathbb{R}^n$.

**Definition:**

Eine Funktion $\langle \cdot, \cdot \rangle: V \times V \to \mathbb{R}$ ist ein Inneres Produkt auf einem [[Vektorräume|Vektorraum]] $V$ über den reellen Zahlen, wenn sie für alle $v, w, u \in V$ und alle [[Skalar|Skalare]] $\alpha, \beta \in \mathbb{R}$ die folgenden drei [[Eigenschaften]] (Axiome) erfüllt:

1.  **Symmetrie:** Das innere Produkt ist symmetrisch bezüglich seiner Argumente.
    $$ \langle v, w \rangle = \langle w, v \rangle $$
2.  **Linearität im ersten Argument:** Das innere Produkt ist linear bezüglich des ersten Arguments. Aufgrund der Symmetrie ist es auch linear bezüglich des zweiten Arguments.
    $$ \langle \alpha v + \beta w, u \rangle = \alpha \langle v, u \rangle + \beta \langle w, u \rangle $$
3.  **Positive Definitheit:** Das innere Produkt eines Vektors mit sich selbst ist nicht-negativ und nur dann Null, wenn der Vektor der [[Nullvektor]] ist.
    $$ \langle v, v \rangle \ge 0 \quad \text{und} \quad \langle v, v \rangle = 0 \iff v = \vec{0} $$

Ein [[Vektorräume|Vektorraum]] zusammen mit einem definierten Inneren Produkt heißt **Innerer Produktraum**.

**Verbindungen zu anderen Konzepten:**

* **Induzierte [[Norm]]:** Jedes Innere Produkt induziert eine [[Norm]] auf dem [[Vektorräume|Vektorraum]], definiert als die Wurzel des inneren Produkts eines Vektors mit sich selbst:
    $$ ||v|| = \sqrt{\langle v, v \rangle} $$
    Ein Innerer Produktraum ist somit auch ein normierter Raum und damit auch ein metrischer Raum.
* **[[Orthogonalität]]:** Zwei [[Vektoren]] $v$ und $w$ sind **orthogonal** zueinander, wenn ihr Inneres Produkt Null ist: $\langle v, w \rangle = 0$.
* **Winkel:** Das Innere Produkt kann verwendet werden, um den Winkel zwischen zwei [[Vektoren]] zu definieren (für $\vec{v}, \vec{w} \neq \vec{0}$): $\cos(\theta) = \frac{\langle v, w \rangle}{||v|| \cdot ||w||}$. Dies basiert auf der **Cauchy-Schwarz-Ungleichung**: $|\langle v, w \rangle| \le ||v|| \cdot ||w||$.
* **[[Skalarprodukt]]:** Das Standard-[[Skalarprodukt]] im $\mathbb{R}^n$, definiert als $\vec{x} \cdot \vec{y} = \vec{x}^T \vec{y} = \sum_{i=1}^n x_i y_i$, ist das kanonische Beispiel für ein Inneres Produkt.

Innere Produkte spielen eine wichtige Rolle in vielen Bereichen der Mathematik, Physik und Ingenieurwissenschaften, da sie es ermöglichen, geometrische Konzepte wie Länge, Winkel und Orthogonalität in abstrakten Vektorräumen zu definieren.

---

## Verwendung:

```dataview
list from [[Inneres Produkt]]
```