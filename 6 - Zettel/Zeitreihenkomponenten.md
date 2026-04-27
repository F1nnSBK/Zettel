#Note

2026-04-21

Tags: [[Business Analytics]], [[6 - Zettel/Business Intelligence]], [[Zeitreihen]], [[ARIMA]], [[Smoothing]]
#bi

---
Eine [[Zeitreihen|Zeitreihe]] enthält versteckte Informationen. Man kann sie in 3 verschiedene Komponenten einteilen. Es verhält sich etwa wie ein Signal (Zeitreihe) das man mit einer [[Fast-Fourier-Transformation]] in die einzelnen Bestandteile zerlegt.

1. [[Basiskomponente]] -> Sie ist der y-Achsenabschnitt
   -> quasi der "Ursprung" einer Zeitreihe
2. [[Trendkomponente]] -> Das ist die Steigung
   -> sie gibt die Richtung der Zeitreihe an (steigt/fällt)
3. [[Saisonkomponente]] -> Sie enthält Informationen über wiederkehrende Muster
   -> sie enthält eine Amplitude und Frequenz (z.B. Jahreszeiten)




---
#### Flashcards

Was sind die 3 Zeitreihenkomponenten?::Basiskomponente, Trendkomponente und Saisonkomponente

Nenne ein Beispiel für die Saisonkomponente::Die Jahreszeiten beeinflussen die Besucher von Hallenbädern.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Zeitreihenkomponenten]]
SORT file.mtime DESC
```