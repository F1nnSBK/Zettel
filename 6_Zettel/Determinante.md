#Note

2025-05-15

Tags: [[Determinante]], [[Matrizen]], [[Lineare Algebra]],  [[Invertierbarkeit]], [[Lineare Gleichungssysteme]], [[Cramer-Regel]], [[Laplace-Entwicklung]], [[Sarrus-Regel]], [[Kofaktor]], [[Unterdeterminante]]

---

Die **[[Determinante]]** ist ein Skalarwert, der einer **[[Quadratische Matrix|quadratischen Matrix]]** zugeordnet wird. Sie erfasst quantitativ, wie stark die durch die Matrix repräsentierte [[Transformation]] den "Raum" skaliert. Für eine $2 \times 2$ Matrix skaliert sie die Fläche, für eine $3 \times 3$ Matrix das [[Volumen]].

**Definition:**

Die [[Determinante]] ist nur für [[Quadratische Matrix|quadratische Matrizen]] $A$ (Dimension $n \times n$) definiert und wird mit $\det(A)$ oder $|A|$ bezeichnet.

**[[Berechnung]] der [[Determinante]]:**

Die Methode zur [[Berechnung]] hängt von der Größe der Matrix ab:

1.  **Für $2 \times 2$ Matrizen:**
    Für $A = \begin{pmatrix} a_{1,1} & a_{1,2} \\ a_{2,1} & a_{2,2} \end{pmatrix}$ ist die [[Determinante]] definiert als:

    $$\det(A) = |A| = a_{1,1} \cdot a_{2,2} - a_{1,2} \cdot a_{2,1}$$

2.  **Für $3 \times 3$ Matrizen ([[Sarrus-Regel]]):**
    Für $A = \begin{pmatrix} a_{1,1} & a_{1,2} & a_{1,3} \\ a_{2,1} & a_{2,2} & a_{2,3} \\ a_{3,1} & a_{3,2} & a_{3,3} \end{pmatrix}$ kann die [[Determinante]] mithilfe der [[Sarrus-Regel]] berechnet werden:

    $$\det(A) = a_{1,1} a_{2,2} a_{3,3} + a_{1,2} a_{2,3} a_{3,1} + a_{1,3} a_{2,1} a_{3,2} \\ - (a_{3,1} a_{2,2} a_{1,3} + a_{3,2} a_{2,3} a_{1,1} + a_{3,3} a_{2,1} a_{1,2})$$

3.  **Für $n \times n$ Matrizen mit $n \ge 4$ ([[Laplace-Entwicklung]]):
    Für größere Matrizen wird die [[Determinante]] rekursiv mithilfe der [[Laplace-Entwicklung]] (oder Kofaktorentwicklung) berechnet. Man wählt eine beliebige Zeile $i$ oder Spalte $j$ und summiert die Produkte der Elemente mit ihren zugehörigen [[Kofaktor|Kofaktoren]].

    Entwicklung nach Zeile $i$:

    $$\det(A) = \sum_{k=1}^n a_{i,k} \cdot \operatorname{Cof}_{i,k}$$

    Entwicklung nach Spalte $k$:

    $$\det(A) = \sum_{i=1}^n a_{i,k} \cdot \operatorname{Cof}_{i,k}$$

    Der [[Kofaktor]] $\operatorname{Cof}_{i,k}$ (entspricht $a_{i,k}^*$) zum Element $a_{i,k}$ ist definiert als:

    $$\operatorname{Cof}_{i,k} = (-1)^{i+k} \cdot \det(A_{i,k})$$

    Dabei ist $A_{i,k}$ die **[[Untermatrix]]**, die aus $A$ entsteht, indem man die $i$-te Zeile und die $k$-te Spalte entfernt. $\det(A_{i,k})$ ist die entsprechende [[Unterdeterminante]] oder Minor $u_{i,k}$. Es ist vorteilhaft, eine Zeile oder Spalte mit möglichst vielen Nullen für die Entwicklung zu wählen.

    **Beispiel für [[Laplace-Entwicklung]] (Entwicklung nach der 1. Zeile):**
    Berechne die [[Determinante]] der Matrix $A = \begin{pmatrix} 1 & 2 & 3 \\ 0 & 1 & 4 \\ 5 & 6 & 0 \end{pmatrix}$.

    Wir entwickeln nach der 1. Zeile:

    $$\det(A) = a_{1,1} \operatorname{Cof}_{1,1} + a_{1,2} \operatorname{Cof}_{1,2} + a_{1,3} \operatorname{Cof}_{1,3}$$

    Berechnung der [[Kofaktor|Kofaktoren]]:

    $$\operatorname{Cof}_{1,1} = (-1)^{1+1} \cdot \det(A_{1,1}) = +1 \cdot \det \begin{pmatrix} 1 & 4 \\ 6 & 0 \end{pmatrix} = 1 \cdot 0 - 4 \cdot 6 = -24$$

    $$\operatorname{Cof}_{1,2} = (-1)^{1+2} \cdot \det(A_{1,2}) = -1 \cdot \det \begin{pmatrix} 0 & 4 \\ 5 & 0 \end{pmatrix} = -1 \cdot (0 \cdot 0 - 4 \cdot 5) = -1 \cdot (-20) = 20$$

    $$\operatorname{Cof}_{1,3} = (-1)^{1+3} \cdot \det(A_{1,3}) = +1 \cdot \det \begin{pmatrix} 0 & 1 \\ 5 & 6 \end{pmatrix} = +1 \cdot (0 \cdot 6 - 1 \cdot 5) = -5$$

    Nun setzen wir die Werte in die Entwicklungsformel ein:

    $$\det(A) = 1 \cdot (-24) + 2 \cdot (20) + 3 \cdot (-5) = -24 + 40 - 15 = 1$$

    Die [[Determinante]] der Matrix $A$ ist 1.

