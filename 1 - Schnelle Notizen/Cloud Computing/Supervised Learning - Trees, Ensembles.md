
Entscheidungsbäume - Aufteilung des Raums in Hyperrechtecke (Segmentierung)
(Für Regression)
Aufteilungen der verschiedenen Features in Hyperräume (Rechtecke oder Regionen, meint hier das selbe)
Prozess der Baumbildung - Nach RSS Minimierung (Nacheinander Schrittweise, gleichzeitig ist zu rechenaufwendig)
-> Greedy Search (Recursive Binary Splitting) top-down
In den Aufteilungen können keine Überlappungen sein und im 3D Plot muss der RSS Wert über die gesamte Region konstant sein

Ich will nicht mehr als ne Baumtiefe von 5 oder wenn nur noch 5 Datenpunkte übrig bleiben will ich nicht mehr teilen

Pruning - Baum maximal groß machen und dann Äste wegschneiden ohne viel RSS zu verlieren. So viel wie nötig, so wenig wie möglich

Entscheidungsbäume für Klassifikation (Änderungen häufigste Klasse, Fehlerrate/GINI-Index)
Fehlerrate nicht sensitiv genug gegen Änderungen weil wird berechnet durch 1 minus Häufigkeit der häufigsten Klasse
Gini index daher besser (normalisiert die häufigste Klasse auf alle anderen - so etwas wie Reinheit)
Alternative zu $G$ ist Cross Entropy - Liefern oft sehr ähnliche Ergebnisse
Bäume vs. lineare Modelle

Ensemble Modelle
Bagging
Allgemein anwendbares Verfahren zur Verringerung der Varianz
Kommt aus der Statistik: Wenn man Mittelwerte über die beobachtete Gruppen bildet, wird die Varianz verringert
Wenn wir viele Modelle haben, die auswerten und Mitteln senken wir die Varianz (Motivation)
Wir machen Bootstrapping, da wir so auf jeden Bootstrap Datensatz ein neues Modell trainieren können, würden wir das nicht machen, hätten wir immer das gleiche Ergebnis und der Effekt wäre weg
Bagging-Function:
$$\hat{f}_{bag}(x)=\frac{1}{B}\sum^{B}_{i=1}\hat{f}^{i*}(x)$$
Mehrheitsabstimmung oder Häufigkeitsverteilung (wenn es sie gibt)
Out-of-Bag Schätzung Nur ein Teil der Bäume wird zur Vorhersage verwendet, nicht alle
Einzelne Bäume im Bag dürfen nicht zu ähnlich sein

- Random Forest
Trick bei RandomForest (Ein Bag of Trees mit zufälliger Auswahl an $m$ Features bei der ersten Entcsheidung und bei allen anderen). D.h. für jeden Baum habe ich $m$ zufällig gewählte Features, so muss jeder Baum eine andere Entscheidung treffen. Daumenregel ist $m \approx floor(\sqrt{p})$
RF liefert Feature Importance - Explainability
$B$ liegt oft im Bereich von 100en oder 1000en Bäumen


Boosting
Weiteres Ensembles Modell, Entscheidungsbäume können hier genommen werden aber auch andere z.B. lineare Regression
Unterschiede zu Bagging - Erzeugung läuft sequentiell und nicht unabhängig - sie werden abhängig nacheinander gebaut.
Boosting Algorithmus für Regressionsbäume S. 49
1. Initialisierung
2. Für b .. wiederhole
	1. Trainiere Baum ...
	2. Aktualisiere ...
	3. Aktualisieren der Residuen
3. Ausgabe des finalen Modells

Overfittet gerne aber um das Risiko zu senken haben wir das Lambda als Regularisierung dabei (Learning Rate)
Das war für Regression, es geht auch für Klassifikation ist aber dort komplizierter, findet man aber im Buch Elements of Statistical Learning in Kapitel 10
Vorsicht bei den Parametern bei `XGBoost` die treffen seltsame Entscheidungen bei den Standardparametern für $\lambda \text{ oder }\eta=0,3$ was gerne mal viel zu hoch ist
Definitiv Tuning notwendig zb via `Optuna` mit ihrem Tree-Structured-Parzen-Estimator (Bayesian Optimization)


Stacking