#Note

2026-04-21

Tags: [[Business Analytics]], [[Business Intelligence]], [[Zeitreihenkomponenten]], [[Prediktive Modellierung]], [[Forecasting]], [[Modellgüte]]
#bi

---
Eine **Zeitreihe** ist eine Folge von zeitlich abhängigen Datenpunkten. Typische Beispiele sind Aktienkurse von der Börse oder Sensordaten. Die [[Zeitreihenanalyse]] beschäftig sich mit der Analyse & Vorhersage der künfitgen Entwicklung einer Zeitreihe. Man kann sie als spezielle Form der [[Regressionsanalyse]] betrachten.

Eine typische Fragestellung ist: Können die Passagierzahlen einer Airline für den nächsten Monat vorhergesagt werden?

Für die Analyse einer Zeitreihe sollte man sich folgende Fragen stelle:
+ Welches Modell eignet sich am besten in diesem Use Case?
+ Wie gut sind die verwendeten Modelle?
+ Sind meine Modelle besser als naive Modelle?



---
#### Flashcards

Was ist eine Zeitreihe?::Eine Zeitreihe ist eine Folge von zeitlich abhängigen Datenpunkten.

Nenne 3 Beispiele für Zeitreihen?::Aktienkurs, Daten eines Abstandssensors, Lagerbestand über 1 Jahr

Welche Fragen sollte man sich bei der Modellauswahl für eine Zeitreihe stellen?
?
+ Welches Modell eignet sich für meinen Use Case?
+ Wie gut sind meine verwendeten Modelle?
+ Schlagen meine Modelle naive Methoden?

Wie findet man das beste Modell für eine Zeitreihenanalyse?::Man macht ein "Horse race"

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Zeitreihen]]
SORT file.mtime DESC
```