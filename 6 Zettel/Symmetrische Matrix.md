#Note

2025-05-17

Tags: [[Symmetrische Matrix]], [[Spezielle Matrizen]], [[Matrizen]], [[Lineare Algebra]], [[Eigenwerte]], [[Eigenvektoren]], [[Orthogonalität]], [[Diagonalisierung]]

---

Eine **Symmetrische Matrix** ist eine [[Quadratische Matrix|quadratische Matrix]], die gleich ihrer [[Transponieren|Transponierten]] ist.

**Definition:**

Eine [[Quadratische Matrix|quadratische Matrix]] $A$ ist symmetrisch, wenn gilt:

$$A = A^T$$

Diese Bedingung bedeutet, dass für alle Indizes $i$ und $j$ das Element in der $i$-ten Zeile und $j$-ten Spalte ($a_{ij}$) gleich dem Element in der $j$-ten Zeile und $i$-ten Spalte ($a_{ji}$) ist:

$$a_{ij} = a_{ji} \quad \text{für alle } i, j$$

Die Matrix ist also spiegelbildlich zur Hauptdiagonale.

**Beispiel:**

Eine $3 \times 3$ symmetrische Matrix hat die Form:

$$
\begin{pmatrix}
a & b & c \\
b & d & e \\
c & e & f
\end{pmatrix}
$$

**Besondere [[Eigenschaften]]:**

Symmetrische Matrizen haben sehr nützliche [[Eigenschaften]], insbesondere bezüglich [[Eigenwerte|Eigenwerten]] und [[Eigenvektoren]]:

* Die [[Eigenwerte]] einer symmetrischen Matrix sind immer **reell**.
* Eigenvektoren zu **unterschiedlichen** [[Eigenwerte|Eigenwerten]] einer symmetrischen Matrix sind immer **orthogonal** zueinander.
* Jede symmetrische Matrix ist [[Diagonalisierung|diagonalisierbar]] (auch über $\mathbb{R}$). Das bedeutet, sie kann in der Form $A = S \Lambda S^{-1}$ geschrieben werden, wobei $\Lambda$ eine [[Diagonalmatrix]] der [[Eigenwerte|Eigenwerte]] ist und $S$ eine Matrix aus den zugehörigen Eigenvektoren. Tatsächlich kann $S$ sogar so gewählt werden, dass sie eine orthogonale Matrix ist ($S^{-1} = S^T$), was die [[Diagonalisierung|Diagonalisierung]] besonders einfach macht.

---

## Verwendung:

```dataview
list from [[Symmetrische Matrix]]
```