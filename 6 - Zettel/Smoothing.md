#Note

2026-04-21

Tags: [[Business Intelligence]], [[Business Analytics]], [[Glättung]], [[Holt-Winter]]
#bi

---
Fragestellungen:
Welches Modell eignet sich zur Schätzung der Zeitreihen?
Wie gut sind die verwendeten Modelle?
Sind die Modelle besser als naive Modelle?

Gütemaße:
   + Mean Absolute Deviation MAD $$MAD = \frac{1}{K}\sum_{k=1}^{K}|e_{T + k}|$$
   + Mean Absolute Percentage Error MAPE $$MAPE = \frac{1}{K}\sum_{k=1}^{K}|\frac{e_{T + k}}{Y_{T+k}}|$$
+ Mean Squared Error MSE $$MSE = \frac{1}{N}\sum_{i=1}^{N}(y_i - \hat{y}_i)^2$$
+ Root Mean Squared Error MSE $$RMSE = \sqrt{\frac{1}{N}\sum_{i=1}^{N}(y_i - \hat{y}_i)^2}$$
  Der RMSE ist im Vergleich zum MSE besser, wenn 






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