#Note

2025-05-15

Tags: [[Invertierbarkeit]], [[Inverse Matrix]], [[Determinante]], [[Matrizen]], [[Quadratische Matrix]], [[Lineare Algebra]], [[Lösbarkeit]]

---

**Invertierbarkeit** ist eine Eigenschaft, die bestimmte [[Matrizen|Matrizen]] besitzen können. Eine Matrix ist invertierbar (oder regulär), wenn eine [[Inverse Matrix|Inverse Matrix]] $A^{-1}$ existiert, die die Gleichung $A \cdot A^{-1} = A^{-1} \cdot A = E$ erfüllt (wobei $E$ die [[Einheitsmatrix]] ist).

**Voraussetzungen und Bedingung:**

Für eine Matrix $A$ ist die **Invertierbarkeit** genau dann gegeben, wenn zwei Bedingungen erfüllt sind:

1.  $A$ muss eine **[[Quadratische Matrix|quadratische Matrix]]** sein (gleiche Anzahl Zeilen und Spalten).
2.  Die **[[Determinante]]** von $A$ muss **ungleich Null** sein: $\det(A) \neq 0$.

Wenn $\det(A) = 0$, ist die Matrix **singulär** und nicht invertierbar.

**Bedeutung für [[Lineare Gleichungssysteme|LGS]]:**

Wenn die Koeffizientenmatrix $A$ eines [[Lineare Gleichungssysteme|LGS]] $A\vec{x} = \vec{b}$ invertierbar ist ($\det(A) \neq 0$), dann hat das System immer genau eine eindeutige Lösung, die mithilfe der [[Inverse Matrix|inversen Matrix]] ($\vec{x} = A^{-1}\vec{b}$) oder der [[Cramer-Regel]] gefunden werden kann.

---

## Verwendung:

```dataview
list from [[Invertierbarkeit]]
```