#Note

2026-04-08

Tags: [[]], [[]], [[]]
#bi

---

**Business Analytics** beschreibt den ...
(Mehr Vorhersagen für die Zukunft)

**Business Intelligence** beschreibt...
(Mehr deskriptive Analyse)



### 1 Problemstellung
Welches Modell ist das beste zur Prognose und wie gut ist es insgesamt?

### 2 Datenerhebung und Visualisierung
Zeitreihe visualisieren
Zeitreihenkomponenten:
	Basiskomponente -> $\alpha$ (y-Achsenabschnitt)
	Trendkomponente -> Steigung
	Saisonale Komponente -> Schwankungen

### 3 Modellformulierung

**Grundmodell**: (Prognose = Basiskomp. + Trendkomp. + Saisonkomp.)
$\hat{y}$ = $\alpha + \beta + \gamma$

**Deterministische Modelle**: (Geht immer auf, ohne Fehler)
$Y = f(x)$
$y = b_0 + b_1 * X$

**Stochastische Modelle**: (Fehler möglichst niedrig halten)
$Y = f(x) + e$
$y = b_0 + b_1 * X + e$
-> Minimierung von e

Basismodelle:
Additives Modell (linear): $\hat{Y} = \alpha + \beta + \gamma$
Mulitplikatives Modell (expo.): $\hat{Y} = \alpha * \beta * \gamma$

Modell ohne Saisonkomponente:
$\hat{Y}_t = \alpha + \beta_1 * t$

Modell mit Saisonkomponente:

Modell mit Saisonkomponente und Kausalvariablen:

Im Paper dann die Variablen und Komponenten immer ausführlich begründen.


Lag-Variablen
-> verzögerte, zurücksetzte Variable um mehr Einfluss zu haben

Prognosen
Prognoseerstellung
Werte einsetzen
Prognosegüte 
MAPE = $\frac{1}{N} \sum$
MAD

Wie legt man die Schätzperiode und die Validierungsperiode fest?
-> Wichtig für Paper, Trend (Für SMARD Market Regime)



# Smoothing-Modelle (Glättung)
Gütemaße
MAD, MAPE, MSE, RMSE

## Naive Forecasts
Die naive Prognose ist einfach der letzte verfügbare Wert der Zeitreihe. Sie wird als bester Schätzer der nächsten Periode verwendet.

$$\hat{y}_{t+1} = y_t$$
Vorteile

Nachteile

Keine Trends
Keine Saisoneffekte
Keine langfristigen Vorhersagen
-> Trivial

## Simple Average
Alle Werte aus der Vergangenheit werden mit in die Prognose einbezogen.

$$\hat{y}_{t+1} = \frac{y_t + y_{t-1} + \dots + y_{t-n}}{t}$$
Vorteile

Nachteile


## Moving Average
Verwenden ein Zeitfenster $w$ über $t$ Zeitpunkte für den Durchschnitt.
#### Trailing Moving Average
Letze $t$ Zeitpunkte
Annahme: Die letzten $t$ Punkte sind relevant für die Zukunft.
#### Weighted Moving Average
Unterschiedliche Gewichtung der letzen $t$ Punkte.
Annahme: Die näheren Beobachtungen sind wichtiger für die Prognose als Beobachtungen, die weiter Weg sind.

Sind für Prognosen schwierig, da sie Trends nicht berücksichtigen aber zb für die reine Trenderkennung bei verrauschten Daten sinnvoll.

## Exponential Smooting
Gedankennotiz: Verbindung zu den Momenten aus fortgeschrittener Statistik? Gegenschritte?

#### Simple Exponential Smoothing
Lässt die Gewichtungen alter Werte mit voranschreitender Zeit exponentiell weniger wiegen. 
Probleme
Nur ein Prognosewert
Wahl der Startwerts
Wahl des Smoothingparameters $\alpha$

#### Double Exponential Smoothing
Levelkomponente
Trendkomponente

Bei dem exponentiellen Glätten nehmen wir jetzt nicht die vollen Werte der Trend- & Levelkomponenten sondern eben nur Bruchteile (exponentiell absteigend).

Finales Modell

#### Triple Exponential Smoothing
Levelkomponente
Trendkomponente
Saisonkomponente

Gesamtes Modell nach Holt-Winter (additiv)


Gesamtes Modell nach Holt-Winter (multiplikativ)

Upper Confidence Level

Lower Confidence Level


ARIMA
(AutoRegressive Integrated Moving Average)

Zusammenhang Lag-Variable: Eine Variable, deren Wert sich aus einem vorhergehenden Wert der Zeitreihe ergibt.

Auto-Regressiv: Kann ich aus der unmittelbaren Vergangenheit die Zukunft vorhersagen?
-> Impliziert hohe Korrelation zwischen dem aktuellen Punkt und den Punkten davor

Zusammenhang Korrelation (Pearson im Qudrat = Bestimmtheitsmaß, nur bei linearer Korrelation, sonst Spearman)

