#Note

2025-05-15

Tags: [[Reduzierte Zeilenstufenform]], [[RZF]], [[Zeilenstufenform]], [[Gauß-Algorithmus]], [[Rang]], [[Lineare Gleichungssysteme]], [[Matrizen]], [[Lineare Algebra]], [[Definition]], [[Beispiel]], [[Pivotelement]]

---

Die **Reduzierte Zeilenstufenform (RZF)** ist eine spezielle und eindeutige Form der [[Zeilenstufenform (ZSF)]], in die jede [[Matrizen|Matrix]] durch den [[Gauß-Algorithmus]] (genauer gesagt: den Gauß-Jordan-Algorithmus) überführt werden kann.

**Definition:**

Eine Matrix ist in **Reduzierter Zeilenstufenform (RZF)**, wenn sie die Bedingungen der [[Zeilenstufenform]] erfüllt *und* zusätzlich:

1.  Jedes [[Pivotelement]] (das erste Element ungleich Null in jeder Zeile) gleich 1 ist.
2.  Jedes [[Pivotelement]] das einzige Element ungleich Null in seiner Spalte ist (d.h., alle Elemente oberhalb und unterhalb eines [[Pivotelement]]s sind Null).

**Zweck und Vorteile:**

Die RZF ist besonders nützlich, weil:

* Sie die eindeutige Form ist, in die eine Matrix durch Zeilenumformungen gebracht werden kann.
* Sie das Ablesen des [[Rang]]s (Anzahl der Nicht-Null-Zeilen) direkt ermöglicht.
* Sie die Lösung von [[Lineare Gleichungssysteme|Linearen Gleichungssystemen]] ($A\vec{x} = \vec{b}$) extrem vereinfacht. Wenn die erweiterte Matrix $(A|\vec{b})$ in RZF vorliegt, kann die Lösung oft direkt abgelesen oder mit minimalem Aufwand bestimmt werden, insbesondere die partikuläre und die homogene Lösung (Kern).

**[[Beispiel]]: Umformung von ZSF zu RZF**

Wir starten mit einer Matrix in [[Zeilenstufenform]] und formen sie in die Reduzierte Zeilenstufenform um. Angenommen, wir haben die ZSF-Matrix $B = \begin{pmatrix} 1 & 3 & 5 \\ 0 & -3 & -3 \\ 0 & 0 & 0 \end{pmatrix}$ (aus dem Beispiel in der Notiz zur [[Zeilenstufenform]]).

Matrix in ZSF:

$$
\begin{pmatrix}
1 & 3 & 5 \\
0 & -3 & -3 \\
0 & 0 & 0
\end{pmatrix}
$$

Erster Schritt zur RZF: Sicherstellen, dass die [[Pivotelement]]e 1 sind. Das zweite [[Pivotelement]] ist -3.

Operation: $R_2 \leftarrow -\frac{1}{3}R_2$.

$$
\begin{pmatrix}
1 & 3 & 5 \\
-\frac{1}{3}(0) & -\frac{1}{3}(-3) & -\frac{1}{3}(-3) \\
0 & 0 & 0
\end{pmatrix}
=
\begin{pmatrix}
1 & 3 & 5 \\
0 & 1 & 1 \\
0 & 0 & 0
\end{pmatrix}
$$

Zweiter Schritt zur RZF: Sicherstellen, dass über den [[Pivotelement]]en Nullen stehen. Das zweite [[Pivotelement]] (in Zeile 2, Spalte 2) ist jetzt 1. Wir eliminieren die 3 darüber (in Zeile 1, Spalte 2).

Operation: $R_1 \leftarrow R_1 - 3R_2$.

$$
\begin{pmatrix}
1 - 3(0) & 3 - 3(1) & 5 - 3(1) \\
0 & 1 & 1 \\
0 & 0 & 0
\end{pmatrix}
=
\begin{pmatrix}
1 & 0 & 2 \\
0 & 1 & 1 \\
0 & 0 & 0
\end{pmatrix}
$$

Diese Matrix ist nun in **Reduzierter Zeilenstufenform (RZF)**. Die [[Pivotelement]]e sind 1 (in Zeile 1, Spalte 1 und Zeile 2, Spalte 2), und alle anderen Einträge in den [[Pivotelement]]spalten sind Null.

---

## Verwendung:

```dataview
list from [[Reduzierte Zeilenstufenform]]
```