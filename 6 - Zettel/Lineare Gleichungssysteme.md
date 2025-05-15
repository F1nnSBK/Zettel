---
---

#Note
2025-05-15

Tags: [[Lineare Gleichungssysteme]], [[Lineare Algebra]], [[Matrizen]], [[Gauß-Algorithmus]], [[Rang]], [[Lösbarkeit]], [[Zeilenstufenform]], [[Reduzierte Zeilenstufenform]], [[Inverse Matrix]], [[Cramer-Regel]], [[Determinante]]

---

Ein Lineares Gleichungssystem (LGS) ist eine Sammlung von $m$ zusammenhängenden linearen Gleichungen für $n$ Unbekannte. Aufgrund ihrer Linearität dürfen [[Lineare Algebra|Linearkombinationen]] von Gleichungen angewendet werden, um das System zu lösen.

**Darstellung:**

Ein LGS kann als eine Menge von Gleichungen geschrieben werden, z.B. für 3 Unbekannte $x, y, z$:
$$3x + 2y + 6z = 20$$
$$5x + 4y + 1z = 22$$
$$7x + 8y + 12z = 13$$
Es kann auch in **Matrixdarstellung** als $A\vec{x} = \vec{b}$ geschrieben werden, wobei A die Koeffizientenmatrix, $\vec{x}$ der Vektor der Unbekannten und $\vec{b}$ der Vektor der rechten Seiten ist:
$$ \begin{pmatrix} 3 & 2 & 6 \\ 5 & 4 & 1 \\ 7 & 8 & 12 \end{pmatrix} \begin{pmatrix} x \\ y \\ z \end{pmatrix} = \begin{pmatrix} 20 \\ 22 \\ 13 \end{pmatrix} $$
Oft wird das erweiterte System $(A|\vec{b})$ betrachtet:
$$ (A|\vec{b}) = \left( \begin{array}{ccc|c} 3 & 2 & 6 & 20 \\ 5 & 4 & 1 & 22 \\ 7 & 8 & 12 & 13 \end{array} \right) $$

**Lösungsmethoden:**

* **[[Gauß-Algorithmus]]:** Eine systematische Methode, um das LGS durch Äquivalenzumformungen in die [[Zeilenstufenform]] (ZSF) oder [[Reduzierte Zeilenstufenform]] (RZF) zu überführen. Die erlaubten Operationen sind:
    * Vertauschen von Zeilen (Gleichungen).
    * Multiplikation einer Zeile mit einer Konstanten $k \neq 0$.
    * Addition eines Vielfachen einer Zeile zu einer anderen Zeile.
    Nach Erreichen der ZSF kann die Lösung durch Rückwärtseinsetzen gefunden werden.

* **Lösung mit [[Inverse Matrix|inverser Matrix]]:** Wenn die Koeffizientenmatrix A quadratisch ist und [[Determinante|invertierbar]] ($det(A) \neq 0$), kann das LGS $A\vec{x} = \vec{b}$ durch Multiplikation mit der Inversen $A^{-1}$ von links gelöst werden:
    $$\vec{x} = A^{-1}\vec{b}$$
    Dies ist nur möglich, wenn A quadratisch ist und vollen [[Rang]] hat.

* **Lösung mit [[Determinante|Determinanten]] ([[Cramer-Regel]]):** Für quadratische Systeme mit $det(A) \neq 0$ kann jede Komponente $x_i$ des Lösungsvektors berechnet werden als:
    $$x_i = \frac{\det(A_i)}{\det(A)}$$
    Dabei ist $A_i$ die Matrix A, bei der die $i$-te Spalte durch den Vektor der rechten Seiten $\vec{b}$ ersetzt wurde.

**Anzahl der Lösungen ([[Lösbarkeit]]):**

Die Anzahl der Lösungen eines LGS hängt vom [[Rang]] der Koeffizientenmatrix A und des erweiterten Systems $(A|\vec{b})$ sowie der Anzahl der Variablen $n$ ab. Der Rang einer Matrix ist die Anzahl der Nicht-Null-Zeilen in ihrer [[Zeilenstufenform]]. Ein LGS ist lösbar, wenn $rg(A) = rg(A|\vec{b})$.

* **Genau eine Lösung:** $rg(A) = rg(A|\vec{b}) = n$. Die Anzahl der linear unabhängigen Gleichungen entspricht der Anzahl der Unbekannten.
* **Unendlich viele Lösungen:** $rg(A) = rg(A|\vec{b}) < n$. Es gibt mehr Variablen als linear unabhängige Gleichungen, was zu freien Variablen führt.
* **Keine Lösung:** $rg(A) \neq rg(A|\vec{b})$. Die Gleichungen sind widersprüchlich. Dies tritt auf, wenn in der [[Zeilenstufenform]] eine Zeile der Form $(0\ 0\ \dots\ 0\ |\ c)$ mit $c \neq 0$ auftritt.

**Konzepte im Gauß-Algorithmus:**

* **Pivotelement:** Das erste Nicht-Null-Element in einer Zeile der [[Zeilenstufenform]] (von links gelesen).
* **Pivotspalte:** Eine Spalte, die ein Pivotelement enthält.

**[[Reduzierte Zeilenstufenform]] (RZF):**

In der RZF sind alle Pivotelemente 1 und alle anderen Einträge in den Pivotspalten sind 0. Aus der RZF lässt sich direkt eine **partikuläre Lösung** ablesen (setze Nicht-Pivot-Variablen auf 0). Die **allgemeine Lösung** ist die Summe einer partikulären Lösung und der Lösung des homogenen Systems ($A\vec{x}=\vec{0}$), die den Kern von A beschreibt.

**LGS mit Parametern:**

LGS, die zusätzlich zu den Variablen Parameter enthalten, können grundsätzlich wie normale LGS behandelt werden. Nach der Umformung in die [[Zeilenstufenform]] sind jedoch [[Fallunterscheidung]]en erforderlich, um Divisionen durch Null zu vermeiden, abhängig von den Werten der Parameter.

**Arten von LGS (nach Dimensionen):**

* **Unterbestimmt:** Mehr Variablen als Gleichungen ($n > m$). Haben oft unendlich viele oder keine Lösungen.
* **Überbestimmt:** Weniger Variablen als Gleichungen ($m > n$). Haben oft keine oder genau eine Lösung.

---

## Verwendung:

```dataview
list from [[Lineare Gleichungssysteme]]
```