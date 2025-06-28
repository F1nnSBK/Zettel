#Note

2025-05-15

Tags: [[Cramer-Regel]], [[Lineare Gleichungssysteme]], [[Determinante]], [[Matrizen]], [[Quadratische Matrix]], [[Invertierbarkeit]], [[Lösbarkeit]]

---

Die **[[Cramer-Regel]]** ist eine Methode zur direkten Lösung eines **[[Lineare Gleichungssysteme|Linearen Gleichungssystems]]** ($A\vec{x} = \vec{b}$), vorausgesetzt, die Koeffizienten-[[Matrizen|Matrix]] $A$ ist eine **[[Quadratische Matrix|quadratische Matrix]]** und **[[Invertierbarkeit|invertierbar]]**. Die [[Invertierbarkeit]] wird dabei durch die [[Determinante]] geprüft: Die [[Cramer-Regel]] ist anwendbar, wenn $\det(A) \neq 0$.

**Formel:**

Für ein System mit $n$ Gleichungen und $n$ Unbekannten ($A\vec{x} = \vec{b}$), bei dem $\det(A) \neq 0$, kann jede Komponente $x_i$ des Lösungsvektors $\vec{x}$ berechnet werden als:

$$x_i = \frac{\det(A_i)}{\det(A)}$$

Dabei ist $A_i$ die Matrix, die entsteht, indem man in der ursprünglichen Matrix $A$ die $i$-te Spalte durch den Vektor der rechten Seiten $\vec{b}$ ersetzt.

**[[Beispiel]] (Lösung eines $2 \times 2$ Systems mit [[Cramer-Regel]]):**

Löse das folgende [[Lineare Gleichungssystem]]:
$2x + y = 5$
$x - 3y = -8$

Wir schreiben das System in Matrixform $A\vec{x} = \vec{b}$:

$$
A = \begin{pmatrix} 2 & 1 \\ 1 & -3 \end{pmatrix}, \quad \vec{x} = \begin{pmatrix} x \\ y \end{pmatrix}, \quad \vec{b} = \begin{pmatrix} 5 \\ -8 \end{pmatrix}
$$

1.  **Berechne die [[Determinante]] von $A$:**

    $$\det(A) = \det \begin{pmatrix} 2 & 1 \\ 1 & -3 \end{pmatrix} = (2)(-3) - (1)(1) = -6 - 1 = -7$$

    Da $\det(A) = -7 \neq 0$, ist die Matrix $A$ [[Invertierbarkeit|invertierbar]], und die [[Cramer-Regel]] ist anwendbar.

2.  **Erstelle $A_1$ und berechne $\det(A_1)$:**
    Ersetze die 1. Spalte von $A$ durch $\vec{b}$.

    $$
    A_1 = \begin{pmatrix} 5 & 1 \\ -8 & -3 \end{pmatrix}
    $$

    $$\det(A_1) = \det \begin{pmatrix} 5 & 1 \\ -8 & -3 \end{pmatrix} = (5)(-3) - (1)(-8) = -15 - (-8) = -15 + 8 = -7$$

3.  **Erstelle $A_2$ und berechne $\det(A_2)$:**
    Ersetze die 2. Spalte von $A$ durch $\vec{b}$.

    $$
    A_2 = \begin{pmatrix} 2 & 5 \\ 1 & -8 \end{pmatrix}
    $$

    $$\det(A_2) = \det \begin{pmatrix} 2 & 5 \\ 1 & -8 \end{pmatrix} = (2)(-8) - (5)(1) = -16 - 5 = -21$$

4.  **Berechne $x$ und $y$ mithilfe der [[Cramer-Regel]] Formel:**

    $$x = \frac{\det(A_1)}{\det(A)} = \frac{-7}{-7} = 1$$

    $$y = \frac{\det(A_2)}{\det(A)} = \frac{-21}{-7} = 3$$

Die Lösung des [[Lineare Gleichungssysteme|LGS]] ist somit $x=1$ und $y=3$.

Die [[Cramer-Regel]] ist besonders nützlich für kleine Systeme oder wenn man nur die Werte für einzelne Unbekannte benötigt, kann aber für größere Systeme rechnerisch aufwendig werden im Vergleich zum [[Gauß-Algorithmus]].

---

## Verwendung:

```dataview
list from [[Cramer-Regel]]
```