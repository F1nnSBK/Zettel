#Note

2025-05-15

Tags: [[Sarrus-Regel]], [[Determinante]], [[Matrizen]], [[Lineare Algebra]]

---

Die **[[Sarrus-Regel]]** ist eine einfache Berechnungsmethode (eine Merkregel) zur Bestimmung der [[Determinante]] einer **$3 \times 3$ [[Quadratische Matrix|quadratischen Matrix]]**. Sie ist *ausschließlich* für $3 \times 3$ Matrizen anwendbar und nicht für größere Matrizen geeignet (dafür verwendet man die [[Laplace-Entwicklung]]).

**Methode:**

Um die [[Determinante]] einer $3 \times 3$ Matrix $A$ mit der [[Sarrus-Regel]] zu berechnen, geht man wie folgt vor:

1.  Schreibe die Matrix $A$ auf.
2.  Schreibe die erste und die zweite Spalte von $A$ noch einmal rechts neben die Matrix.
3.  Berechne die Summe der Produkte der Elemente entlang der drei Diagonalen von links oben nach rechts unten.
4.  Berechne die Summe der Produkte der Elemente entlang der drei Diagonalen von links unten nach rechts oben.
5.  Subtrahiere die zweite Summe von der ersten Summe.

**Formel:**

Für $A = \begin{pmatrix} a_{1,1} & a_{1,2} & a_{1,3} \\ a_{2,1} & a_{2,2} & a_{2,3} \\ a_{3,1} & a_{3,2} & a_{3,3} \end{pmatrix}$ ist die [[Determinante]] nach der [[Sarrus-Regel]]:

$$\det(A) = a_{1,1} a_{2,2} a_{3,3} + a_{1,2} a_{2,3} a_{3,1} + a_{1,3} a_{2,1} a_{3,2} \\ - (a_{3,1} a_{2,2} a_{1,3} + a_{3,2} a_{2,3} a_{1,1} + a_{3,3} a_{2,1} a_{1,2})$$

**Beispiel:**

Berechne die [[Determinante]] der Matrix $A = \begin{pmatrix} 1 & 2 & 3 \\ 0 & 1 & 4 \\ 5 & 6 & 0 \end{pmatrix}$ mithilfe der [[Sarrus-Regel]].

Wir schreiben die ersten beiden Spalten rechts daneben:

$$
\begin{pmatrix}
1 & 2 & 3 \\
0 & 1 & 4 \\
5 & 6 & 0
\end{pmatrix}
\begin{matrix} 1 & 2 \\ 0 & 1 \\ 5 & 6 \end{matrix}
$$

Berechnung der Produkte entlang der Diagonalen:

* Positive Diagonalen (links oben nach rechts unten):
    $(1 \cdot 1 \cdot 0) + (2 \cdot 4 \cdot 5) + (3 \cdot 0 \cdot 6) = 0 + 40 + 0 = 40$

* Negative Diagonalen (links unten nach rechts oben):
    $(5 \cdot 1 \cdot 3) + (6 \cdot 4 \cdot 1) + (0 \cdot 0 \cdot 2) = 15 + 24 + 0 = 39$

Nun subtrahieren wir die Summe der negativen Diagonalen von der Summe der positiven Diagonalen:

$$ \det(A) = 40 - 39 = 1 $$

Die [[Determinante]] der Matrix A beträgt 1. Dies stimmt mit dem Ergebnis aus dem Beispiel zur [[Laplace-Entwicklung]] überein.

---

## Verwendung:

```dataview
list from [[Sarrus-Regel]]
```