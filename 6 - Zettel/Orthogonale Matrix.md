#Note

2025-05-18

Tags: [[Orthogonale Matrix]], [[Matrizen]], [[Lineare Algebra]], [[Orthonormalität]], [[Einheitsmatrix]], [[Inverse Matrix]], [[Geometrische Transformation]], [[Inneres Produkt]], [[Norm]], [[Determinante]], [[Eigenwerte]], [[QR-Zerlegung]], [[Spektralzerlegung]], [[Symmetrische Matrix]]

---

Eine **Orthogonale Matrix** ist eine [[Quadratische Matrix|quadratische Matrix]], deren Spaltenvektoren eine **orthonormale Menge** bilden. Dies bedeutet, dass die Spalten paarweise [[Orthogonalität|orthogonal]] zueinander sind und jeder Spaltenvektor die [[Norm]] 1 hat. Eine äquivalente Bedingung ist, dass die Zeilenvektoren eine orthonormale Menge bilden.

**Definition:**

Eine $n \times n$ Matrix $Q$ ist orthogonal, wenn gilt:

$$ Q^T Q = E $$

wobei $Q^T$ die [[Transponieren|transponierte Matrix]] von $Q$ und $E$ die [[Einheitsmatrix]] ist. Diese Bedingung entspricht genau der Aussage, dass die Spalten (oder Zeilen) von $Q$ eine orthonormale Menge bilden: $\langle \vec{q}_i, \vec{q}_j \rangle = \delta_{ij}$.

**Schlüsseleigenschaft: Die Inverse ist die Transponierte**

Aus der Definition $Q^T Q = E$ folgt direkt eine der nützlichsten Eigenschaften Orthogonaler Matrizen: Wenn eine Matrix $Q^T Q = E$ erfüllt, dann ist $Q^T$ die [[Inverse Matrix]] von $Q$ (und umgekehrt).

$$ Q^{-1} = Q^T $$

Dies macht die [[Berechnung]] der Inversen trivial, wenn die Matrix orthogonal ist.

**Weitere [[Eigenschaften]] und Bedeutung:**

* **[[Geometrische Transformation]]:** Orthogonale Matrizen repräsentieren **starre Körper-Transformationen** wie **Rotationen** und **Spiegelungen** im Raum. Sie verändern weder Längen noch Winkel zwischen Vektoren.
* **Erhält [[Inneres Produkt]] und [[Norm]]:** Für orthogonale Matrizen $Q$ und beliebige Vektoren $\vec{v}, \vec{w}$ gilt:
    $$ \langle Q\vec{v}, Q\vec{w} \rangle = \langle \vec{v}, \vec{w} \rangle $$
    $$ ||Q\vec{v}|| = ||\vec{v}|| $$
    Dies erklärt, warum Längen und Winkel erhalten bleiben.
* **[[Determinante]]:** Die [[Determinante]] einer orthogonalen Matrix ist immer entweder **+1** (reine Rotation) oder **-1** (Rotation kombiniert mit einer Spiegelung). $\det(Q) = \pm 1$.
* **[[Eigenwerte]]:** Die [[Eigenwerte]] einer orthogonalen Matrix haben immer den Betrag **1** ($|\lambda| = 1$).
* Orthogonale Matrizen spielen eine zentrale Rolle bei der **[[QR-Zerlegung]]** ($A=QR$, wobei $Q$ orthogonal ist) und der **[[Spektralzerlegung]]** [[Symmetrische Matrix|symmetrischer Matrizen]] ($A=Q \Lambda Q^T$, wobei $Q$ orthogonal ist).

---

## Verwendung:

```dataview
list from [[Orthogonale Matrix]]
```