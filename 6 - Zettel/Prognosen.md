#Note

2026-04-21

Tags: [[6 - Zettel/Business Intelligence]], [[Business Analytics]], [[Deskriptive Statistik]], [[Modellformulierung]], [[Mittelwert]]
#bi

---
Ziel der Zeitreihenanalyse ist die Erstellung von Prognosen -> Aussagen über den weiteren Verlauf.

1. Wahl der Schätz- und Validierungsperiode
   Für die Validierungsperiode nimmt man einen kleinen Teil am aktuellen Ende der Zeitreihe (z.B. 1 Jahr). Der Rest de Zeitreihe dient als Schätzperiode (z.B. 9 Jahre)
   -> [[Backtesting]] ist der Vergleich der prognostizierten Werte mit den realisierten Werte.
	Man muss darauf achten, dass die Validierungsperiode aussagekräftig ist.
2. Vergleich der prognostizierten Werte mit den realisierten Werten
   Über die Prognosefehler kann man das beste Modell bestimmen.
   + Mean Absolute Deviation MAD $$MAD = \frac{1}{K}\sum_{k=1}^{K}|e_{T + k}|$$
   + Mean Absolute Percentage Error MAPE $$MAPE = \frac{1}{K}\sum_{k=1}^{K}|\frac{e_{T + k}}{Y_{T+k}}|$$
Oft wird das [[Bestimmtheitsmaß]] $R^{2}$ (Wie viel Streeung erklärt mein Modell) dazugenommen.


---
#### Flashcards

Gib ein Beispiel für eine schlechte Validierungsperiode::Schätzperiode sind 5 Jahre vor der Coronakrise und die Validierungsperiode ist nur 1 Jahr mitten in der Coronakrise

Was sind 3 wichtige Fehlermaße für Prognosen?::MAD, MAPE und Bestimmtheitsmaß $R^{2}$.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Prognosen]]
SORT file.mtime DESC
```