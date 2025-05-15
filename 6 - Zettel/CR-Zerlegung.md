#Note
2025-05-15

Tags: [[Matrizen]], [[Lineare Algebra]], [[Zerlegung]]

---

Die CR-Zerlegung einer Matrix A zerlegt diese in zwei Matrizen C und R, die den Spaltenraum bzw. den Zeilenraum von A repräsentieren.

**Definitionen:**

* **C-Matrix:** Enthält die linear unabhängigen Spaltenvektoren der Matrix A. Sie bildet eine Basis für den Spaltenraum ($Col(A)$ oder $Im(A)$). Jede Spalte von A kann als Linearkombination der Spalten von C dargestellt werden.
    $$C = [\vec{c}_1, \vec{c}_2, \dots, \vec{c}_r]$$
    wobei $\vec{c}_i$ die Spalten von A sind, die den Pivotspalten in der RZF von A entsprechen.
* **R-Matrix:** Ist die reduzierte Zeilenstufenform (RZF) der Matrix A. R stellt den Zeilenraum ($Row(A)$) dar.

**Bestimmung von C und R:**

1.  Bestimme die reduzierte Zeilenstufenform (RZF) der Matrix A. Das Ergebnis ist die Matrix R.
2.  Identifiziere die Spalten in R, die Pivotelemente enthalten. Die entsprechenden Spalten in der ursprünglichen Matrix A bilden die Matrix C.

**Eigenschaften:**

* Der Rang der Matrizen C, R und A ist gleich: $Rang(C) = Rang(R) = Rang(A)$.

**Magic Factorization:**

Die Zerlegung kann auch geschrieben werden als $A = C \omega^{-1} R_*$.
Hierbei ist $\omega$ eine quadratische $r \times r$ Untermatrix der ursprünglichen Matrix A ($r$ ist der Rang von A). Diese Untermatrix befindet sich am Schnittpunkt der Zeilen in A, die Pivotzeilen in $R_*$ (bzw. R) entsprechen, und der Spalten in A, die Pivotspalten in R (und damit C) entsprechen. $R_*$ ist hierbei oft die RZF, bei der eventuelle Nullzeilen am Ende weggelassen wurden oder eine Variante, die besser zur Struktur von $\omega$ passt.

**Beispiel:**

Für die Matrix $A$:
$$A = \begin{pmatrix} 1 & 3 & 5 \\ 2 & 3 & 7 \\ 1 & 3 & 5 \end{pmatrix}$$

1.  Bestimmung der RZF von A:
    $$A = \begin{pmatrix} 1 & 3 & 5 \\ 2 & 3 & 7 \\ 1 & 3 & 5 \end{pmatrix} \xrightarrow{\tiny R_2 \leftarrow R_2 - 2R_1} \begin{pmatrix} 1 & 3 & 5 \\ 0 & -3 & -3 \\ 1 & 3 & 5 \end{pmatrix} \xrightarrow{\tiny R_3 \leftarrow R_3 - R_1} \begin{pmatrix} 1 & 3 & 5 \\ 0 & -3 & -3 \\ 0 & 0 & 0 \end{pmatrix} \xrightarrow{\tiny R_2 \leftarrow -\frac{1}{3}R_2} \begin{pmatrix} 1 & 3 & 5 \\ 0 & 1 & 1 \\ 0 & 0 & 0 \end{pmatrix} \xrightarrow{\tiny R_1 \leftarrow R_1 - 3R_2} \begin{pmatrix} 1 & 0 & 2 \\ 0 & 1 & 1 \\ 0 & 0 & 0 \end{pmatrix} = R$$
    Die Pivotelemente sind in der 1. und 2. Spalte.
2.  Bestimmung von C:
    Die 1. und 2. Spalte der ursprünglichen Matrix A bilden C:
    $$C = \begin{pmatrix} 1 & 3 \\ 2 & 3 \\ 1 & 3 \end{pmatrix}$$
    Die dritte Spalte von A ist eine Linearkombination der Spalten von C: $\begin{pmatrix} 5 \\ 7 \\ 5 \end{pmatrix} = 2 \cdot \begin{pmatrix} 1 \\ 2 \\ 1 \end{pmatrix} + 1 \cdot \begin{pmatrix} 3 \\ 3 \\ 3 \end{pmatrix}$

---

## Verwendung:

```dataview
list from [[CR-Zerlegung]]
```
