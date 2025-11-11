#Note

2025-05-15

Tags: [[Unterdeterminante]], [[Determinante]], [[Laplace-Entwicklung]], [[Kofaktor]], [[Matrizen]], [[Lineare Algebra]]

---

Eine **Unterdeterminante**, auch **Minor** genannt, ist die [[Determinante]] einer **[[Untermatrix]]**, die aus einer [[Quadratische Matrix|quadratischen Matrix]] $A$ gewonnen wird, indem man eine Zeile und eine Spalte entfernt.

**Bildung:**

Um die Unterdeterminante $u_{i,k}$ zum Element $a_{i,k}$ (in der $i$-ten Zeile und $k$-ten Spalte) der Matrix $A$ zu erhalten, bildet man zunächst die **[[Untermatrix]]** $A_{i,k}$ (manchmal auch $A_{-i,-k}$ notiert). Diese [[Untermatrix]] entsteht, indem man die $i$-te Zeile und die $k$-te Spalte aus der ursprünglichen Matrix $A$ entfernt.

Wenn $A$ eine $n \times n$ Matrix ist, dann ist $A_{i,k}$ eine $(n-1) \times (n-1)$ Matrix.

**Notation:**

Die Unterdeterminante zum Element $a_{i,k}$ wird mit $u_{i,k}$ oder $\det(A_{i,k})$ notiert.

**Verwendung:**

Unterdeterminanten sind entscheidend für die [[Berechnung]] der [[Determinante]] großer Matrizen mittels der [[Laplace-Entwicklung]]. Sie sind auch ein Bestandteil bei der [[Berechnung]] der [[Kofaktor|Kofaktoren]]:

$$ \operatorname{Cof}_{i,k} = (-1)^{i+k} \cdot u_{i,k} $$

Die [[Kofaktor|Kofaktoren]] wiederum werden für die [[Laplace-Entwicklung]] und die Bildung der [[Adjugate Matrix|Adjunkten Matrix]] (zur [[Berechnung]] der [[Inverse Matrix|inversen Matrix]]) benötigt.

---

## Verwendung:

```dataview
list from [[Unterdeterminante]]
```