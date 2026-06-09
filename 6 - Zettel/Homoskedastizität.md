#Note

2026-05-19

Tags: [[Statistik]], [[Lineare Regression]], [[Deskriptive Statistik]], [[Regressionsanalyse]], [[Heteroskedastizität]]
#statistik

---
**Homoskedastizität** (Gleichschaligkeit) ist eine zentrale Standardannahme der klassischen linearen Regression. Sie besagt, dass die Varianz der Residuen (Fehlerterme) für alle Werte der unabhängigen Variable $X$ konstant ist.
### Definition

Das Modell der linearen Regression lautet $y_i = a + b \cdot x_i + \epsilon_i$. Homoskedastizität fordert:

$$\text{Var}(\epsilon_i \mid x_i) = \sigma^2 = \text{konstant für alle } i$$

### Das Gegenteil: Heteroskedastizität

Liegt keine konstante Varianz vor, spricht man von **Heteroskedastizität**.

- **Klassisches Szenario:** Bei der Analyse von Einkommen ($X$) und Konsumausgaben ($Y$). Menschen mit geringem Einkommen haben eine sehr begrenzte, homogene Streuung bei den Ausgaben (Existenzminimum). Menschen mit hohem Einkommen streuen extrem (einige sparen extrem, andere geben alles aus).


### Diagnose im Residualplot

Zur Überprüfung plottet man die Residuen $e_i = y_i - \hat{y}_i$ auf der y-Achse gegen die vorhergesagten Werte $\hat{y}_i$ (oder $x_i$) auf der x-Achse.

- **Homoskedastizität:** Die Punkte bilden einen gleichmäßig breiten, horizontalen "Streifen" um die Nulllinie.

- **Heteroskedastizität:** Die Punkte zeigen ein systematisches Muster, meist eine **Trichterform** oder einen Fächer (die Streuung wird nach rechts hin breiter oder schmaler).


### Konsequenzen für das Modell

Wenn Heteroskedastizität ignoriert wird:

1. Die OLS-Schätzung für $a$ und $b$ ist weiterhin **erwartungstreu**, aber nicht mehr **effizient** (es gäbe bessere Schätzer, z. B. Weighted Least Squares, WLS).

2. Die Standardfehler der Koeffizienten werden systematisch verzerrt geschätzt. Dadurch sind Konfidenzintervalle und Signifikanztests ($t$-Test) ungültig.

---
### Flashcards

Was versteht man unter Homoskedastizität in der Regressionsanalyse?::Die Annahme, dass die Varianz der Fehlerterme (Residuen) über den gesamten Wertebereich der unabhängigen Variable konstant bleibt.

Welches visuelle Muster im Residualplot deutet auf das Vorliegen von Heteroskedastizität hin?::Eine Trichter- oder Fächerform, bei der sich die vertikale Streuung der Residuen mit steigenden Werten auf der x-Achse systematisch verändert.

Warum ist Heteroskedastizität problematisch für die induktive Statistik ($t$-Tests)?
?
Weil sie die Berechnung der Standardfehler der Regressionskoeffizienten verzerrt. Da die Standardfehler als Basis für die Teststatistiken dienen, führen verzerrte Fehler zu falschen p-Werten und somit zu fehlerhaften Signifikanzaussagen.

Mit welcher Transformation der abhängigen Variable kann man Heteroskedastizität im Modell oft reduzieren?
?
Mit einer **Logarithmus-Transformation** ($\log(Y)$). Sie staucht die großen Werte der y-Achse zusammen und komprimiert damit auch die anwachsende Streuung (Varianzstabilisierung).

### Verwendung

---

Code-Snippet

```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Homoskedastizität]]
SORT file.mtime DESC
```