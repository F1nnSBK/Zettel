#Note

2025-05-15

Tags: [[Gauß-Algorithmus]], [[Lineare Algebra]], [[Matrizen]], [[Lineare Gleichungssysteme]], [[Zeilenstufenform]], [[Reduzierte Zeilenstufenform]], [[Rang]]

---

Der **Gauß-Algorithmus** ist ein systematisiertes Verfahren, um eine [[Matrizen|Matrix]] mithilfe von **elementaren Zeilenumformungen** in [[Zeilenstufenform (ZSF)]] zu überführen. Sein Hauptanwendungsbereich ist die Lösung von [[Lineare Gleichungssysteme|Linearen Gleichungssystemen]] und die Bestimmung des [[Rang]]s einer Matrix.

**Elementare Zeilenumformungen:**

Die folgenden Operationen dürfen auf die Zeilen einer Matrix angewendet werden, ohne die Lösungsmenge eines zugehörigen [[Lineare Gleichungssysteme|LGS]] oder den [[Rang]] der Matrix zu ändern:

1.  **Vertauschen von zwei Zeilen ($R_i \leftrightarrow R_j$):** Die Reihenfolge der Gleichungen im System wird geändert.
2.  **Multiplikation einer Zeile mit einem Skalar ($R_i \leftarrow c \cdot R_i$, $c \neq 0$):** Eine Gleichung wird mit einer Konstanten ungleich Null multipliziert.
3.  **Addition eines Vielfachen einer Zeile zu einer anderen ($R_i \leftarrow R_i + c \cdot R_j$, $i \neq j$):** Ein Vielfaches einer Gleichung wird zu einer anderen Gleichung addiert.

**Ziel des Algorithmus:**

Das primäre Ziel des Gauß-Algorithmus ist es, die Matrix in **[[Zeilenstufenform (ZSF)]]** zu transformieren, was bedeutet, Nullen unterhalb der [[Pivotelement|Pivotelemente]] zu erzeugen.

**Beispiel: Anwendung des Gauß-Algorithmus zur Erzeugung von ZSF**

Wir wenden den Gauß-Algorithmus auf die Matrix $A = \begin{pmatrix} 1 & 3 & 5 \\ 2 & 3 & 7 \\ 1 & 3 & 5 \end{pmatrix}$ an, um sie in [[Zeilenstufenform (ZSF)]] zu überführen.

Ursprüngliche Matrix:

$$
\begin{pmatrix}
1 & 3 & 5 \\
2 & 3 & 7 \\
1 & 3 & 5
\end{pmatrix}
$$

Schritt 1: Erzeuge Nullen unter dem ersten [[Pivotelement]] (1 in der 1. Zeile, 1. Spalte).

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

Die Matrix ist nun in **[[Zeilenstufenform (ZSF)]]**. Der Gauß-Algorithmus ist abgeschlossen. Von hier aus kann der [[Rang]] abgelesen oder bei einem erweiterten System das zugehörige [[Lineare Gleichungssysteme|LGS]] durch Rückwärtseinsetzen gelöst werden.

**Erweiterung: Gauß-Jordan-Algorithmus**

Der **Gauß-Jordan-Algorithmus** erweitert den Gauß-Algorithmus, indem er weitere Zeilenumformungen verwendet, um die Matrix in **[[Reduzierte Zeilenstufenform (RZF)]]** zu überführen. Dies beinhaltet zusätzlich die Skalierung der [[Pivotelement|Pivotelemente]] auf 1 und die Erzeugung von Nullen oberhalb der [[Pivotelement|Pivotelemente]].

---

## Verwendung:

```dataview
list from [[Gauß-Algorithmus]]
```