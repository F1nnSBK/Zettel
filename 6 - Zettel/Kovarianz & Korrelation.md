#Note

2026-05-15

Tags: [[Statistik]], [[Korrelation]], [[Zeitreihen]], [[Bivariate Daten]], [[Machine Learning]]
#deskriptive_statistik

---
Kovarianz und Korrelation beschreiben die Art und Stärke des linearen Zusammenhangs zwischen zwei metrischen Variablen $X$ und $Y$.

### [[Kovarianz]] ($s_{xy}$)

Die Kovarianz ist das durchschnittliche Produkt der Abweichungen beider Variablen von ihrem jeweiligen Mittelwert.
$$s_{xy} = \frac{1}{n-1} \sum_{i=1}^n (x_i - \bar{x})(y_i - \bar{y})$$

- **Interpretation:**  $s_{xy} > 0$: Positiver Gleichlauf (beide steigen).
    - $s_{xy} < 0$: Gegensinniger Verlauf (einer steigt, einer fällt).
    - **Problem:** Die Einheit ist das Produkt der Einheiten von $X$ und $Y$ (z. B. $kg \cdot m$), was die Interpretation unmöglich macht.

### Pearson-Korrelationskoeffizient ($r$)

Die Korrelation normiert die Kovarianz durch das Produkt der Standardabweichungen. Sie ist einheitenlos.
$$r_{xy} = \frac{s_{xy}}{s_x \cdot s_y} \in [-1, 1]$$

- **$r = 1$:** Perfekter positiver linearer Zusammenhang.
- **$r = 0$:** Kein **linearer** Zusammenhang.
- **$r = -1$:** Perfekter negativer linearer Zusammenhang.

### Spearman-Rangkorrelation ($\rho$)

Wenn Zusammenhänge zwar monoton (immer steigend/fallend), aber nicht linear sind, nutzt man die Ränge der Daten statt der Rohwerte.

- **Vorteil:** Robust gegenüber Ausreißern und anwendbar auf ordinalskalierte Daten.
- **Logik:** Berechne den Pearson-Koeffizienten auf Basis der Rangzahlen $R(x_i)$ und $R(y_i)$.

### Autokorrelation (ACF)

In der Zeitreihenanalyse misst die Autokorrelation die Korrelation einer Variable mit sich selbst zu einem früheren Zeitpunkt (Lag $k$).

$$r(k) = \text{Corr}(X_t, X_{t-k})$$

- **Einsatz:** Identifikation von Saisonalitäten (z. B. Peak bei $k=24$ bei stündlichen Stromdaten).

### Scheinkorrelation (Spurious Correlation)

Ein hoher Korrelationskoeffizient ohne kausalen Zusammenhang.
- **Ursache:** Meist eine gemeinsame Drittvariable $Z$, die beide beeinflusst (z. B. "Anzahl Störche" und "Geburtenrate" korrelieren aufgrund der Variable "Ländlichkeit").


---
#### Flashcards

Warum ist die Kovarianz kein geeignetes Maß, um die Stärke eines Zusammenhangs zwischen zwei verschiedenen Studien zu vergleichen?::Da die Kovarianz einheitenabhängig ist. Sie ändert ihren Wert massiv, wenn man z. B. eine Variable von Metern in Millimeter umrechnet, ohne dass sich die Beziehungsstärke ändert.

Was ist der entscheidende Vorteil der Spearman-Rangkorrelation gegenüber Pearson bei nicht-linearen Funktionen?::Spearman bewertet nur die Ordnung (Monotonie). Solange $y$ mit steigendem $x$ ebenfalls steigt, ist $\rho = 1$, selbst wenn die Steigung nicht konstant ist (z. B. bei exponentiellem Wachstum).
<!--SR:!2026-06-09,1,230-->

Warum verschwindet eine Scheinkorrelation oft, wenn man die Daten "partielliert" (Partialkorrelation)?
?
Durch die Partialkorrelation wird der lineare Einfluss der störenden Drittvariable $Z$ rechnerisch eliminiert. Wenn der Zusammenhang zwischen $X$ und $Y$ nur durch $Z$ induziert wurde, sinkt die Korrelation danach auf Null.
<!--SR:!2026-06-09,1,230-->

Was beschreibt eine Autokorrelation von $r(k) \approx 1$ für kleine Lags $k$ in einer Zeitreihe?
?
Sie beschreibt eine hohe Trägheit (Persistenz) im System. Der aktuelle Wert ist stark von seinem unmittelbaren Vorgänger abhängig, was typisch für Trends oder gedämpfte physikalische Prozesse ist.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Kovarianz & Korrelation]]
SORT file.mtime DESC
```