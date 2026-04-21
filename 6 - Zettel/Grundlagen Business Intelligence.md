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
