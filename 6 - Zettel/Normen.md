#Note

2025-05-15

Tags: [[Normen]], [[Vektoren]], [[3 - Tags/Grundlagen]], [[Operationen]], [[Mathematik]]

---

Eine Norm ist eine Funktion, die jedem [[Vektoren|Vektor]] $\vec{x}$ in einem Vektorraum einen **nicht-negativen Skalar** zuordnet, der als seine "Länge" oder sein "Betrag" interpretiert wird. Die Notation für eine Norm ist meist $||\vec{x}||$.

**Eigenschaften einer Norm:**

Eine Funktion $||\cdot||: \mathbb{R}^n \to \mathbb{R}$ muss die folgenden drei Eigenschaften erfüllen, um eine Norm zu sein:

1.  **Dreiecksungleichung:** Die Länge der Summe zweier Vektoren ist kleiner oder gleich der Summe ihrer Längen.
    $$||\vec{x} + \vec{y}|| \le ||\vec{x}|| + ||\vec{y}|| \quad \forall \vec{x}, \vec{y} \in \mathbb{R}^n$$
2.  **Absolute Homogenität:** Wenn ein Vektor mit einem Skalar multipliziert wird, skaliert sich seine Norm mit dem Betrag des Skalars.
    $$||s\vec{x}|| = |s| \cdot ||\vec{x}|| \quad \forall \vec{x} \in \mathbb{R}^n, s \in \mathbb{R}$$
3.  **Definitheit:** Die Norm eines Vektors ist genau dann Null, wenn es sich um den Nullvektor handelt.
    $$||\vec{x}|| = 0 \iff \vec{x} = \vec{0}$$

**Wichtige Normen:**

Es gibt verschiedene Arten von Normen, die häufig verwendet werden:

* **p-Norm:** Eine Verallgemeinerung der L1- und L2-Normen.
    $$||\vec{x}||_p = \left( \sum_{i=1}^n |x_i|^p \right)^{\frac{1}{p}} \quad \text{für } p \ge 1$$
* **L1-Norm (Manhattan-Norm oder Taxi-Distanz):** Die Summe der Beträge der Komponenten des Vektors.
    $$||\vec{x}||_1 = \sum_{i=1}^n |x_i|$$
* **L2-Norm (euklidische Norm):** Die gebräuchlichste Norm, die der Standard-Länge oder dem Betrag eines Vektors entspricht.
    $$||\vec{x}||_2 = \sqrt{\sum_{i=1}^n |x_i|^2}$$
* **L$\infty$-Norm (Maximum-Norm):** Der größte Betrag unter allen Komponenten des Vektors.
    $$||\vec{x}||_\infty = \max(|x_1|, |x_2|, \dots, |x_n|)$$

Die Wahl der Norm hängt vom spezifischen Problem oder Kontext ab.

---

## Verwendung:

```dataview
list from [[Normen]]
```