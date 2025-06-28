#Note

2025-05-15

Tags: [[Spezielle Matrizen]], [[Matrizen]], [[Lineare Algebra]]

---

Neben der allgemeinen Form gibt es verschiedene Typen von [[Matrizen]], die aufgrund ihrer Struktur oder Eigenschaften besondere Bedeutung haben.

**[[Quadratische Matrix]]:**

Eine Matrix ist quadratisch, wenn die Anzahl ihrer Zeilen ($m$) gleich der Anzahl ihrer Spalten ($n$) ist ($m = n$). Nur quadratische Matrizen können eine [[Inverse Matrix]] haben oder eine [[Determinante]] im klassischen Sinn.
$$ A = \begin{pmatrix} a_{1,1} & a_{1,2} \\ a_{2,1} & a_{2,2} \end{pmatrix} \quad \text{(eine } 2 \times 2 \text{ quadratische Matrix)} $$

**[[Einheitsmatrix]] (oder [[Identitätsmatrix]]):**

Eine spezielle [[Quadratische Matrix]], bei der alle Elemente auf der Hauptdiagonale 1 sind und alle anderen Elemente 0 sind. Sie wird meist mit $E$ oder $I$ bezeichnet. Die Einheitsmatrix wirkt bei der Matrixmultiplikation wie die Zahl 1: $A \cdot E = E \cdot A = A$.
$$ E_3 = \begin{pmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{pmatrix} \quad \text{(die } 3 \times 3 \text{ Einheitsmatrix)} $$

**[[Nullmatrix]]:**

Eine Matrix beliebiger [[Dimension]], deren alle Elemente 0 sind. Addiert mit einer Matrix A ergibt sie A: $A + 0 = A$.
$$ 0 = \begin{pmatrix} 0 & 0 \\ 0 & 0 \\ 0 & 0 \end{pmatrix} \quad \text{(eine } 3 \times 2 \text{ Nullmatrix)} $$

**[[Diagonalmatrix]]:**

Eine [[Quadratische Matrix]], bei der alle Elemente außerhalb der Hauptdiagonale Null sind. Die Elemente auf der Diagonale können beliebige Werte annehmen.
$$ D = \begin{pmatrix} d_1 & 0 & 0 \\ 0 & d_2 & 0 \\ 0 & 0 & d_3 \end{pmatrix} \quad \text{(eine } 3 \times 3 \text{ Diagonalmatrix)} $$

**[[Dreiecksmatrix]]:**

Eine [[Quadratische Matrix]], bei der entweder alle Elemente oberhalb (obere Dreiecksmatrix) oder alle Elemente unterhalb (untere Dreiecksmatrix) der Hauptdiagonale Null sind.
Obere Dreiecksmatrix: $$ U = \begin{pmatrix} u_{1,1} & u_{1,2} & u_{1,3} \\ 0 & u_{2,2} & u_{2,3} \\ 0 & 0 & u_{3,3} \end{pmatrix} $$
Untere Dreiecksmatrix: $$ L = \begin{pmatrix} l_{1,1} & 0 & 0 \\ l_{2,1} & l_{2,2} & 0 \\ l_{3,1} & l_{3,2} & l_{3,3} \end{pmatrix} $$

**[[Symmetrische Matrix]]:**

Eine [[Quadratische Matrix]] A ist symmetrisch, wenn sie gleich ihrer [[Transponieren|Transponierten]] $A^T$ ist ($A = A^T$). Die Elemente sind spiegelsymmetrisch zur Hauptdiagonale ($a_{i,j} = a_{j,i}$).
$$ S = \begin{pmatrix} 1 & 2 & 3 \\ 2 & 4 & 5 \\ 3 & 5 & 6 \end{pmatrix} \quad \text{(eine symmetrische Matrix)} $$

Das Verständnis dieser speziellen Matrixtypen ist wichtig, da sie in vielen Algorithmen und theoretischen Konzepten der [[Lineare Algebra]] vorkommen.

---

## Verwendung:

```dataview
list from [[Spezielle Matrizen]]
```