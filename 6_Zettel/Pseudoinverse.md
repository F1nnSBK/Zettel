#Note

2025-05-18

Tags: [[Pseudoinverse]], [[Moore-Penrose Inverse]], [[Matrizen]], [[Lineare Algebra]], [[Inverse Matrix]], [[Singulärwertzerlegung]], [[Lineare Gleichungssysteme]], [[Kleinste Quadrate]]

---

Die **Pseudoinverse**, auch **Moore-Penrose-Inverse** genannt und mit $A^+$ notiert, ist eine Verallgemeinerung der [[Inverse Matrix|inversen Matrix]], die für **jede Matrix** (auch nicht-quadratische oder singuläre) existiert.

**Warum wird sie benötigt?**

Für Matrizen, die nicht [[Invertierbarkeit|invertierbar]] sind (weil sie nicht quadratisch sind oder weil ihre [[Determinante]] Null ist), existiert die Standard-[[Inverse Matrix]] $A^{-1}$ nicht. Die Pseudoinverse $A^+$ bietet in solchen Fällen eine Art "bestmögliche Annäherung" an eine Inverse und ist nützlich, um z.B. "ungefähre" Lösungen für [[Lineare Gleichungssysteme|Lineare Gleichungssysteme]] zu finden, wenn keine exakte Lösung existiert (z.B. bei [[Kleinste Quadrate|Überbestimmten LGS]] im Sinne der [[Kleinste Quadrate|kleinsten Quadrate]]).

**[[Eigenschaften]] (Moore-Penrose-Bedingungen):**

Die Pseudoinverse $A^+$ einer Matrix $A$ ist die eindeutige Matrix, die die folgenden vier Bedingungen erfüllt:

1.  $A A^+ A = A$
2.  $A^+ A A^+ = A^+$
3.  $(A A^+)^T = A A^+$ ( $A A^+$ ist [[Symmetrische Matrix|symmetrisch]])
4.  $(A^+ A)^T = A^+ A$ ( $A^+ A$ ist [[Symmetrische Matrix|symmetrisch]])

**Spezialfälle (Links- und Rechtsinverse):**

* Wenn eine Matrix $A$ [[Lineare Unabhängigkeit|linear unabhängige]] Zeilen hat, dann ist $A A^+$ die [[Einheitsmatrix]] ($A A^+ = E$), und $A^+$ ist eine **Rechtsinverse**.
* Wenn eine Matrix $A$ [[Lineare Unabhängigkeit|linear unabhängige]] Spalten hat, dann ist $A^+ A$ die [[Einheitsmatrix]] ($A^+ A = E$), und $A^+$ ist eine **Linksinverse**.

**[[Berechnung]] mithilfe der [[Singulärwertzerlegung]]:**

Der gebräuchlichste und numerisch stabilste Weg zur [[Berechnung]] der Pseudoinverse ist über die [[Singulärwertzerlegung]]. Wenn die SVD von $A$ gegeben ist durch $A = U \Sigma V^T$, dann ist die Pseudoinverse gegeben durch:

$$ A^+ = V \Sigma^+ U^T $$

Dabei ist $\Sigma^+$ die [[Pseudoinverse]] von $\Sigma$ (der Diagonalmatrix der Singulärwerte). $\Sigma^+$ wird gebildet, indem man die [[Transponieren|Transponierte]] von $\Sigma$ nimmt und jeden von Null verschiedenen Singulärwert $\sigma_i$ auf der Diagonalen durch seinen Kehrwert $1/\sigma_i$ ersetzt.

**Verbindung zur Standard-[[Inverse Matrix]]:**

Wenn eine Matrix $A$ [[Invertierbarkeit|invertierbar]] (d.h., quadratisch und nicht-singulär) ist, dann ist ihre Pseudoinverse gleich ihrer Standard-[[Inverse Matrix]]: $A^+ = A^{-1}$.

**Nutzen:**

Die Pseudoinverse findet Anwendung bei der Lösung von [[Lineare Gleichungssysteme|Linearen Gleichungssystemen]], insbesondere bei [[Kleinste Quadrate|Kleinste-Quadrate-Problemen]], wo sie die Lösung mit der kleinsten euklidischen [[Norm]] liefert, auch wenn die [[Normalengleichung]] singulär ist. Sie ist auch ein Schlüsselwerkzeug in der [[Singulärwertzerlegung (SVD)|SVD]] und ihren Anwendungen.

---

## Verwendung:

```dataview
list from [[Pseudoinverse]]
```
