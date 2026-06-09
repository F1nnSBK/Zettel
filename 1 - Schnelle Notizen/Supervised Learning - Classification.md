
Nun kommen label wie spam/ham oder ok/wartungsbedarf/kaputt.
Credit Card Default Beispiel
Achtung bei unbalanced Datasets (Interpretation)
Verbindung Zipf Verteilung -> Was bringt uns das hier?

Binäre, Lineare Klassifikation
-> Aufteilung in 2 Hälften durch Hyperebene

Können wir lineare Regression dafür verwenden?
Umcodieren (Dummies) -> Credit card default (0) credit default (1) als Beispiel
$$
\hat{c}(x) = 
$$
Logistische Regression

Modellierung der Wahrscheinlichkeit
$$p(x)=\frac{s}{1 + s} \text{ mit } s=e^{a} \text{ und } a=\beta_{0}+ \beta_1X_{1}+\dots+\beta_nX_n$$
Logit-Transformation (oder Log-Odds Transformation)
Welche Werte liefern genau den Schwellenwert für die Entscheidung?

-> erzeugt auch eine Hyperebene linear im Featureraum

Störfaktoren Confluence

Cas-Control Samples
Wie viele Controls -> ungefähr das Fünffache
Cases sind oft der limitierende Faktor
-> Problem für die logistische Regression
Korrektur der y-Achsenabschnitts
{Korrekturformel}

Log Regression mit $K > 2$ Klassen
Nichtlinearität in Log Reg
Rein für die Trennung sind unendliche viele Lösungen für die parameter Beta nicht problematisch, da sie nur die Länge der Normalenvektors verändern. Problematisch wird das erst bei der Berechnung von Wahrscheinlichkeiten
Koeffizienten müssen gegen unendlich laufen lassen $\to +\infty$ 
Regularisierte Log Regression oder andere Methode Hard-/Soft-Margin Classifier -> SVM
$L_2-Regularisierung$ (Ridge) oder $L_1-Regularisierung$ (Lasso)

Diskriminanzanalyse
Klassen einzeln anschauen und vergleichen
LDA > 2 Klassen gut geeignet
Boundaries of LDA als 2D Konfidenzintervalle -> Beziehung Mahalanobis Distanz?
Arten der Diskriminananalyse
LDA (Normalverteilung mit gleicher Kovarianz in jeder Klasse) -> Ellipsen müssen gleich geformt sein, Quadratische Diskriminanzanalyse (Normalverteilung mit unterschiedlicher Kovarianz in jeder Klasse), Naive Bayes (Die Dichtefunktion ist das Produkt der individuellen Dichten)

Unausgewogene Daten Maße
F1-Score, Zäfferer findet Balanced Error (Balanced Accuracy) besser Mittelwert des Fehlers pro Klasse, über alle Klassen



