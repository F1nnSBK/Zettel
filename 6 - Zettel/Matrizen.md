#Note

2025-05-15

Tags: [[Matrizen]],  [[Lineare Algebra]], [[Vektoren]], [[Dimension]], [[Spezielle Matrizen]], [[Inverse Matrix]], [[Invertierbarkeit]], [[Determinante]], [[Rang]], [[3 - Tags/Grundlagen]]

---

Eine Matrix ist ein mathematisches Objekt, das aus einer rechteckigen Anordnung von Zahlen (oder anderen mathematischen Objekten) in Zeilen und Spalten besteht. Man kann sie als eine Organisation von [[Vektoren]], entweder als Zeilenvektoren oder Spaltenvektoren, betrachten.

**Notation und Dimension:**

Eine Matrix A wird oft mit $A = (a_{i,j})$ bezeichnet, wobei $a_{i,j}$ das Element in der $i$-ten Zeile und $j$-ten Spalte ist.
Die **Dimension** einer Matrix wird als $m \times n$ angegeben, wobei $m$ die Anzahl der Zeilen und $n$ die Anzahl der Spalten ist.
$$A = \begin{pmatrix} a_{1,1} & a_{1,2} & \dots & a_{1,n} \\ a_{2,1} & a_{2,2} & \dots & a_{2,n} \\ \vdots & \vdots & \ddots & \vdots \\ a_{m,1} & a_{m,2} & \dots & a_{m,n} \end{pmatrix}$$

**Matrixoperationen:**

* **Addition und Subtraktion:** Werden komponentenweise durchgeführt. Matrizen müssen die gleiche [[Dimension]] haben, um addiert oder subtrahiert werden zu können.
    $$A \pm B = \begin{pmatrix} a_{1,1} \pm b_{1,1} & \dots & a_{1,n} \pm b_{1,n} \\ \vdots & \ddots & \vdots \\ a_{m,1} \pm b_{m,1} & \dots & a_{m,n} \pm b_{m,n} \end{pmatrix}$$
* **Multiplikation mit einem Skalar:** Jedes Element der Matrix wird mit dem Skalar multipliziert (komponentenweise).
    $$k \cdot A = \begin{pmatrix} k \cdot a_{1,1} & \dots & k \cdot a_{1,n} \\ \vdots & \ddots & \vdots \\ k \cdot a_{m,1} & \dots & k \cdot a_{m,n} \end{pmatrix}$$
* **Matrixmultiplikation:** Das Produkt $C = A \cdot B$ zweier Matrizen A ($m \times n$) und B ($n \times r$) ist eine Matrix C der Dimension $m \times r$. Die Multiplikation ist nur möglich, wenn die Anzahl der Spalten von A gleich der Anzahl der Zeilen von B ist. Die Elemente $c_{i,k}$ der Ergebnismatrix C werden berechnet als:
    $$c_{i,k} = \sum_{j=1}^n a_{i,j} \cdot b_{j,k}$$
    (Zeile von A mal Spalte von B als [[Skalarprodukt]]). Die Matrixmultiplikation ist im Allgemeinen nicht kommutativ ($A \cdot B \neq B \cdot A$).

**Spezielle Matrizen:**

* **[[Quadratische Matrix]]:** Eine Matrix mit gleicher Anzahl von Zeilen und Spalten ($m = n$).
* **[[Einheitsmatrix]] (Identitätsmatrix) E:** Eine quadratische Matrix, bei der alle Elemente auf der Hauptdiagonale 1 sind und alle anderen 0. $A \cdot E = E \cdot A = A$.
    $$E = \begin{pmatrix} 1 & 0 & \dots & 0 \\ 0 & 1 & \dots & 0 \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \dots & 1 \end{pmatrix}$$
* **[[Nullmatrix]]:** Eine Matrix, deren alle Elemente 0 sind. Addiert mit einer Matrix A ergibt sie A.
* **[[Diagonalmatrix]]:** Eine quadratische Matrix, bei der alle Elemente außerhalb der Hauptdiagonale 0 sind.
* **[[Dreiecksmatrix]]:** Eine quadratische Matrix, bei der alle Elemente entweder oberhalb (obere Dreiecksmatrix) oder unterhalb (untere Dreiecksmatrix) der Hauptdiagonale Null sind.

**Transponierte Matrix:**

Die Transponierte Matrix $A^T$ einer Matrix A wird erhalten, indem man ihre Zeilen und Spalten vertauscht ("um 90° gedreht"). Wenn $A = (a_{i,j})$, dann ist $A^T = (a_{j,i})$.
$$ A = \begin{pmatrix} 1 & 2 \\ 3 & 4 \\ 5 & 6 \end{pmatrix} \quad \implies \quad A^T = \begin{pmatrix} 1 & 3 & 5 \\ 2 & 4 & 6 \end{pmatrix} $$
Eine Matrix A ist **[[Symmetrische Matrix|symmetrisch]]**, wenn $A = A^T$.

**[[Inverse Matrix]]:**

Die [[Inverse Matrix]] $A^{-1}$ einer quadratischen Matrix A macht deren Transformation rückgängig: $A \cdot A^{-1} = A^{-1} \cdot A = E$. Eine Matrix ist nur dann [[Invertierbarkeit|invertierbar]], wenn sie quadratisch ist und ihre [[Determinante]] nicht Null ist ($det(A) \neq 0$).

**[[Rang]] einer Matrix:**

Der [[Rang]] $rg(A)$ einer Matrix ist die maximale Anzahl linear unabhängiger Zeilen- oder Spaltenvektoren in der Matrix. (Siehe auch [[Lineare Gleichungssysteme]] zur Bestimmung des Rangs mittels [[Gauß-Algorithmus]]).

---

## Verwendung:

```dataview
list from [[Matrizen]]
```