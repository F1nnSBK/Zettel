#Note

2025-05-17

Tags: [[LU-Zerlegung]], [[Matrixzerlegung]], [[Matrizen]], [[Lineare Algebra]], [[Dreiecksmatrix]], [[Determinante]], [[Lineare Gleichungssysteme]], [[Gauß-Algorithmus]], [[Inverse Matrix]], [[Pivotisierung]]

---

Die **LU-Zerlegung** ist eine [[Matrixzerlegung|Matrixzerlegung]], bei der eine [[Quadratische Matrix|quadratische Matrix]] $A$ in das Produkt zweier [[Dreiecksmatrix|Dreiecksmatrizen]] faktorisiert wird: eine untere Dreiecksmatrix $L$ und eine obere Dreiecksmatrix $U$.

**Definition:**

Eine [[Quadratische Matrix|quadratische Matrix]] $A$ wird zerlegt in:

$$A = L U$$

* $L$: Eine untere [[Dreiecksmatrix]] (alle Einträge oberhalb der Hauptdiagonale sind Null). In der gebräuchlichsten Variante (Doolittle) hat $L$ Einsen auf der Hauptdiagonale.
* $U$: Eine obere [[Dreiecksmatrix]] (alle Einträge unterhalb der Hauptdiagonale sind Null). Die Diagonalelemente von $U$ sind die [[Pivotelement|Pivotelemente]], die während des [[Gauß-Algorithmus]] auftreten würden.

**Beispielstruktur (Doolittle-Variante):**

Für eine $3 \times 3$ Matrix $A$:

$$
L = \begin{pmatrix}
1 & 0 & 0 \\
l_{21} & 1 & 0 \\
l_{31} & l_{32} & 1
\end{pmatrix}, \quad
U = \begin{pmatrix}
u_{11} & u_{12} & u_{13} \\
0 & u_{22} & u_{23} \\
0 & 0 & u_{33}
\end{pmatrix}
$$

**Bestimmung von L und U:**

Die Matrizen $L$ und $U$ werden typischerweise mithilfe des [[Gauß-Algorithmus]] bestimmt. Die Matrix $U$ ist im Wesentlichen die [[Zeilenstufenform (ZSF)]] von $A$ (wenn keine Zeilenvertauschungen nötig sind). Die Elemente unterhalb der Diagonale in $L$ sind die Multiplikatoren, die im [[Gauß-Algorithmus]] verwendet wurden, um die Einträge unterhalb der [[Pivotelement|Pivotelemente]] zu eliminieren.

**Nutzen der LU-Zerlegung:**

Die LU-Zerlegung ist rechnerisch sehr nützlich:

* **Lösen von [[Lineare Gleichungssysteme|LGS]]:** Ein [[Lineare Gleichungssysteme|LGS]] $A\vec{x} = \vec{b}$ kann durch $LU\vec{x} = \vec{b}$ ersetzt werden. Dies wird in zwei einfachere Schritte aufgeteilt:
    1.  Löse $L\vec{y} = \vec{b}$ nach $\vec{y}$ durch **Vorwärtseinsetzen** (da $L$ eine untere Dreiecksmatrix ist).
    2.  Löse $U\vec{x} = \vec{y}$ nach $\vec{x}$ durch **Rückwärtseinsetzen** (da $U$ eine obere Dreiecksmatrix ist).
    Dies ist oft effizienter als die direkte Inversion von $A$ oder der Gauß-Algorithmus, insbesondere wenn man das System mit verschiedenen Vektoren $\vec{b}$ lösen muss.
* **[[Berechnung]] der [[Determinante]]:** Die [[Determinante]] einer Dreiecksmatrix ist das Produkt ihrer Diagonalelemente. Da $\det(A) = \det(L \cdot U) = \det(L) \cdot \det(U)$, und für die Doolittle-Variante $\det(L)=1$ ist, ist $\det(A) = \det(U) = u_{11} \cdot u_{22} \cdot \dots \cdot u_{nn}$.
* **[[Berechnung]] der [[Inverse Matrix]]:** Die LU-Zerlegung kann auch zur effizienten [[Berechnung]] der [[Inverse Matrix]] $A^{-1}$ verwendet werden, indem man das System $A \vec{x}_i = \vec{e}_i$ für jede Spalte $\vec{x}_i$ der [[Inverse Matrix]] und den $i$-ten Einheitsvektor $\vec{e}_i$ löst (wobei jede Lösung wieder das Vorwärts- und Rückwärtseinsetzen nutzt).

**Existenz und [[Pivotisierung (LU)|Pivotisierung]]:**

Eine einfache LU-Zerlegung ($A=LU$) existiert nicht immer für jede [[Quadratische Matrix|quadratische Matrix]]. Sie schlägt fehl, wenn während des [[Gauß-Algorithmus]] ohne Zeilenvertauschung ein [[Pivotelement|Pivotelement]] Null wäre. In solchen Fällen ist eine **[[Pivotisierung (LU)|Pivotisierung]]** (Zeilenvertauschung) erforderlich, was zu der Form $PA = LU$ führt, wobei $P$ eine [[Permutationsmatrix|Permutationsmatrix]] ist. $PA=LU$ existiert für jede [[Invertierbarkeit|invertierbare Matrix]].

---

## Verwendung:

```dataview
list from [[LU-Zerlegung]]
```