4.  **Für [[Dreiecksmatrix|Dreiecks-]] und [[Diagonalmatrix|Diagonalmatrizen]]:**
    Die [[Determinante]] ist das Produkt der Diagonal elemente:

    $$\det(A) = a_{1,1} \cdot a_{2,2} \cdot \dots \cdot a_{n,n} = \prod_{i=1}^n a_{i,i}$$

**[[Eigenschaften]] der [[Determinante]]:**

Die [[Determinante]] hat mehrere nützliche [[Eigenschaften]], die bei ihrer [[Berechnung]] und Interpretation helfen:

* Die [[Determinante]] einer [[Einheitsmatrix]] ist $\det(E) = 1$.
* Eine [[Quadratische Matrix]] $A$ ist **[[Invertierbarkeit|invertierbar]]** genau dann, wenn ihre [[Determinante]] ungleich Null ist: $A$ ist [[Invertierbarkeit|invertierbar]] $\iff \det(A) \neq 0$. Wenn $\det(A) = 0$, ist die Matrix singulär.
* Die [[Determinante]] eines Produkts von Matrizen ist das Produkt ihrer [[Determinante|Determinanten]]: $\det(AB) = \det(A) \cdot \det(B)$. Daraus folgt auch $\det(A^k) = (\det(A))^k$.
* Die [[Determinante]] der [[Transponieren|transponierten]] Matrix ist gleich der [[Determinante]] der ursprünglichen Matrix: $\det(A^T) = \det(A)$.
* Die [[Determinante]] der [[Inverse Matrix|inversen Matrix]] ist der Kehrwert der [[Determinante]] der ursprünglichen Matrix (falls die Inverse existiert): $\det(A^{-1}) = \frac{1}{\det(A)}$ (für $\det(A) \neq 0$).
* Wenn man eine Zeile (oder Spalte) einer $n \times n$ Matrix mit einem Skalar $c$ multipliziert, multipliziert sich die [[Determinante]] mit $c$. Wenn man die gesamte Matrix mit $c$ multipliziert ($cA$), multipliziert sich die [[Determinante]] mit $c^n$: $\det(cA) = c^n \det(A)$.
* Das Vertauschen zweier Zeilen (oder Spalten) ändert das Vorzeichen der [[Determinante]].
* Das Addieren eines Vielfachen einer Zeile zu einer anderen Zeile (oder Spalte zu Spalte) ändert die [[Determinante]] nicht.
* Wenn eine Matrix eine Zeile oder eine Spalte hat, die nur aus Nullen besteht, ist ihre [[Determinante]] Null.
* Wenn eine Matrix zwei identische Zeilen oder Spalten hat, ist ihre [[Determinante]] Null.
* Wenn die Zeilen- oder Spaltenvektoren einer Matrix linear abhängig sind, ist die [[Determinante]] Null.

**Anwendung:**

Neben der Bestimmung der [[Invertierbarkeit]] wird die [[Determinante]] auch verwendet, um [[Lineare Gleichungssysteme]] mithilfe der [[Cramer-Regel]] zu lösen (für [[Quadratische Matrix|quadratische]] Systeme mit $\det(A) \neq 0$).

---

## Verwendung:

```dataview
list from [[Determinante]]
```