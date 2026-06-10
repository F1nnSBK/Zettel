
KLAUSUR

Für eine Regression ohne Beschränkungen mit NNs oft die Identity Function als Activation
Beispiel bei Klassifikation Aufgabe 12, wenn p nicht gegeben oft 0,5 annehmen (beide Klassen gleich wichtig) oder zb bei Spam/Ham ist es vll gegeben oder man möchte sicher gehen, keinen Ham zu. verpassen dann würde mein ein p von0,9 nehmen (beispiel)

Aufgabe 7 SVM Model 
supportvektoren aus alpha sind nur 1 und 4 mit 0.2 und 0.8
kernel funktion und den 2 supportvecs
vorhersageformel (allgemeine Formel) mit werten der kernel funktion
-> Vorhersagewerte
Stellen in alpha mit 0 sind irrelevant

Alles was nicht in Train war, kommt zu Val bei Bootstrap -> Keine Dopplungen in Val

Bootstrapping für luna?

Einfach über den Mittelwert Resampling 8
Bagging wie entscheiden wir? Häufigkeiten oder Mittelwert
KLAUSUR ENDE













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



