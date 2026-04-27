#Note

2026-04-21

Tags: [[6 - Zettel/Business Intelligence]], [[Business Analytics]], [[Glättung]], [[Holt-Winter]], [[Zeitreihen]], [[Zeitreihenkomponenten]]
#bi

---
Fragestellungen:
Welches Modell eignet sich zur Schätzung der Zeitreihen?
Wie gut sind die verwendeten Modelle?
Sind die Modelle besser als naive Modelle?

Gütemaße:
   + Mean Absolute Deviation MAD $$MAD = \frac{1}{K}\sum_{k=1}^{K}|e_{T + k}|$$
   + Mean Absolute Percentage Error MAPE $$MAPE = \frac{1}{K}\sum_{k=1}^{K}|\frac{e_{T + k}}{Y_{T+k}}|$$
+ Mean Squared Error MSE $$MSE = \frac{1}{N}\sum_{i=1}^{N}(y_i - \hat{y}_i)^2$$
  Man quadriert den absoluten Abstand, damit sich negative und positive Abweichungen nicht aufheben. Im Vergleich zum MAD ist der MSE empfindlicher.
+ Root Mean Squared Error MSE $$RMSE = \sqrt{\frac{1}{N}\sum_{i=1}^{N}(y_i - \hat{y}_i)^2}$$
  Der RMSE ist im Vergleich zum MSE besser, wenn der Abstand zur Vorhersage eine tatsächliche, interpretierbare Bedeutung hat und man diese behalten möchte.

### Naive Forecast
Letzer Datenpunkt ist die Prognose für den nächsten
$$\hat{y}_{t+1} = y_t$$
Nachteile
+ Keine Berücksichtigung von Trends in den Prognosen
+ Keine Berücksichtigung von Saisoneffekten
+ Für langfristige Periode ungeeignet, da immer nur der letzte tatsächliche Wert verwendet wird
Vorteile
+ Stabile Zeitreihen mit möglichst wenig Schwankungen
+ Als Vergleichswerte für andere Prognoseverfahren

### Simple Average
Vorhersage ist einfach der Durchschnitt alle Beobachtungen
$$\hat{y}_{t+1} = \frac{y_t+y_{t+1}+\dots+y_{t-n}}{t}$$
Vorteile
+ Einfach
Nachteile
+ Trends werden nur langsam berücksichtigt
+ Keine Berücksichtigung von Saisoneffekten
+ Weiter entfernte Prognosen sind nicht möglich oder nur unter Verwendung von vorherigen Prognosen. Dadurch langsame Glättung der Prognosen.

## Moving Averages
Gleitender Durchschnitt
Bei der Methode der gleitenden Durchschnitte ergibt sich der Prognosewert aus dem Mittelwert eines vorgegebenen Zeitfensters $w$.

### Trailing Moving Average
Durchschnitt aus einem Zeitfenster der Vergangenheit direkt vor dem Prognosewert, bei dem alle Beobachtungen alle gleich gewichtet werden.

Sei $w=4$:
$$MA_t=\frac{y_{t-1}+y_{t-2}+y_{t-3}+y_{t-4}}{4}$$
### Weighted Moving Average
Durchschnitt aus einem Zeitfenster der Vergangenheit direkt vor dem Prognosewert, bei dem bewusst die einzelnen Beobachtungen unterschiedlich gewichtet werden. In der Regel gewichtet man jüngere Beobachtungen stärker. Vorstufe zum exponentiell gewichteten Moving Average (EWMA).

Sei $w=4$:
$$MA_t=\frac{0,8 \cdot y_{t-1}+0,6 \cdot y_{t-2}+0,4 \cdot y_{t-3}+0,2 \cdot y_{t-4}}{4}$$

Moving Averages werden teilweise zur Prognose verwendet, wenn kein Trend oder Saisonalität vorliegen, da sowohl Trend als auch Saisonalität im Modell nicht berücksichtigt werden.

