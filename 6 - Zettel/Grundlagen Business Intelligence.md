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

**Deterministische Modelle**: (Geht immer auf ohne Fehler)
$Y = f(x)$
$y = b_0 + b_1 * X$

**Stochastische Modelle**: (Fehler möglicht niedrig halten)
$Y = f(x) + e$
$y = b_0 + b_1 * X + e$
-> Minimierung von e

Basismodelle:
Additives Modell (linear): $\hat{Y} = \alpha + \beta + \gamma$
Mulitplikatives Modell (expo.): $\hat{Y} = \alpha * \beta * \gamma$

Modell ohne Saisonkomponente:
$\hat{Y}_t = \alpha + \beta_1 * t$




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
