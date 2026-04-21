#Note

2026-04-16

Tags: [[Supervised Learning]], [[Lineare Algebra]], [[Lineare Regression]]
#sl

---
### Statistical Learning

Notation bei der Regression, Label, Features, Feature-Vektor, Zusammenhang von $X$ und $Y$
$$Y = f(X) + \epsilon$$
$\epsilon$ = Fehler -> ref. zu stochastisches Modell

Gibt es ein ideales $f(X)$ S.7
Ideale Regression als Gedankenbeispiel -> unmöglich (nicht stetig wegen fehlender Daten)

Geschätzte Regression
Fehler
Schätzung: $\hat{f}(X)$
Nicht berechenbar: $\epsilon = Y - f(X)$ (Wegen nicht möglicher idealer Funktion $f(X)$)
Wie macht man es also? 
Vorhersagefehler des Schätzwertes $\hat{f}(X)$: Differenz $\hat{f}(X) - f(X)$, plus nicht-reduzierbaren Fehler $\epsilon$
Konkrete Denkweise: Das x-Achse auf $\mathbb{R}$ gibt es oft garkeine Punkte **exakt** auf 4,0 sondern z.B. auf 4,012 oder 4,0532. Deshalb schauen wir uns ein Intervall an: $[3,9;4,1]$

Keine Intervalle, sonder einfach $n$ nächste Punkte an unserem wert.
k-Nearest Neighbours -> Median oder Mittelwert? (Ausreißer!)

Neighborhood Averaging
+ Wenige Features ($p$ < 10)
+ Viele Beobachtungen ($N$ groß, Größenordnung: Hunderte)
-> curse of dimensionality S.15 10% Neighborhood (Wird schwer, wenn $p$ (Anzahl der Features) groß ist)
Verbindung zu Matryoshka Representation Learning

Modellbewertung & Trade-Offs
Vorhersagegenauigkeit vs. Interpretierbarkeit
Overfit vs. Underfit

Ermittlung der Modellgenauigkeit
Mean Squared Error
$$MSE = \frac{1}{n} \sum_{i=1}^{n}(y_i - \hat{f}(x_i))^2$$
-> Kann Overfit nicht erkennen, weil wir bei den Stellen, an denen das Modell keinen Fehler macht einfach $0^2$ gerechnet wird. Daraus erfahren wir aber nichts.
-> Funktioniert also nur auf ungesehenen Daten (Test-Daten), auf den Trainingsdaten kann der MSE nur Hinweise für Overfit/Underfit geben.
Plot S.24 $MSE_{test}$ & $MSE_{train}$ Verlauf -> Was ist Flexibility?

Bias - Variance Trade Off S.27
$$Error(x^*, y^*) = \text{Variance of }\hat{f}(x^*) + \text{Bias of }\hat{f}(x^*) + \epsilon$$
Variance: Fehler der Modellvorhersagen
	Aufgrund kleiner Änderungen in den Trainingsdaten
Bias: Fehler der Modellvorhersagen
	Aufgrund der Modellstruktur
$\epsilon$: Nicht-reduzierbarer Fehler
	Fehler in den Daten selbst, kann nicht durch das Modell "behoben" werden
Bei hoher Komplexität $\uparrow$ wird die  Variance $\uparrow$  aber der Bias $\downarrow$  -> S.30/31 $\epsilon$ = konstant

Wie erkennt man Overfit?

#### Idealer Klassifikator
Klassenwahrscheinlichkeiten für gegebenes $x$
Bayes optimal classifier $c(x)$

















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