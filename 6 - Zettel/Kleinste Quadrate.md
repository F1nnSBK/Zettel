#Note

2025-05-17

Tags: [[Kleinste Quadrate]], [[SSE]], [[Lineare Regression]], [[Regression]], [[Statistik]], [[Maschinelles Lernen]], [[Residuum]], [[Optimierung]]

---

Das Prinzip der **kleinsten Quadrate** ist die am häufigsten verwendete Methode zur Bestimmung der Koeffizienten einer [[Lineare Regression|Linearen Regression]]. Das Ziel ist, die Koeffizienten ($c_0, c_1, \dots, c_n$) so zu wählen, dass die Summe der quadrierten Fehler zwischen den tatsächlichen Beobachtungswerten ($y_j$) und den durch das Modell vorhergesagten Werten ($f(x_j) = c_0 + c_1 x_j + \dots$) minimiert wird.

**Residuum (Fehler):**

Das **Residuum** (oder der Fehler) $\epsilon_j$ für einen einzelnen Datenpunkt $(x_j, y_j)$ ist die vertikale Distanz zwischen dem beobachteten Wert $y_j$ und dem vom Regressionsmodell vorhergesagten Wert $\hat{y}_j$:

$$ \epsilon_j = y_j - \hat{y}_j = y_j - (c_0 + c_1 x_j + \dots + c_n x_{nj}) $$

**Summe der kleinsten Quadrate (SSE):**

Die **Summe der kleinsten Quadrate (SSE)**, auch Summe der quadrierten Residuen (Sum of Squared Residuals) genannt, ist die Summe der Quadrate dieser Residuen über alle $m$ Datenpunkte:

$$ SSE = \sum_{j=1}^m \epsilon_j^2 = \sum_{j=1}^m (y_j - (c_0 + c_1 x_j + \dots + c_n x_{nj}))^2 $$

Die Fehler werden quadriert, um negative und positive Fehler gleich zu behandeln und größere Fehler stärker zu bestrafen.

In der [[Matrizen|Matrixnotation]] ($A\vec{x} = \vec{b}$ bzw. hier $\vec{y} = X\vec{c}$) lässt sich die SSE schreiben als die quadrierte [[Norm]] des Residuenvektors $\vec{\epsilon} = \vec{y} - X\vec{c}$:

$$ SSE = ||\vec{y} - X\vec{c}||^2 = (\vec{y} - X\vec{c})^T (\vec{y} - X\vec{c}) $$

**Ziel:**

Das Prinzip der kleinsten Quadrate besteht darin, den Koeffizientenvektor $\vec{c}$ zu finden, der die SSE **minimiert**:

$$ \min_{\vec{c}} SSE = \min_{\vec{c}} ||\vec{y} - X\vec{c}||^2 $$

Die Lösung dieses **[[Optimierung|Minimierungsproblems]]** führt zur [[Normalengleichung|Normalengleichung]], mit der die optimalen Koeffizienten $\vec{c}$ berechnet werden können.

---

## Verwendung:

```dataview
list from [[Kleinste Quadrate]]
```