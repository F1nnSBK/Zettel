#Note

2026-05-15

Tags: [[Statistik]], [[Lineare Regression]], [[Bivariate Daten]], [[Machine Learning]], [[Prognose]]
#deskriptive_statistik
 
---
Die **einfache lineare Regression** modelliert den Zusammenhang zweier metrischer Variablen durch eine Gerade. Ziel ist es, die abhängige Variable $Y$ (Wirkung) durch die unabhängige Variable $X$ (Ursache/Einflussfaktor) zu erklären.

### Das Modell

Die Gleichung der Regressionsgeraden lautet:

$$\hat{y} = a + b \cdot x$$

- **$b$ (Regressionskoeffizient/Steigung):** Gibt an, um wie viele Einheiten $\hat{y}$ steigt, wenn $x$ um eine Einheit zunimmt.
- **$a$ (Achsenabschnitt/Intercept):** Der geschätzte Wert von $y$, wenn $x=0$ ist.

### Methode der kleinsten Quadrate (OLS)

Um die „beste“ Gerade zu finden, minimiert man die Summe der quadrierten Residuen (Abweichungen):

$$\sum_{i=1}^n (y_i - \hat{y}_i)^2 \to \min$$

### Berechnung der Koeffizienten

1. **Steigung $b$:** Basiert auf dem Verhältnis von gemeinsamer Variation zu Eigenvariation von $X$.
$$b = \frac{s_{xy}}{s_x^2} = \frac{\text{Kovarianz}(x,y)}{\text{Varianz}(x)}$$

2. **Achsenabschnitt $a$:** Resultiert daraus, dass die Gerade durch den Schwerpunkt $(\bar{x}, \bar{y})$ gehen muss.
$$a = \bar{y} - b \cdot \bar{x}$$


### Gütemaß: [[Bestimmtheitsmaß]] ($R^2$)

Das Bestimmtheitsmaß gibt an, welcher Anteil der Gesamtvarianz von $Y$ durch das Modell (die Gerade) erklärt wird.

- Im Fall der einfachen linearen Regression gilt: $R^2 = r_{xy}^2$ (Quadrat des Pearson-Korrelationskoeffizienten).
- $R^2 = 1$: Alle Punkte liegen exakt auf der Geraden.
- $R^2 = 0$: Das Modell hat keinen Erklärungsgehalt (horizontale Gerade durch $\bar{y}$).

---

### Flashcards

Wie lautet die Formel für die Steigung $b$ der Regressionsgeraden basierend auf Kovarianz und Varianz?
?
$b = \frac{s_{xy}}{s_x^2}$ (Kovarianz von $x$ und $y$ dividiert durch die Varianz von $x$).
<!--SR:!2026-06-09,1,230-->

Welchen Punkt im Koordinatensystem passiert jede Regressionsgerade, die nach der Methode der kleinsten Quadrate berechnet wurde, zwingend?::Den Schwerpunkt der Datenwolke $(\bar{x}, \bar{y})$.

Was beschreibt das Residuum $e_i$ in der Regressionsanalyse?
?
Das Residuum $e_i = y_i - \hat{y}_i$ ist die Differenz zwischen dem tatsächlich beobachteten Wert $y_i$ und dem vom Modell vorhergesagten Wert $\hat{y}_i$. Es repräsentiert den nicht erklärten Teil der Daten.

Wie interpretiert man ein Bestimmtheitsmaß von $R^2 = 0,85$?
?
85 % der in der abhängigen Variable $Y$ beobachteten Varianz können durch den linearen Zusammenhang mit der unabhängigen Variable $X$ erklärt werden. Die restlichen 15 % sind auf andere Einflüsse oder Zufallsschwankungen zurückzuführen.
<!--SR:!2026-06-09,1,230-->

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Regressionsgerade]]
SORT file.mtime DESC
```