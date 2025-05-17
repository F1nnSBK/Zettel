#Note

2025-05-17

Tags: [[Normalengleichung]], [[Lineare Regression]], [[Regression]], [[Lineare Algebra]], [[Matrizen]], [[Koeffizienten]], [[Kleinste Quadrate]], [[Designmatrix]], [[Optimierung]], [[Inverse Matrix]]

---

Die **Normalengleichung** ist eine Gleichung, die sich aus der Minimierung der [[Kleinste Quadrate|Summe der kleinsten Quadrate (SSE)]] ergibt und eine geschlossene Formel zur Berechnung des optimalen [[Koeffizienten|Koeffizientenvektors]] $\vec{c}$ in der [[Lineare Regression|Linearen Regression]] ($\vec{y} = X\vec{c}$) liefert.

**Herleitung:**

Wir wollen die [[Kleinste Quadrate|SSE]] minimieren: $\min_{\vec{c}} ||\vec{y} - X\vec{c}||^2$.
Wir wissen, dass $SSE = (\vec{y} - X\vec{c})^T (\vec{y} - X\vec{c})$. Wenn wir dies ausmultiplizieren, erhalten wir:
$SSE = \vec{y}^T \vec{y} - \vec{y}^T X\vec{c} - (X\vec{c})^T \vec{y} + (X\vec{c})^T X\vec{c}$
Da $(X\vec{c})^T \vec{y} = \vec{c}^T X^T \vec{y}$ und $\vec{y}^T X\vec{c}$ ein Skalar ist (und somit gleich seiner Transponierten), gilt $\vec{y}^T X\vec{c} = (X\vec{c})^T \vec{y}$.
$SSE = \vec{y}^T \vec{y} - 2\vec{y}^T X\vec{c} + \vec{c}^T X^T X\vec{c}$

Um den Minimum der SSE zu finden, nehmen wir die partielle Ableitung nach dem Vektor $\vec{c}$ und setzen diese gleich Null:

$$ \nabla_{\vec{c}} (\vec{y}^T \vec{y} - 2\vec{y}^T X\vec{c} + \vec{c}^T X^T X\vec{c}) = \vec{0} $$

Die Ableitung von $\vec{y}^T \vec{y}$ nach $\vec{c}$ ist $\vec{0}$.
Die Ableitung von $-2\vec{y}^T X\vec{c}$ nach $\vec{c}$ ist $-2(X^T \vec{y})^T = -2 X^T \vec{y}$ (unter Verwendung der Regel $\nabla_{\vec{x}}(\vec{a}^T \vec{x}) = \vec{a}$ und Transponieren).
Die Ableitung von $\vec{c}^T X^T X\vec{c}$ nach $\vec{c}$ ist $2 X^T X\vec{c}$ (unter Verwendung der Regel $\nabla_{\vec{x}}(\vec{x}^T A \vec{x}) = 2 A \vec{x}$ für symmetrisches A; hier ist $X^T X$ symmetrisch).

Setzen wir die Ableitung gleich Null:

$$ -2 X^T \vec{y} + 2 X^T X \vec{c} = \vec{0} $$

Durch Umstellung erhalten wir die **Normalengleichung**:

$$ X^T X \vec{c} = X^T \vec{y} $$

**Lösung für den [[Koeffizienten|Koeffizientenvektor]] $\vec{c}$:**

Wenn die Matrix $X^T X$ [[Invertierbarkeit|invertierbar]] ist, können wir die Normalengleichung nach $\vec{c}$ auflösen, indem wir von links mit der [[Inverse Matrix|inversen Matrix]] $ (X^T X)^{-1} $ multiplizieren:

$$ (X^T X)^{-1} (X^T X \vec{c}) = (X^T X)^{-1} (X^T \vec{y}) $$
$$ I \vec{c} = (X^T X)^{-1} X^T \vec{y} $$
$$ \vec{c} = (X^T X)^{-1} X^T \vec{y} $$

Diese Formel liefert den optimalen [[Koeffizienten|Koeffizientenvektor]] $\vec{c}$ (die Steigungen und den Achsenabschnitt) im Sinne der [[Kleinste Quadrate|kleinsten Quadrate]].

