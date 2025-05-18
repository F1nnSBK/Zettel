#Note

2025-05-18

Tags: [[Spektralzerlegung]], [[Matrixzerlegung]], [[Eigenwertzerlegung]], [[Diagonalisierung]], [[Symmetrische Matrix]], [[Matrizen]], [[Lineare Algebra]], [[Orthogonale Matrix]], [[Diagonalmatrix]], [[Eigenwerte]], [[Eigenvektoren]], [[Inverse Matrix]], [[Definitheit (Matrizen)]]], [[Singulärwertzerlegung (SVD)]]

---

Die **Spektralzerlegung** ist ein Spezialfall der [[Eigenwertzerlegung]] bzw. [[Diagonalisierung]], der für **[[Symmetrische Matrix|symmetrische Matrizen]]** existiert. Sie zerlegt eine [[Symmetrische Matrix|symmetrische]] Matrix in eine Form, die ihre Struktur und [[Eigenschaften]] hervorhebt.

**Definition:**

Eine [[Symmetrische Matrix|symmetrische]] Matrix $A$ kann zerlegt werden als:

$$A = Q \Lambda Q^T$$

* $A$: Die ursprüngliche [[Symmetrische Matrix|symmetrische Matrix]].
* $Q$: Eine **[[Orthogonale Matrix|orthogonale Matrix]]**, deren Spalten die **orthonormalen** [[Eigenvektoren|Eigenvektoren]] von $A$ sind.
* $\Lambda$ (Lambda): Eine **[[Diagonalmatrix]]**, deren Diagonaleinträge die zugehörigen **reellen** [[Eigenwerte|Eigenwerte]] von $A$ sind, in der gleichen Reihenfolge wie die [[Eigenvektoren|Eigenvektoren]] in $Q$.

**Voraussetzung:**

Die Spektralzerlegung existiert genau dann, wenn die Matrix $A$ **[[Symmetrische Matrix|symmetrisch]]** ist ($A = A^T$). Der Spektralsatz der Linearen Algebra garantiert, dass [[Symmetrische Matrix|symmetrische Matrizen]] immer [[Diagonalisierung|diagonalisierbar]] sind, nur reelle [[Eigenwerte|Eigenwerte]] haben und eine Menge von orthogonalen [[Eigenvektoren|Eigenvektoren]] besitzen, die zu einer orthonormalen Basis normiert werden können.

**Nutzen der Spektralzerlegung:**

Die Spektralzerlegung ist sehr nützlich und eng mit den [[Eigenschaften]] [[Symmetrische Matrix|symmetrischer Matrizen]] verbunden:

* Sie bietet dieselben Vorteile wie die allgemeine [[Eigenwertzerlegung]], z.B. beim einfachen Potenzieren der Matrix ($A^k = Q \Lambda^k Q^T$).
* Die [[Inverse Matrix]] einer [[Invertierbarkeit|invertierbaren]] symmetrischen Matrix kann sehr einfach berechnet werden: $A^{-1} = Q \Lambda^{-1} Q^T$. Dies liegt daran, dass $Q^T = Q^{-1}$ für orthogonale Matrizen und $\Lambda^{-1}$ einfach die [[Diagonalmatrix]] mit den Kehrwerten der [[Eigenwerte|Eigenwerte]] auf der Diagonale ist (vorausgesetzt $\lambda_i \neq 0$).
* Die [[Definitheit (Matrizen)|Definitheit]] einer [[Symmetrische Matrix|symmetrischen Matrix]] kann direkt anhand der Vorzeichen ihrer [[Eigenwerte|Eigenwerte]] in $\Lambda$ abgelesen werden.
* Für [[Definitheit (Matrizen)|positiv semi-definite]] symmetrische Matrizen ist die Spektralzerlegung eng mit der [[Singulärwertzerlegung]] verwandt.

---

## Verwendung:

```dataview
list from [[Spektralzerlegung]]
```