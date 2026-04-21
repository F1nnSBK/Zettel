#Note

2026-04-21
Tags: [[Mathematik]], [[Statistik]], [[Deskriptive Statistik]]
#bi

---
Das Bestimmtheitsmaß $R^{2}$ sagt aus, wie viel Variation in den Daten durch ein [[Regressionsmodell]] erklärt werden kann.

Ist das Verhältnis aus erklärter Streeung (SSE) und Gesamtstreuung (SST)
Die erklärte Streuung ist die Summe der quadrierten Differenzen zwischen geschätztem Wert $\hat{y}$ und Mittelwert $y$ für alle Beobachtungen.
Die nicht erklärte Streuung (SSR) ist die Summe der quadrierten Diffenrenzen zwischen geschätztem Wert $\hat{y}$ und beobachtetem Wert $y$ für alle Beobachtungen.
$$
SST = SSE + SSR$$

$R^{2}=\frac{SSE}{SST}$


---
#### Flashcards

Wie berechnet man $R^{2}$?
?
$$SSE = \sum^{m}_{i=1}(y_i - \hat{y}_i)^2$$
$$SSR = \sum^{m}_{i=1}(y_i - \bar{y})^2$$
$$SST = SSE + SSR$$
$$R^{2}=1-\frac{SSE}{SST}$$

Was ist ein Problem mit dem Bestimmtheitsmaß?::$R^2$ steigt auch, wenn einfach nur mehr Datenpunkte hinzugefügt werden. Deshalb hat man Adjusted $R^2$ eingeführt. 


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Bestimmtheitsmaß]]
SORT file.mtime DESC
```