Autokorrelation ist der Zusammenhang einer Variable mit seiner Lag-Variable.
Trendentwicklung $\hat{=}$ Hohe Autokorrelation
Bestimmung: Tatsächliche Werte werden gelaggt, Korrelationen der tatsächlichen Variable mit ihren Lag-Variablen, Oft mit den ersten 2 Lag-Variablen, Plot in einem Autocorrelation Function (ACF)-Plot

ACF-Plot (x-Achse "Generationen" der Lag-Variable, y-Achse Wert der Autokorrelation - zentriert auf 0 -> Mitte ist 0, weil negative Autokorrelation oft vorhanden)
(Berechnungsformel)
Zusammenhang Autokorrelation - Trend - Steigung

AR(1): $$\hat{Y}_{t+1} = \beta_0 + \beta_1 \cdot y_t + \epsilon_t$$$\beta_0$: Konstante (Intercept)
$\beta_1$: Lag "Generation" 1
$y_t$: Vorheriger Wert (Auto Regressive Komponente)

zu $\beta_0$: Er stellt den Teil des Erwartungswertes dar, der nicht durch die unmittelbare Vergangenheit erklärt wird

Partielle Autokorrelation
Wird verwendet, wenn man mehrere Lag "Generationen" verwenden möchte, weil diese Effekte darstellen, die für die Prognose wichtig sind.
Die partielle Autokorrelation sagt mir, welche Lag-Variablen für mich wirklich zusätzliche Informationen gibt. Er zeigt, wie stark die Autokorrelation ist, unter Ausschluß der Effekte davor.
Dafür macht man ein Partial Autocorrelation Function (PACF)-Plot.

AR(2): $$\hat{Y}_{t+1} = \beta_0 + \beta_1 \cdot y_t + \beta_2 \cdot y_{t-1}+ \epsilon_t$$
$\beta_2$:  Lag "Generation" 2
$y_{t-1}$: Vorvorheriger Wert

#### Analyes der Zeitreihe
Bedingungen: 
Ist die Zeitreihe stationär?
-> konstanter Mittelwert & konstante Varianz
Ja -> keine Anpassung
Nein -> Anpassung an Stationarität durch Differenzierung (I - Integrated), Anzahl der Differenzierungen: d

Liegt eine Autokorrelation vor, sodass eine Lag-Variable einbezogen werden muss?
-> Durbin-Watson Test oder ACF-Plot
Ja -> PACF-Plot -> AR Komponenten werden eingebaut
Nein -> Keine AR Komponente

Liegt eine MA-Komponente vor?
-> nur eine oder wenige signifikante Autokorrelationen im ACF-Plot, im PACF-Plot mehrere signifikante, partielle Autokorrelationen leigen vor und diese nehmen ab und schwanken zwischen negativ & positiv
Ja -> MA-Komponente hinzufügen
Nein -> Keine MA-Komponente

ACF-Plot beantwortet die Frage ob Auto Regressive Modelle sinnvoll sind und das PACF-Plot beantwortet, wie viele AR Komponenten eingebaut werden müssen.

Box-Ljung Test -> Gibt die Signifikanz eine Lag-Variable an (Ziel Sig.  < 0,05)
Differenzierungskomponente
AR(1,1,0) Modell -> 1 AR Komponente & 1 Differenzierungskomponente

MA-Komponente
-> Kurzfristiges Gedächtnis des ARIMA Modells
Schätzt den Wert in der Zukunft mit der Hilfe des Schätzfehlers vorheriger Werte.

$$\hat{Y}_{t+1} = \beta_0 + \beta_1 \cdot y_t + \alpha \cdot\epsilon_t$$
$\alpha$: Gewichtungsfaktor
$\epsilon_t$: Error Term = $y_t - \hat{y}_t$
MA-Komponente ist stark, wenn wir Zeitreiehen haben, die um einen Wert fluktuieren.
Wie finden wir heraus, ob wir eine MA-Komponente brauchen?
Signale im ACf & PACF-Plot: nur eine oder wenige signifikante Autokorrelationen im ACF-Plot, im PACF-Plot mehrere signifikante, partielle Autokorrelationen leigen vor und diese nehmen ab und schwanken zwischen negativ & positiv

Saisonale Komponente (SARIMA)
-> Seasonal ARIMA Modell

**ARIMA (p, d, q) (P, D, Q)\_m**
- **p**: nicht-saisonale AR-Reihenfolge  
- **d**: nicht-saisonale Differenzierung  
- **q**: nicht-saisonale MA-Reihenfolge  
- **P**: saisonale AR-Reihenfolge  
- **D**: saisonale Differenzierung  
- **Q**: saisonale MA-Reihenfolge  
- **m**: Zeitspanne des sich wiederholenden saisonalen Musters

$$
\hat{y}_t = \beta_0 + \beta_1 y_{t-1} + \beta_2 \Phi_{t-1} + \varepsilon_t
$$

- $\Phi$: Moving-Average-Komponente  
- $y_{t-1}$: Autoregressive Komponente  

Wird eine saisonale Komponente ergänzt, ergibt sich ein **$SARIMA (1,1,1)(1,1,1)_{12}$**-Modell.
12 -> Anzahl der Saisons.

SARIMAX -> + Kausalvariablen


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
