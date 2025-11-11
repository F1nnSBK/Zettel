#Note

2025-05-17

Tags: [[Eigenwerte]], [[Eigenvektoren]], [[Lineare Algebra]], [[Matrizen]], [[Charakteristisches Polynom]], [[Determinante]], [[Invertierbarkeit]], [[Spur]], [[Symmetrische Matrix]], [[Diagonalmatrix]], [[Dreiecksmatrix]]

---

Ein **Eigenwert** einer [[Quadratische Matrix|quadratischen Matrix]] $A$ ist der [[Skalar]] $\lambda$, der in der **Charakteristischen Gleichung** $A\vec{x} = \lambda\vec{x}$ auftritt, wobei $\vec{x}$ der zugehörige [[Eigenvektoren|Eigenvektor]] ist ($\vec{x} \neq \vec{0}$). Der Eigenwert beschreibt, um welchen Faktor der [[Eigenvektoren|Eigenvektor]] bei Multiplikation mit der Matrix skaliert wird.

**[[Berechnung]] von [[Eigenwerte|Eigenwerten]]:**

Um die Eigenwerte einer $n \times n$ Matrix $A$ zu finden, gehen wir von der Charakteristischen Gleichung $A\vec{x} = \lambda\vec{x}$ aus und formen sie um:

$A\vec{x} - \lambda\vec{x} = \vec{0}$

Da $A$ eine Matrix und $\lambda$ ein Skalar ist, können wir $\lambda\vec{x}$ nicht einfach als $\lambda$ vor die Matrix ziehen. Wir verwenden die [[Einheitsmatrix]] $I$: $\lambda\vec{x} = \lambda I \vec{x}$.

$A\vec{x} - \lambda I \vec{x} = \vec{0}$

$(A - \lambda I)\vec{x} = \vec{0}$

Dies ist ein [[Homogenes Lineares Gleichungssystem]]. Wir suchen nicht-triviale Lösungen für $\vec{x}$ ($\vec{x} \neq \vec{0}$). Ein [[Homogenes Lineares Gleichungssystem]] hat genau dann nicht-triviale Lösungen, wenn die Koeffizientenmatrix $(A - \lambda I)$ **nicht [[Invertierbarkeit|invertierbar]]** (singulär) ist. Dies ist der Fall, wenn ihre [[Determinante]] gleich Null ist:

$$\det(A - \lambda I) = 0$$

Diese Gleichung wird als **Charakteristische Gleichung** (im Kontext der Eigenwerte) bezeichnet. Die linke Seite $\det(A - \lambda I)$ ist ein Polynom in $\lambda$ vom Grad $n$, genannt **[[Charakteristisches Polynom]]**.

Die Eigenwerte $\lambda$ der Matrix $A$ sind die **Nullstellen** (Wurzeln) des [[Charakteristisches Polynom|Charakteristischen Polynoms]], d.h., die Lösungen der Gleichung $\det(A - \lambda I) = 0$.

**[[Beispiel]] zur [[Berechnung]] von [[Eigenwerte|Eigenwerten]]:**

Berechne die Eigenwerte der Matrix $A = \begin{pmatrix} -4 & 4 \\ -12 & 10 \end{pmatrix}$.

Wir stellen die Gleichung $\det(A - \lambda I) = 0$ auf:

$$
A - \lambda I = \begin{pmatrix} -4 & 4 \\ -12 & 10 \end{pmatrix} - \lambda \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix} = \begin{pmatrix} -4 - \lambda & 4 \\ -12 & 10 - \lambda \end{pmatrix}
$$

Wir berechnen die [[Determinante]] dieser Matrix:

$$\det(A - \lambda I) = \det \begin{pmatrix} -4 - \lambda & 4 \\ -12 & 10 - \lambda \end{pmatrix} = (-4 - \lambda)(10 - \lambda) - (4)(-12)$$

Wir setzen die [[Determinante]] gleich Null, um das [[Charakteristisches Polynom]] zu erhalten und dessen Nullstellen zu finden:

$$(-4 - \lambda)(10 - \lambda) - (4)(-12) = 0$$
$$-40 + 4\lambda - 10\lambda + \lambda^2 + 48 = 0$$
$$\lambda^2 - 6\lambda + 8 = 0$$

Dies ist das [[Charakteristisches Polynom]]. Wir finden die Nullstellen (Eigenwerte) durch Faktorisierung oder mithilfe der p-q-Formel:

$$(\lambda - 4)(\lambda - 2) = 0$$

Die Nullstellen sind $\lambda_1 = 4$ und $\lambda_2 = 2$.

Die Eigenwerte der Matrix $A$ sind also 4 und 2. Für jeden dieser Eigenwerte können dann die zugehörigen [[Eigenvektoren|Eigenvektoren]] berechnet werden (siehe Notiz zu [[Eigenvektoren|Eigenvektoren]]).

**[[Eigenschaften]] von [[Eigenwerte|Eigenwerten]]:**

* Eine $n \times n$ Matrix hat genau $n$ Eigenwerte, wenn man sie mit ihrer algebraischen Vielfachheit zählt (auch wenn sie komplex oder mehrfach auftreten).
* Die Summe der Eigenwerte einer Matrix ist gleich ihrer [[Spur]] (Summe der Diagonalelemente): $\sum_{i=1}^n \lambda_i = \operatorname{spur}(A)$.
* Das Produkt der Eigenwerte einer Matrix ist gleich ihrer [[Determinante]]: $\prod_{i=1}^n \lambda_i = \det(A)$.
* Die Eigenwerte einer [[Symmetrische Matrix|symmetrischen Matrix]] sind immer reell.
* Die Eigenwerte einer [[Dreiecksmatrix|Dreiecks-]] oder [[Diagonalmatrix|Diagonalmatrix]] sind einfach ihre Diagonalelemente.
* Wenn $\lambda$ ein Eigenwert von $A$ ist, dann ist $\lambda + \gamma$ ein Eigenwert von $A + \gamma E$.
* Wenn $\lambda$ ein Eigenwert von $A$ ist und $A$ [[Invertierbarkeit|invertierbar]] ist, dann ist $\lambda^{-1}$ ein Eigenwert von $A^{-1}$ (vorausgesetzt $\lambda \neq 0$).
* Wenn $\lambda$ ein Eigenwert von $A$ ist, dann ist $\lambda^k$ ein Eigenwert von $A^k$ für jede ganze Zahl $k \ge 1$.

---

## Verwendung:

```dataview
list from [[Eigenwerte]]
```