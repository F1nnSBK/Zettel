#Note

2025-05-17

Tags: [[Designmatrix]], [[Lineare Regression]], [[Regression]], [[Matrizen]], [[Lineare Algebra]], [[Normalengleichung]], [[Koeffizienten]]

---

Die **Designmatrix** $X$ ist eine spezielle [[Matrizen|Matrix]], die in der [[Lineare Regression|Linearen Regression]] verwendet wird, um die unabhängigen Variablen (Prädiktoren) für alle Datenpunkte zu organisieren.

**Struktur:**

* Jede **Zeile** der Designmatrix entspricht einem einzelnen **Datenpunkt** (einer Beobachtung).
* Jede **Spalte** entspricht einer **unabhängigen Variable**.
* Um den Achsenabschnitt ($c_0$) im Modell $y = c_0 + c_1 X_1 + \dots + c_n X_n$ zu berücksichtigen, wird der Designmatrix üblicherweise eine **erste Spalte** hinzugefügt, die nur aus **Einsen** besteht. Diese Einsen werden mit dem Koeffizienten $c_0$ multipliziert und repräsentieren den Achsenabschnitt, als wäre er mit einer "konstanten" Variable ($X_0=1$) assoziiert.

Wenn wir $m$ Datenpunkte haben und jede Beobachtung $n$ unabhängige Variablen ($X_1, \dots, X_n$) hat, dann hat die Designmatrix $X$ die Dimension $m \times (n+1)$ ( $m$ Zeilen und $n+1$ Spalten, eine für jede Variable plus eine für den Achsenabschnitt).

**Beispielstruktur:**

Für $m$ Datenpunkte und $n$ unabhängige Variablen ($X_1, \dots, X_n$) sieht die Designmatrix typischerweise so aus:

$$
X = \begin{pmatrix}
1 & x_{11} & x_{12} & \dots & x_{1n} \\
1 & x_{21} & x_{22} & \dots & x_{2n} \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
1 & x_{m1} & x_{m2} & \dots & x_{mn}
\end{pmatrix}
$$

Hierbei steht $x_{ji}$ für den Wert der $i$-ten unabhängigen Variable des $j$-ten Datenpunkts.

**Rolle in der Matrixformulierung:**

Die Designmatrix $X$ ermöglicht es, die [[Lineare Regression|Lineare Regression]] in einer kompakten Matrixform auszudrücken:

$$ \vec{y} = X\vec{c} + \vec{\epsilon} $$

wobei $\vec{y}$ der Vektor der abhängigen Variablen ist, $\vec{c}$ der Vektor der [[Koeffizienten]] ($c_0, c_1, \dots, c_n$) und $\vec{\epsilon}$ der Vektor der Residuen (Fehler). Das Ziel ist, $\vec{c}$ so zu finden, dass $\vec{\epsilon}$ (im Sinne der kleinsten Quadrate) minimiert wird. Dies führt zur [[Normalengleichung]].

---

## Verwendung:

```dataview
list from [[Designmatrix]]
```