#Note

2025-05-15

Tags: [[Einheitsmatrix]], [[Matrizen]], [[Spezielle Matrizen]], [[Lineare Algebra]], [[Neutralelement]], [[Matrixmultiplikation]]

---

Die **Einheitsmatrix**, auch **Identitätsmatrix** genannt, ist eine spezielle [[Matrizen|Matrix]], die eine herausragende Rolle in der [[Lineare Algebra]] spielt, ähnlich wie die Zahl 1 bei der Multiplikation von Skalaren.

**Definition:**

Die Einheitsmatrix ist eine **[[Quadratische Matrix|quadratische Matrix]]**, bei der alle Elemente auf der **Hauptdiagonale** den Wert 1 haben und alle anderen Elemente außerhalb der Diagonale den Wert 0 haben.

**Notation:**

Die Einheitsmatrix der [[Dimension]] $n \times n$ wird üblicherweise mit $E_n$ oder $I_n$ bezeichnet.

**Darstellung:**

Die $3 \times 3$ Einheitsmatrix sieht zum Beispiel so aus:
$$ E_3 = \begin{pmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{pmatrix} $$
Verallgemeinert für eine $n \times n$ Matrix:
$$ E_n = \begin{pmatrix} 1 & 0 & \dots & 0 \\ 0 & 1 & \dots & 0 \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \dots & 1 \end{pmatrix} $$

**Eigenschaft als [[Neutralelement]]:**

Die wichtigste Eigenschaft der Einheitsmatrix ist, dass sie das **neutrale Element** für die [[Matrixmultiplikation]] ist. Das bedeutet, wenn man eine Matrix A (deren [[Dimension]] die Multiplikation erlaubt) mit der Einheitsmatrix multipliziert, bleibt die Matrix A unverändert:
$$ A \cdot E = E \cdot A = A $$
Dies gilt, solange die Dimensionen der Matrizen so gewählt sind, dass die Multiplikationen definiert sind (die Einheitsmatrix muss die entsprechende Größe haben).

**Rolle bei der [[Inverse Matrix|Inversen Matrix]]:**

Die Einheitsmatrix ist auch zentral für die Definition der [[Inverse Matrix|inversen Matrix]]. Eine Matrix $A^{-1}$ ist die [[Inverse Matrix|Inverse]] von A genau dann, wenn ihr Produkt die Einheitsmatrix ergibt: $A \cdot A^{-1} = A^{-1} \cdot A = E$.

---

## Verwendung:

```dataview
list from [[Einheitsmatrix]]
```