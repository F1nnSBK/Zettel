#Note

2025-05-15

Tags: [[Untermatrix]], [[Matrizen]], [[Lineare Algebra]], [[Unterdeterminante]], [[Kofaktor]]

---

Eine **Untermatrix** ist eine [[Matrizen|Matrix]], die aus einer größeren [[Matrizen|Matrix]] entsteht, indem man eine oder mehrere Zeilen und/oder eine oder mehrere Spalten löscht.

**Spezifische Form für Determinanten:**

Im Zusammenhang mit der [[Berechnung]] von [[Determinante|Determinanten]] und [[Kofaktor|Kofaktoren]] ist mit Untermatrix meist die Matrix $A_{i,k}$ gemeint. Diese spezielle [[Untermatrix]] erhält man aus einer Matrix $A$, indem man genau die $i$-te Zeile und die $k$-te Spalte entfernt.

Wenn $A$ eine $n \times n$ Matrix ist, dann ist die [[Untermatrix]] $A_{i,k}$ eine $(n-1) \times (n-1)$ Matrix.

**Verwendung:**

Die **[[Untermatrix]]** $A_{i,k}$ ist die Grundlage für die [[Berechnung]] der **[[Unterdeterminante]]** $u_{i,k} = \det(A_{i,k})$.

Diese [[Unterdeterminante|Unterdeterminanten]] werden dann wiederum verwendet, um die **[[Kofaktor|Kofaktoren]]** zu bestimmen, die für die [[Laplace-Entwicklung]] der [[Determinante]] und für die Bildung der [[Adjugate Matrix|Adjunkten Matrix]] (zur [[Berechnung]] der [[Inverse Matrix|inversen Matrix]]) benötigt werden.

---

## Verwendung:

```dataview
list from [[Untermatrix]]
```