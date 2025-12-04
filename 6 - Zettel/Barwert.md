#Note

2025-12-04

Tags: [[Dynamische Investitionsrechenverfahren]], [[Grundlagen Finanzierung & Investition]]

---
Der Barwert ($BW_0$) ist der heutige Wert eines zukünftigen Zahlungszuflusses $CF_n$, der über $n$ Jahre mit dem Zinssatz $i$ diskontiert wird.

$$BW_0 = \frac{CF_n}{(1+i)^n} = CF_n \cdot (1+i)^{-n}$$

- $CF_n$: Zahlung im Zeitpunkt $n$ (Zukunft).
- $(1+i)^{-n}$: Abzinsungs- bzw. Diskontierungsfaktor.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Barwert]]
SORT file.mtime DESC
```