#Note

2025-05-15

Tags: [[Kofaktor]], [[Determinante]], [[Laplace-Entwicklung]], [[Unterdeterminante]], [[Adjugate Matrix]], [[Inverse Matrix]], [[Matrizen]], [[Lineare Algebra]]

---

Ein **Kofaktor** ist ein Skalarwert, der mit jedem Element $a_{i,k}$ einer [[Quadratische Matrix|quadratischen Matrix]] A verbunden ist. Er ist eine **[[Unterdeterminante]]** mit einem spezifischen Vorzeichen.

**Definition und Formel:**

Der Kofaktor $\operatorname{Cof}_{i,k}$ zum Element $a_{i,k}$ (in der $i$-ten Zeile und $k$-ten Spalte) einer Matrix A wird berechnet als:
$$ \operatorname{Cof}_{i,k} = (-1)^{i+k} \cdot \det(A_{i,k}) $$

Dabei gilt:
* $(-1)^{i+k}$ bestimmt das Vorzeichen des Kofaktors. Das Vorzeichen wechselt schachbrettartig über die Matrixpositionen:
    $$ \begin{pmatrix} + & - & + & \dots \\ - & + & - & \dots \\ + & - & + & \dots \\ \vdots & \vdots & \vdots & \ddots \end{pmatrix} $$
* $\det(A_{i,k})$ ist die **[[Unterdeterminante]]** (oder Minor), das heißt die [[Determinante]] der [[Untermatrix]] $A_{i,k}$. Die [[Untermatrix]] $A_{i,k}$ entsteht, indem man die $i$-te Zeile und die $k$-te Spalte aus der ursprünglichen Matrix A entfernt.

**Verwendung:**

[[Kofaktor|Kofaktoren]] sind zentrale Bestandteile von zwei wichtigen Berechnungen:
1.  Der [[Laplace-Entwicklung]] zur [[Berechnung]] der [[Determinante]] einer Matrix.
2.  Der Bildung der [[Adjugate Matrix|Adjunkten Matrix]] ($A^*$), die wiederum zur [[Berechnung]] der [[Inverse Matrix|inversen Matrix]] verwendet wird ($A^{-1} = \frac{1}{\det(A)} A^*$).

---

## Verwendung:

```dataview
list from [[Kofaktor]]
```