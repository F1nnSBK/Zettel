#Note

2025-05-17

Tags: [[Charakteristisches Polynom]], [[Eigenwerte]], [[Determinante]], [[Matrizen]], [[Lineare Algebra]]

---

Das **Charakteristische Polynom** einer [[Quadratische Matrix|quadratischen Matrix]] $A$ ist ein Polynom in der Variable $\lambda$, das durch die [[Berechnung]] der [[Determinante]] der Matrix $(A - \lambda I)$ erhalten wird.

**Formel:**

Für eine $n \times n$ Matrix $A$ ist das Charakteristische Polynom $p(\lambda)$ gegeben durch:

$$p(\lambda) = \det(A - \lambda I)$$

Dabei ist $I$ die [[Einheitsmatrix]] der gleichen Dimension wie $A$.

**Bedeutung:**

Die **Nullstellen** (Wurzeln) des Charakteristischen Polynoms sind genau die [[Eigenwerte]] der Matrix $A$. Die [[Berechnung]] von [[Eigenwerte|Eigenwerten]] reduziert sich somit auf das Finden der Nullstellen dieses Polynoms, d.h., das Lösen der Gleichung $\det(A - \lambda I) = 0$.

**[[Beispiel]] (für eine $2 \times 2$ Matrix):**

Berechne das Charakteristische Polynom für die Matrix $A = \begin{pmatrix} -4 & 4 \\ -12 & 10 \end{pmatrix}$.

Wir berechnen $\det(A - \lambda I)$:

$$
A - \lambda I = \begin{pmatrix} -4 & 4 \\ -12 & 10 \end{pmatrix} - \lambda \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix} = \begin{pmatrix} -4 - \lambda & 4 \\ -12 & 10 - \lambda \end{pmatrix}
$$

Das Charakteristische Polynom ist die [[Determinante]] dieser Matrix:

$$p(\lambda) = \det \begin{pmatrix} -4 - \lambda & 4 \\ -12 & 10 - \lambda \end{pmatrix} = (-4 - \lambda)(10 - \lambda) - (4)(-12)$$
$$p(\lambda) = -40 + 4\lambda - 10\lambda + \lambda^2 + 48$$
$$p(\lambda) = \lambda^2 - 6\lambda + 8$$

Das Charakteristische Polynom der Matrix $A$ ist $p(\lambda) = \lambda^2 - 6\lambda + 8$. Die Nullstellen dieses Polynoms (in diesem Fall $\lambda = 4$ und $\lambda = 2$) sind die [[Eigenwerte]] von $A$.

---

## Verwendung:

```dataview
list from [[Charakteristisches Polynom]]
```