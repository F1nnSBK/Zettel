#Note

2025-05-15

Tags: [[Adjugate Matrix]], [[Adjunkte]], [[Matrizen]], [[Lineare Algebra]], [[Kofaktor]], [[Unterdeterminante]], [[Inverse Matrix]], [[Determinante]]

---

Die **Adjugate Matrix**, auch **Adjunkte** genannt und mit $A^*$ oder $\operatorname{adj}(A)$ notiert, ist die **[[Transponieren|Transponierte]] der Matrix der [[Kofaktor|Kofaktoren]]** einer [[Quadratische Matrix|quadratischen Matrix]] $A$.

**Bildung:**

1.  Ersetze jedes Element $a_{i,k}$ in der Matrix $A$ durch seinen [[Kofaktor]] $\operatorname{Cof}_{i,k}$. Dies ergibt die Kofaktormatrix $\operatorname{Cof}(A)$.
2.  Transponiere die Kofaktormatrix. Das Ergebnis ist die Adjugate Matrix $A^*$.

Formel:

$$ A^* = (\operatorname{Cof}(A))^T $$

Die Elemente der Adjugaten Matrix an der Stelle $(k,i)$ sind also die [[Kofaktor|Kofaktoren]] der ursprünglichen Matrix an der Stelle $(i,k)$:

$$ (A^*)_{k,i} = \operatorname{Cof}_{i,k} = (-1)^{i+k} \cdot \det(A_{i,k}) $$

wobei $\det(A_{i,k})$ die [[Unterdeterminante]] zum Element $a_{i,k}$ ist.

**Verwendung:**

Die Adjugate Matrix ist am wichtigsten für die [[Berechnung]] der [[Inverse Matrix|inversen Matrix]] $A^{-1}$ einer [[Invertierbarkeit|invertierbaren]] Matrix $A$:

$$ A^{-1} = \frac{1}{\det(A)} \cdot A^* $$

Diese Formel ist besonders nützlich für $2 \times 2$ Matrizen, kann aber für größere Matrizen rechnerisch aufwendig sein, da die [[Berechnung]] vieler [[Determinante|Determinanten]] (der [[Untermatrix|Untermatrizen]]) erforderlich ist.

---

## Verwendung:

```dataview
list from [[Adjugate Matrix]]
```