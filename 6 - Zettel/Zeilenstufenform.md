#Note

2025-05-15

Tags: [[Zeilenstufenform]], [[Reduzierte Zeilenstufenform]], [[Gauß-Algorithmus]], [[Rang]], [[Lineare Gleichungssysteme]], [[Matrizen]], [[Lineare Algebra]], [[Pivotelement]]

---

Die **Zeilenstufenform (ZSF)** und die **Reduzierte Zeilenstufenform (RZF)** sind spezielle Formen, in die eine [[Matrizen|Matrix]] durch Anwendung des [[Gauß-Algorithmus]] umgeformt werden kann. Diese Formen erleichtern die [[Berechnung]] des [[Rang]]s und die Lösung von [[Lineare Gleichungssysteme|Linearen Gleichungssystemen]].

**Definitionen:**

Eine Matrix ist in **Zeilenstufenform (ZSF)**, wenn folgende Bedingungen erfüllt sind:

1.  Alle Zeilen, die nur aus Nullen bestehen, sind am Ende der Matrix.
2.  Das erste Element ungleich Null (genannt **[[Pivotelement]]**) in jeder Nicht-Null-Zeile ist rechts vom ersten Element ungleich Null in der darüber liegenden Zeile.
3.  Alle Elemente in einer Spalte unterhalb eines [[Pivotelement]]s sind Null.

Eine Matrix ist in **Reduzierter Zeilenstufenform (RZF)**, wenn zusätzlich zu den Bedingungen der ZSF gilt:

1.  Jedes [[Pivotelement]] ist gleich 1.
2.  Jedes [[Pivotelement]] ist das einzige Element ungleich Null in seiner Spalte (d.h., die Elemente oberhalb und unterhalb der [[Pivotelement]]e sind Null).

**Zweck:**

Durch die Umformung einer Matrix in ihre ZSF oder RZF mittels des [[Gauß-Algorithmus]] können wir:

* Einfach den [[Rang]] der Matrix bestimmen (Anzahl der Nicht-Null-Zeilen).
* [[Lineare Gleichungssysteme]] lösen (mittels Rückwärtseinsetzen bei ZSF oder direktes Ablesen bei RZF).
* Die lineare Abhängigkeit oder Unabhängigkeit von [[Vektoren]] prüfen.

**Beispiel: Umformung in ZSF und RZF**

Wir verwenden elementare Zeilenumformungen, um die Matrix $A = \begin{pmatrix} 1 & 3 & 5 \\ 2 & 3 & 7 \\ 1 & 3 & 5 \end{pmatrix}$ in ZSF und RZF zu überführen.

Ursprüngliche Matrix:

$$
\begin{pmatrix}
1 & 3 & 5 \\
2 & 3 & 7 \\
1 & 3 & 5
\end{pmatrix}
$$

Erste Schritte des [[Gauß-Algorithmus]] zur Erzeugung von Nullen unter dem ersten [[Pivotelement]] (Element in der 1. Zeile, 1. Spalte):

Operationen: $R_2 \leftarrow R_2 - 2R_1$ und $R_3 \leftarrow R_3 - R_1$.

$$
\begin{pmatrix}
1 & 3 & 5 \\
2 - 2(1) & 3 - 2(3) & 7 - 2(5) \\
1 - 1(1) & 3 - 1(3) & 5 - 1(5)
\end{pmatrix}
=
\begin{pmatrix}
1 & 3 & 5 \\
0 & -3 & -3 \\
0 & 0 & 0
\end{pmatrix}
$$

Diese Matrix ist nun in **Zeilenstufenform (ZSF)**. Die [[Pivotelement]]e sind 1 (in Zeile 1, Spalte 1) und -3 (in Zeile 2, Spalte 2). Es gibt zwei Nicht-Null-Zeilen, also ist der [[Rang]] dieser Matrix 2.

Um zur **Reduzierten Zeilenstufenform (RZF)** zu gelangen, machen wir weitere Schritte:

Zuerst stellen wir sicher, dass die [[Pivotelement]]e 1 sind. Wir skalieren die 2. Zeile:

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

Nun sorgen wir dafür, dass über den [[Pivotelement]]en Nullen stehen. Das erste [[Pivotelement]] in Zeile 2, Spalte 2 ist 1. Wir eliminieren das Element darüber (in Zeile 1, Spalte 2):

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
list from [[Zeilenstufenform]]
```