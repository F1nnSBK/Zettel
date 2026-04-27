#Note

2026-04-21

Tags: [[Business Analytics]], [[6 - Zettel/Business Intelligence]], [[Zeitreihen]], [[Zeitreihenanalyse]], [[Zeitreihenkomponenten]]
#bi

---
Die Modelle in der Zeitreihenanalyse lassen sich von der Regressionsanalyse ableiten. In der Regressionsanalyse kennen wir folgende Modelle:
**Deterministische Modelle**: (Geht immer auf, ohne Fehler)
$Y = f(x)$
$y = b_0 + b_1 * X$

In diesem Beispiel entspricht $b_0$ der Basiskomponente (y-Achsenabschnitt), $b_1$ der Trendkomponente (Steigung) und $X$ ist unsere abhängige Variable.

Jetzt erweitern wir diese Modell um einen Error-Term $e$, da wir es nie schaffen werden, eine Zeitreihe perfekt zu modellieren. Oft wollen wir das auch garnicht.
**Stochastische Modelle**: (Fehler möglichst niedrig halten)
$Y = f(x) + e$
$y = b_0 + b_1 * X + e$
-> Minimierung von e

Bei der Zeitreihenanalyse bauen wir darauf auf. Ein Modell ist eine mathematische Funktion, in der ein Prognosewert $\hat{Y}$ durch 1) die Zeitreihenkomponenten und durch 2) deren Verknüpfung geschätzt wird. Außerdem unterscheiden wir additive Modelle und multiplikative Modelle.
+ Im additiven Modell geht man davon aus, dass Trend und Saisonale Komponente konstant bleiben. Ebenso wäre die Störgröße [[Normalverteilung|normalverteilt]], d.h. im Zeitablauf konstant.
  (z.B. Freibadbesuche über 10 Jahre)
+ Im multiplikativen Modell wird davon ausgegangen, dass im Zeitablauf Trend und saisonale Komponente größer werden. In diesem Fall würde auch die Störgröße steigen.
  (z.B. Nutzung von KI-Chatbots wird immer intensiver)

Additives Modell (linear): $\hat{Y} = \alpha + \beta + \gamma$
Mulitplikatives Modell (expo.): $\hat{Y} = \alpha * \beta * \gamma$
Dabei sind $\alpha$ die Basiskomponente, $\beta$ die Trendkomponente und $\gamma$ die Saisonkomponente.

Ziel ist die Entwicklung eines Modells zur Schätzung des Prognosewerts $\hat{Y}$ mit minimalen Error Term.

Ein Modell ohne Saisonkomponente ist am Ende eine einfache [[Lineare Regression]]. Die Saisonkomponente wird über [[Dummy-Variablen]] in das Modell eingefügt. Diese sind binär und nehmen die Werte 0 oder 1 an. Sie schalten die Saisonkoeffizienten aus oder an. Man kann sie als [[Designmatrix]] umschreiben.
#### Schätzperiode & Validierungsperiode
Die Schätzperiode entspricht dem Zeitraum, der für die Schätzung des Modells verwendet wird. Dieser sollte mehrere Perioden umfassen, um möglichst viele Beobachtungen für z.B. Saisonalitäten abzudecken.

Die Validierungsperiode ist die letzte Periode der Zeitreihe, für die noch Daten verfügbar sind und die einen kompletten Zyklus abdeckt. Anhand der Daten in diesem Zeitraum wird die Prognosegüte der verschiedenen Modelle gemessen und verglichen.

Dieses System ist vergleichbar mit dem Trainings- und Testdatensätzen im [[Supervised Learning]], sie sind aber nicht gleich.


---
#### Flashcards

Warum ist das additive Modell für Saisonalitäten bei Industrie-Ersatzteilen gefährlich?::Weil der Trend den saisonalen Impact oft nicht nur verschiebt, sondern verstärkt.

Wann ist die Verwendung eines multiplikativen Modells sinnvoll?::Wenn Trend und saisonale Komponente mit dem Zeitverlauf größer werden (z.B. expo. Wachstum). Die Störgröße wächste dann auch proportional mit.

Nenne ein Beispiel für die Anwendung eines additiven Modells und eins für die Anwendung des multiplikative Modells::Das additive Modell ist z.B. bei der Anzahl von Motorradfahreren bei einer schönen Strecke sinnvoll, während ein multiplikative Modell oft ein Wachstum impliziert, z.B. die Anzahl der Einwohner in den USA ab der Kolonialisierung.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Modellformulierung]]
SORT file.mtime DESC
```