#Note

2025-05-17

Tags: [[Dreiecksmatrix]], [[Spezielle Matrizen]], [[Matrizen]], [[Lineare Algebra]], [[Determinante]], [[Eigenwerte]], [[Zeilenstufenform]]

---

Eine **Dreiecksmatrix** ist eine [[Quadratische Matrix|quadratische Matrix]], bei der alle Einträge entweder oberhalb oder unterhalb der Hauptdiagonale Null sind. Man unterscheidet zwei Arten:

1.  **Obere Dreiecksmatrix:** Alle Einträge **unterhalb** der Hauptdiagonale sind Null ($a_{ij} = 0$ für $i > j$).

    Beispiel (für eine $3 \times 3$ Matrix):
    $$
    \begin{pmatrix}
    a_{11} & a_{12} & a_{13} \\
    0 & a_{22} & a_{23} \\
    0 & 0 & a_{33}
    \end{pmatrix}
    $$

2.  **Untere Dreiecksmatrix:** Alle Einträge **oberhalb** der Hauptdiagonale sind Null ($a_{ij} = 0$ für $i < j$).

    Beispiel (für eine $3 \times 3$ Matrix):
    $$
    \begin{pmatrix}
    a_{11} & 0 & 0 \\
    a_{21} & a_{22} & 0 \\
    a_{31} & a_{32} & a_{33}
    \end{pmatrix}
    $$

**Eigenschaften:**

* Die [[Determinante]] einer Dreiecksmatrix ist wie bei einer [[Diagonalmatrix]] das **Produkt ihrer Diagonalelemente**: $\det(T) = a_{11} \cdot a_{22} \cdot \dots \cdot a_{nn}$.
* Die [[Eigenwerte]] einer Dreiecksmatrix sind ebenfalls genau ihre **Diagonalelemente**.
* Eine [[Quadratische Matrix|quadratische Matrix]] in [[Zeilenstufenform (ZSF)]] ist immer eine obere Dreiecksmatrix.

---

## Verwendung:

```dataview
list from [[Dreiecksmatrix]]
```