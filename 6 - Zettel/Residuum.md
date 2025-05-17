#Note

2025-05-17

Tags: [[Residuum]], [[Lineare Regression]], [[Regression]], [[Statistik]], [[Maschinelles Lernen]], [[Kleinste Quadrate]]

---

Ein **Residuum**, auch **Fehler** genannt, in der [[Lineare Regression|Linearen Regression]] ist die Differenz zwischen dem tatsächlich beobachteten Wert der abhängigen Variablen ($y_j$) und dem Wert, der von der Regressionslinie oder -hyperebene für den entsprechenden Punkt vorhergesagt wird ($\hat{y}_j$).

**Definition:**

Das Residuum $\epsilon_j$ für den $j$-ten Datenpunkt ist gegeben durch:

$$ \epsilon_j = y_j - \hat{y}_j $$

Dabei ist $\hat{y}_j$ der vorhergesagte Wert, berechnet durch das Regressionsmodell: $\hat{y}_j = c_0 + c_1 x_j + \dots + c_n x_{nj}$.

**Residuenvektor:**

Der **Residuenvektor** $\vec{\epsilon}$ enthält die Residuen für alle $m$ Datenpunkte und kann in [[Matrizen|Matrixnotation]] ausgedrückt werden als:

$$ \vec{\epsilon} = \vec{y} - \hat{\vec{y}} = \vec{y} - X\vec{c} $$

wobei $\vec{y}$ der Vektor der tatsächlichen Werte, $\hat{\vec{y}}$ der Vektor der vorhergesagten Werte, $X$ die [[Designmatrix]] und $\vec{c}$ der [[Koeffizienten|Koeffizientenvektor]] ist.

**Bedeutung:**

Residuen sind ein Maß für die **Qualität der Modellanpassung** für jeden einzelnen Datenpunkt. Das Ziel des Prinzips der [[Kleinste Quadrate|kleinsten Quadrate]] ist es, die Summe der Quadrate dieser Residuen (die [[Kleinste Quadrate|SSE]]) zu minimieren, um die beste Anpassung an die Daten zu finden.

---

## Verwendung:

```dataview
list from [[Residuum]]
```