**Bedingung für eine eindeutige Lösung:**

Es gibt genau dann eine eindeutige Lösung für $\vec{c}$ mithilfe dieser Formel, wenn die Matrix $X^T X$ **[[Invertierbarkeit|invertierbar]]** ist. Dies ist der Fall, wenn die [[Designmatrix]] $X$ **vollen Spaltenrang** hat, d.h., die Spalten von $X$ (die unabhängigen Variablen plus die Einsen-Spalte) sind [[Lineare Unabhängigkeit|linear unabhängig]].

**[[Beispiel]] zur [[Berechnung]] von $\vec{c}$ mithilfe der Normalengleichung:**

Gegeben sei $X = \begin{pmatrix} 1 & 2 \\ 1 & 3 \\ 1 & 4 \\ 1 & 5 \end{pmatrix}$ und $\vec{y} = \begin{pmatrix} 4 \\ 6 \\ 5 \\ 3 \end{pmatrix}$

1.  **Berechne $X^T X$ und $X^T \vec{y}$:**
    $$
    X^T X = \begin{pmatrix} 1 & 1 & 1 & 1 \\ 2 & 3 & 4 & 5 \end{pmatrix} \begin{pmatrix} 1 & 2 \\ 1 & 3 \\ 1 & 4 \\ 1 & 5 \end{pmatrix} = \begin{pmatrix} 1+1+1+1 & 2+3+4+5 \\ 2+3+4+5 & 4+9+16+25 \end{pmatrix} = \begin{pmatrix} 4 & 14 \\ 14 & 54 \end{pmatrix}
    $$
    $$
    X^T \vec{y} = \begin{pmatrix} 1 & 1 & 1 & 1 \\ 2 & 3 & 4 & 5 \end{pmatrix} \begin{pmatrix} 4 \\ 6 \\ 5 \\ 3 \end{pmatrix} = \begin{pmatrix} 4+6+5+3 \\ 8+18+20+15 \end{pmatrix} = \begin{pmatrix} 18 \\ 61 \end{pmatrix}
    $$
    (Hinweis: Die Werte im PDF für $X^T X$ und $X^T \vec{y}$ im Beispiel scheinen Tippfehler zu enthalten, basierend auf den Matrizen $X$ und $\vec{y}$. Ich rechne hier mit den korrekten Ergebnissen.)

2.  **Berechne $(X^T X)^{-1}$:**
    Wir brauchen die [[Inverse Matrix]] von $\begin{pmatrix} 4 & 14 \\ 14 & 54 \end{pmatrix}$. Die [[Determinante]] ist $4 \cdot 54 - 14 \cdot 14 = 216 - 196 = 20$.
    $$(X^T X)^{-1} = \frac{1}{20} \begin{pmatrix} 54 & -14 \\ -14 & 4 \end{pmatrix} = \begin{pmatrix} 54/20 & -14/20 \\ -14/20 & 4/20 \end{pmatrix} = \begin{pmatrix} 2.7 & -0.7 \\ -0.7 & 0.2 \end{pmatrix}$$

3.  **Berechne $\vec{c} = (X^T X)^{-1} X^T \vec{y}$:**
    $$
    \vec{c} = \begin{pmatrix} 2.7 & -0.7 \\ -0.7 & 0.2 \end{pmatrix} \begin{pmatrix} 18 \\ 61 \end{pmatrix} = \begin{pmatrix} 2.7 \cdot 18 + (-0.7) \cdot 61 \\ -0.7 \cdot 18 + 0.2 \cdot 61 \end{pmatrix} = \begin{pmatrix} 48.6 - 42.7 \\ -12.6 + 12.2 \end{pmatrix} = \begin{pmatrix} 5.9 \\ -0.4 \end{pmatrix}
    $$
    (Hinweis: Auch hier weicht das Ergebnis im PDF Beispiel ab. Die Berechnung sollte $\vec{c} = \begin{pmatrix} 5.9 \\ -0.4 \end{pmatrix}$ ergeben, was $c_0 = 5.9$ und $c_1 = -0.4$ bedeutet.)

Die optimale Regressionsgerade ist somit $y = -0.4x + 5.9$.

---

## Verwendung:

```dataview
list from [[Normalengleichung]]
```