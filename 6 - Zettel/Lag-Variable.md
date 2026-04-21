#Note

2026-04-21

Tags: [[Business Intelligence]], [[Business Analytics]], [[Zeitreihen]], [[Prognosen]]
#bi

---
Eine **Lag-Variable** ist eine um eine oder mehrere Periode verzögerte Variable, die genutzt wird, wenn sich der Einfluss der unabhängigen Variable auf die abhängige Variable nur mit Verzögerung niederschlägt.

Beispiel:
Ein Bauunternehmen will den Einfluss der Anzahl der Bauanträge in einer Gemeinde auf die Anzahl der Aufträge pro Quartal bestimmen. In diesem Fall müssen die Anträge erst bearbeitet werden, sie wirken sich also erst mit Verzögerung – z.B. einen Monat später - auf den Auftragseingang aus

Im Modell:
$$Auftragseingang_{t-1}=\alpha + \beta_1 \cdot Bauanträge_{t-1}$$


---
#### Flashcards

Wann benutz ich eine Lag-Variable?::Wenn eine unabhängige Variable zeitlich verzögert auf eine abhängige Variable einwirkt.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Lag-Variable]]
SORT file.mtime DESC
```