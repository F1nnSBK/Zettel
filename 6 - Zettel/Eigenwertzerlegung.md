#Note

2025-05-17

Tags: [[Eigenwertzerlegung]], [[Diagonalisierung]], [[Eigenwerte]], [[Eigenvektoren]], [[Matrizen]], [[Lineare Algebra]], [[Diagonalmatrix]], [[Inverse Matrix]], [[Invertierbarkeit]], [[Lineare Unabhängigkeit]], [[Symmetrische Matrix]]

---

Die **Eigenwertzerlegung**, auch **Diagonalisierung** genannt, ist eine spezielle Darstellung einer [[Quadratische Matrix|quadratischen Matrix]] $A$ unter Verwendung ihrer [[Eigenwerte|Eigenwerte]] und [[Eigenvektoren|Eigenvektoren]]. Wenn eine Matrix [[Diagonalisierung|diagonalisierbar]] ist, kann sie in einer Form geschrieben werden, die ihre [[Eigenschaften]] und Operationen stark vereinfacht.

**Formel:**

Eine [[Quadratische Matrix|quadratische Matrix]] $A$ der Dimension $n \times n$ ist [[Diagonalisierung|diagonalisierbar]], wenn sie wie folgt zerlegt werden kann:

$$A = S \Lambda S^{-1}$$

**Komponenten der Zerlegung:**

* $A$: Die ursprüngliche Matrix.
* $S$: Die **Matrix der [[Eigenvektoren|Eigenvektoren]]**. Ihre Spalten sind die $n$ [[Lineare Unabhängigkeit|linear unabhängigen]] [[Eigenvektoren|Eigenvektoren]] von $A$.
* $\Lambda$ (Lambda): Die **[[Diagonalmatrix]] der [[Eigenwerte|Eigenwerte]]**. Auf ihrer Hauptdiagonale stehen die [[Eigenwerte|Eigenwerte]] $\lambda_i$ von $A$, in der gleichen Reihenfolge wie die entsprechenden [[Eigenvektoren|Eigenvektoren]] in den Spalten von $S$. Alle Einträge außerhalb der Hauptdiagonale sind Null.

    $$
    \Lambda = \begin{pmatrix}
    \lambda_1 & 0 & \dots & 0 \\
    0 & \lambda_2 & \dots & 0 \\
    \vdots & \vdots & \ddots & \vdots \\
    0 & 0 & \dots & \lambda_n
    \end{pmatrix}
    $$

* $S^{-1}$: Die [[Inverse Matrix]] der Matrix $S$.

**Bedingung für [[Diagonalisierung|Diagonalisierbarkeit]]:**

Eine $n \times n$ Matrix $A$ ist genau dann [[Diagonalisierung|diagonalisierbar]], wenn sie $n$ **[[Lineare Unabhängigkeit|linear unabhängige]] [[Eigenvektoren|Eigenvektoren]]** besitzt. Dies ist äquivalent dazu, dass die Matrix $S$ ([[Eigenvektoren|Eigenvektoren]] als Spalten) **[[Invertierbarkeit|invertierbar]]** ist (da $\det(S) \neq 0$ die Bedingung für Invertierbarkeit ist und $\det(S) \neq 0$ wiederum bedeutet, dass die Spalten von $S$ linear unabhängig sind).

Nicht jede Matrix ist [[Diagonalisierung|diagonalisierbar]]. Eine wichtige Klasse von Matrizen, die immer [[Diagonalisierung|diagonalisierbar]] sind, sind [[Symmetrische Matrix|symmetrische Matrizen]].

**Nutzen der Eigenwertzerlegung:**

Die Eigenwertzerlegung vereinfacht viele [[Matrizen|Matrixoperationen]]:

* **Potenzieren einer Matrix:** $A^k = S \Lambda^k S^{-1}$. Da $\Lambda$ eine [[Diagonalmatrix]] ist, ist $\Lambda^k$ einfach zu berechnen (man potenziert einfach die Diagonalelemente: $\Lambda^k = \begin{pmatrix} \lambda_1^k & \dots \\ \dots & \lambda_n^k \end{pmatrix}$). Dies macht die Berechnung hoher Matrixpotenzen sehr effizient.
* Analyse von [[Eigenschaften]] (z.B. [[Rang]], [[Determinante]], [[Spur]]).
* Lösen bestimmter Arten von Differentialgleichungssystemen.

---

## Verwendung:

```dataview
list from [[Eigenwertzerlegung]]
```