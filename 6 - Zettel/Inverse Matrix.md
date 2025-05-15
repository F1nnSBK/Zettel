#Note

2025-05-15

Tags: [[Inverse Matrix]], [[Invertierbarkeit]], [[Matrizen]], [[Lineare Algebra]], [[Determinante]], [[Lineare Gleichungssysteme]], [[Einheitsmatrix]], [[Berechnung]], [[Adjugate Matrix]], [[Kofaktor]], [[Untermatrix]]

---

Die **[[Inverse Matrix]]** $A^{-1}$ einer [[Matrizen|Matrix]] $A$ ist eine Matrix, die, wenn sie mit $A$ multipliziert wird, die [[Einheitsmatrix|Identitätsmatrix]] $E$ ergibt. Man kann sagen, sie macht die [[Transformation|Transformation]] von $A$ "rückgängig".

**Definition:**

Für eine [[Quadratische Matrix|quadratische Matrix]] $A$ ist ihre inverse Matrix $A^{-1}$ definiert durch die Eigenschaft:

$$A \cdot A^{-1} = A^{-1} \cdot A = E$$

wobei $E$ die [[Einheitsmatrix]] der gleichen [[Dimension]] wie $A$ ist.

**Voraussetzungen für die [[Invertierbarkeit]]:**

Eine Matrix $A$ besitzt nur dann eine [[Inverse Matrix|Inverse]], wenn zwei Bedingungen erfüllt sind:

1.  $A$ muss eine **[[Quadratische Matrix|quadratische Matrix]]** sein (gleiche Anzahl Zeilen und Spalten).
2.  $A$ muss **[[Invertierbarkeit|invertierbar]]** sein, was bedeutet, dass ihre [[Determinante]] nicht Null ist: $\det(A) \neq 0$. Eine quadratische Matrix mit $\det(A) = 0$ wird als singulär bezeichnet und hat keine Inverse.

**Verwendung:**

Die [[Inverse Matrix]] ist nützlich zur Lösung von [[Lineare Gleichungssysteme|Linearen Gleichungssystemen]] der Form $A\vec{x} = \vec{b}$, wenn $A$ eine quadratische, [[Invertierbarkeit|invertierbare Matrix]] ist. Die Lösung kann direkt berechnet werden als:

$$\vec{x} = A^{-1}\vec{b}$$

**[[Berechnung]] der Inversen Matrix:**

Es gibt verschiedene Methoden zur Berechnung der [[Inverse Matrix]] für eine [[Invertierbarkeit|invertierbare]] [[Quadratische Matrix|quadratische Matrix]]:

1.  **Mithilfe der [[Determinante]] und der [[Adjugate Matrix|Adjunkten Matrix]]:**
    Die Inverse kann berechnet werden als:

    $$ A^{-1} = \frac{1}{\det(A)} \cdot A^* $$

    Dabei ist $A^*$ die Adjugate Matrix (oder Adjunkte) von $A$, deren Elemente aus den [[Kofaktor|Kofaktoren]] (mit Vorzeichen versehenen [[Determinante|Unterdeterminanten]]) der [[Transponieren|transponierten]] Matrix gebildet werden.

    Die Adjugierte ist definiert als:

    $$ A^* = \operatorname{adj}(A) = \left( \operatorname{Cof}(A) \right)^T $$

    wobei $\operatorname{Cof}(A)$ die **Kofaktormatrix** ist.

    Die einzelnen [[Kofaktor|Kofaktoren]] $\operatorname{Cof}_{ij}$ berechnen sich durch:

    $$ \operatorname{Cof}_{ij} = (-1)^{i+j} \cdot \det(A_{ij}) $$

    wobei $A_{ij}$ die [[Untermatrix]] ist, die entsteht, wenn man die $i$-te Zeile und die $j$-te Spalte von $A$ entfernt.

    Somit besteht $A^*$ aus diesen [[Kofaktor|Kofaktoren]], allerdings **transponiert**, d.h. die [[Kofaktor|Kofaktoren]] werden gespiegelt über die Hauptdiagonale angeordnet.

2.  **Mithilfe des [[Gauß-Algorithmus]]:**
    Man bildet eine erweiterte Matrix, indem man die [[Einheitsmatrix]] $E$ rechts neben die Matrix $A$ schreibt: $(A | E)$. Durch Anwendung elementarer Zeilenumformungen (die Schritte des [[Gauß-Algorithmus]]) wird die linke Seite ($A$) in die [[Einheitsmatrix]] umgewandelt. Wenn dies gelingt, steht auf der rechten Seite die [[Inverse Matrix]] $A^{-1}$:

    $$(A | E) \xrightarrow{\text{Zeilenumformungen}} (E | A^{-1})$$

    Wenn während dieses Prozesses auf der linken Seite eine Nullzeile entsteht, ist die Matrix nicht [[Invertierbarkeit|invertierbar]] ($\det(A) = 0$).

    **Beispiel (aus den Notizen):**
    Finde die Inverse von $A = \begin{pmatrix} 1 & 2 \\ 3 & 4 \end{pmatrix}$:

    $$ \begin{pmatrix} 1 & 2 & | & 1 & 0 \\ 3 & 4 & | & 0 & 1 \end{pmatrix} \xrightarrow{R_2 \leftarrow R_2 - 3R_1} \begin{pmatrix} 1 & 2 & | & 1 & 0 \\ 0 & -2 & | & -3 & 1 \end{pmatrix} $$

    $$ \xrightarrow{R_2 \leftarrow -\frac{1}{2}R_2} \begin{pmatrix} 1 & 2 & | & 1 & 0 \\ 0 & 1 & | & 1.5 & -0.5 \end{pmatrix} \xrightarrow{R_1 \leftarrow R_1 - 2R_2} \begin{pmatrix} 1 & 0 & | & -2 & 1 \\ 0 & 1 & | & 1.5 & -0.5 \end{pmatrix} $$

    Die [[Inverse Matrix]] ist somit $A^{-1} = \begin{pmatrix} -2 & 1 \\ 1.5 & -0.5 \end{pmatrix}$.

---

## Verwendung:

```dataview
list from [[Inverse Matrix]]
```