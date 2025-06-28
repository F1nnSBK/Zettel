#Note

2025-05-18

Tags: [[Orthonormalität]], [[Orthogonalität]], [[Norm]], [[Vektorräume]], [[Lineare Algebra]], [[Inneres Produkt]], [[Basis]], [[Gram-Schmidt-Verfahren]], [[Orthogonale Matrix]]

---

**Orthonormalität** ist eine stärkere Bedingung als die [[Orthogonalität]]. Eine Menge von [[Vektoren]] ist **orthonormal**, wenn sie eine **orthogonale Menge** ist und jeder Vektor in der Menge zusätzlich die **[[Norm]] 1** hat (d.h., normiert ist).

**Definition:**

Eine Menge von [[Vektoren]] $ \{v_1, v_2, \dots, v_k\} $ in einem Inneren Produktraum ist eine **orthonormale Menge**, wenn für alle $i, j$ gilt:

1.  Die [[Vektoren]] sind orthogonal zueinander: $\langle v_i, v_j \rangle = 0$ für $i \neq j$.
2.  Jeder Vektor hat [[Norm]] 1: $||v_i|| = \sqrt{\langle v_i, v_i \rangle} = 1$ für alle $i$.

Zusammengefasst kann die Bedingung für eine orthonormale Menge mithilfe des Kronecker-Deltas $\delta_{ij}$ ($=1$ wenn $i=j$, $=0$ wenn $i \neq j$) ausgedrückt werden:

$$ \langle v_i, v_j \rangle = \delta_{ij} $$

**Bedeutung:**

* Jede orthonormale Menge von [[Vektoren]] ist automatisch **[[Lineare Unabhängigkeit|linear unabhängig]]**.
* Orthonormale [[Basis|Basen]] (siehe unten) sind äußerst vorteilhaft für Berechnungen. Die Koordinaten eines Vektors bezüglich einer orthonormalen [[Basis]] können sehr einfach berechnet werden, und die [[Norm]] und das [[Inneres Produkt]] von Vektoren sind in orthonormalen Koordinaten einfach zu handhaben.

**Verbindungen zu anderen Konzepten:**

* **[[Orthogonalität]]:** Orthonormalität impliziert immer [[Orthogonalität]].
* **[[Norm]]:** Die Bedingung der Normierung ($||v_i||=1$) ist ein Teil der Definition.
* **[[Basis|Orthonormale Basis]]:** Eine [[Basis]], die eine orthonormale Menge ist. Sie bildet die Grundlage für viele Verfahren.
* **[[Gram-Schmidt-Verfahren]]:** Ein Standardalgorithmus, um aus einer gegebenen Menge linear unabhängiger Vektoren eine orthonormale Menge (und somit eine orthonormale Basis) zu konstruieren.
* **[[Orthogonale Matrix]]:** Eine [[Quadratische Matrix|quadratische Matrix]], deren Spaltenvektoren (und damit auch Zeilenvektoren) eine orthonormale Menge bilden. Orthogonale Matrizen haben sehr nützliche [[Eigenschaften]], die direkt aus der Orthonormalität ihrer Spalten/Zeilen folgen (z.B. $Q^T Q = E$).

Orthonormalität ist ein mächtiges Konzept, das Berechnungen in Vektorräumen erheblich vereinfacht und in vielen Algorithmen und theoretischen Resultaten der Linearen Algebra eine zentrale Rolle spielt.

---

## Verwendung:

```dataview
list from [[Orthonormalität]]
```