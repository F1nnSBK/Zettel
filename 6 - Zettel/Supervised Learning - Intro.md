#Note

2026-04-16

Tags: [[Lineare Algebra]], [[Lineare Regression]], [[Mathematik]], [[Vektoren]]
#sl

---

Supervised vs Unsupervised Learning

+ Motivation, Terminologie und Grundlagen
+ Lineare Regression
+ Klassifikation
+ Support Vector Machines
+ Re-Sampling / Validation
+ Entscheidungsbäume / Ensembles
+ Einführung in Neuronale Netze


#### Motivation, Terminologie und Grundlagen
Viele Anwendungsbereiche (bis S. 17)

Statistical Learning vs Machine Learning
-> Synonym, Lernen aus Daten

Statistik
Daten $X \rightarrow$ Ausgabe $Y$ z.B. LinReg
Abgrenzung zu Machine Learning? -> ML mehr für komplexere Probleme
Sonst sehr überlappend

Supervised Learning
Label $Y$ (Abhängige Variable, Output, Antwort, Zielvariable)
Features $X$, in der Regel mehrere, Anzahl: $p$ (auch: Prädiktoren, Inputs, Merkmal, Kovariate, unabhängige Variablen)
	Regression: $Y$ quantitativ
	Klassifikation: $Y$ ist qualitativ und hat eine endliche Anzahl von Werten (z.B. überlebt/verstorben)
	Normalerweise mit Trainingsdaten für $X$ und $Y$: $(x_1, y_1), \dots ,(x_N,y_N)$. (Auch Datenproben, Datenpunkte, Beobachtungen oder Stichproben)
Ziele -> Genaue Vorhersage von $Y$ für neue Testdaten $X^*$, Verstehen wie $Y$ mit $X$ zusammenhängt, Bestimmen der Unsicherheit von Vorhersagen
-> Dagegen Unsupervised Learning S.22 Autoencoder Label = Features = Label

Pre-Processing
Datenerfassung, -speicherung, -übertragung, -aufbereitung
Post-Processing
Übertragung der Ergebnisse, Speicherung, Interpretation & Visualisierung

Insgesamt kann der Prozess in Prozessmodellen modelliert werden CRISP-DM oder DASC-PM. Hilft manchmal um sich nicht zu verlieren (Eig gesunder Menschenverstand).









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