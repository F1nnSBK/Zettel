#Note

2025-05-17

Tags: [[Lineare Regression]], [[Regression]], [[Statistik]], [[Maschinelles Lernen]], [[Datenanalyse]], [[Lineare Algebra]], [[Modellierung]], [[Designmatrix]]

---

Die **Lineare Regression** ist ein statistisches Verfahren zur **[[Modellierung|Modellierung]] der Beziehung** zwischen einer abhängigen Variablen (Zielgröße, oft mit $y$ bezeichnet) und einer oder mehreren unabhängigen Variablen (Prädiktoren, oft mit $X$ bezeichnet). Das Ziel ist, eine **optimale Gerade** (oder eine Hyperebene in höheren Dimensionen) zu finden, die den Zusammenhang in den Datenpunkten am besten beschreibt.

*![[lineare_regression.png]]

Abbildung: Prinzip der Linearen Regression mit Datenpunkten, Regressionsgerade und Residuen (Fehlern)

**Zweck:**

Die Lineare Regression wird verwendet, um:
* Den Einfluss einer oder mehrerer unabhängiger Variablen auf eine abhängige Variable zu verstehen.
* Vorhersagen für die abhängige Variable basierend auf den unabhängigen Variablen zu treffen.
* Muster und Beziehungen in Daten zu identifizieren.

Sie dient als Basis für viele komplexere Regressionsverfahren.

**Mathematische Formulierung:**

Die Beziehung wird als [[Linearkombinationen|lineare Kombination]] der unabhängigen Variablen und zugehöriger Koeffizienten (Gewichte) formuliert. Für $n$ unabhängige Variablen ($X_1, \dots, X_n$) schreiben wir den Zusammenhang als:

$$y = f(X) = c_0 + c_1 \cdot X_1 + c_2 \cdot X_2 + \dots + c_n \cdot X_n$$

Hierbei ist:
* $y$: die abhängige Variable (Zielgröße).
* $X = (X_1, \dots, X_n)$: die unabhängigen Variablen als Vektor oder [[Matrizen|Matrix]].
* $c_0$: der Achsenabschnitt (Intercept), der Wert von $y$, wenn alle $X_i = 0$ sind.
* $c_1, \dots, c_n$: die Koeffizienten (Steigungen), die die Stärke und Richtung der Beziehung zwischen $X_i$ und $y$ beschreiben.
* $f(X)$: die Regressionsfunktion, die den Zusammenhang [[Modellierung|modelliert]].

Die zentrale Aufgabe in der Linearen Regression ist, die optimalen Werte für die Koeffizienten $c_0, c_1, \dots, c_n$ zu finden, die am besten zur Beziehung in den gegebenen Daten passen. Dies geschieht typischerweise durch die Minimierung des Fehlers zwischen den vorhergesagten Werten und den tatsächlichen Werten.

---

## Verwendung:

```dataview
list from [[Lineare Regression]]
```