## Exponential Smoothing
Ältere Beobachtungen werden exponentiell weniger stark gewichtet

### Simple Exponential Smoothing (SES)
Der Wert aus der Vergangenheit (die einfache Beobachtung) wird als Level $L_t$ bezeichnet. Werte aus der näheren Vergangenheit haben eine höhere Bedeutung.

$$\hat{y}_{t+1}=\alpha \cdot y_t +\alpha(1-\alpha)y_{t-1}+\alpha(1-\alpha)^2 y_{t-2} +\dots$$

Wird $\alpha = 1$ gewählt, entspricht dies wieder der naiven Prognose, da dann nur der letzte Wert die Basis für die Prognose der nächsten Periode bildet.
- **Großes $\alpha$:** Starke Gewichtung der jüngsten Werte (Modell reagiert schnell auf Änderungen).
- **Kleines $\alpha$:** Starke Glättung (Modell ist träge, ignoriert Ausreißer).
Probleme:
Beim SES wird nur *ein* Prognosewert für die nächste Periode erstellt.
Für die erste Periode existiert kein Prognosewert, so dass hier ein Startwert vorgegeben werden muss.
Der optimale Glättungsparameter 𝛼 ist der Wert, mit dem die Fehler der Schätzung möglichst minimiert wird -> Optimierung.

### Double Exponential Smoothing (DES - Holt's Linear)
Das DES erweitert das SES mit einer Trendkomponente $T_t$. Der Prognosewert ergibt sich additiv aus den Komponenten.
$$
\hat{y}_{t+k} = L_t + k \cdot T_t
$$
$$
L_t = \alpha y_t + (1 - \alpha)(L_{t-1} + T_{t-1})
$$
$$
T_t = \beta (L_t - L_{t-1}) + (1 - \beta) \cdot T_{t-1}
$$
Dabei ist $k$ die Anzahl der Perioden. Die Zeitreihe wird zerlegt in eine Level-Komponente und eine Trendkomponente. DIe Levelkomponente stellt quasi den jeweiligen Ausgangswert in einer Periode dar. Die Trendkomponente entspricht der erwarteten Steigung zur nächsten Periode. Die Smoothing-Parameter $\alpha$ und $\beta$ werden nun so gewählt, dass der Fehler minimiert wird.
Level und Trend werden ab Start nicht mehr aktualisiert → Prognosen nutzen letzten Level + konstanten Trend → nur für kurze Horizonte geeignet.
Das Double Exponential Smoothing funktioniert gut in Zeitreihen mit Trend und ohne Saisoneffekte. Durch die Glättung werden auch vergangene Informationen mit berücksichtigt.

### Triple Exponential Smoothing (TES - Holt-Winter)
Im Holt-Winters Modell des Triple Exponential Smoothing wird die Zeitreihe in Level-, Trend- und Saisonkomponente zerlegt. Die einzelnen Komponenten werden dann exponentiell abnehmend gewichtet und zur Prognose reaggegiert.
Der Prognosewert ergibt sich im additiven Modell dann aus der Summe der drei Komponenten. Da mit jeder neuen Periode ein Wert hinzukommt, erfolgt die Glättung für alle drei Komponenten permanent.

##### Additives Modell
$$
\hat{y}_{t+k} = L_t + k \cdot T_t + S_{t+k-M}
$$
$$
L_t = \alpha (y_t - S_{t-M}) + (1 - \alpha)(L_{t-1} + T_{t-1})
$$
$$
T_t = \beta (L_t - L_{t-1}) + (1 - \beta) \cdot T_{t-1}
$$
$$
S_t = \gamma (y_t - L_t) + (1 - \gamma) \cdot S_{t-M}
$$

##### Multiplikatives Modell










---
#### Flashcards

Hier steht eine Frage :: Hier steht die Antwort.

Hier steht eine Frage mit Formel oder mehr Text?
?
Hier steht die Antwort $a² = b² + c² $


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Note]]
SORT file.mtime DESC
```