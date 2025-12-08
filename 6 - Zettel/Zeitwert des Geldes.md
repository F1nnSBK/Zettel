#Note

2025-12-04

Tags: [[Dynamische Investitionsrechenverfahren]], [[Grundlagen Finanzierung & Investition]], [[Barwert]], [[Endwert]]
#finance

---
Grundregel: Ein Euro heute ist wertvoller als ein Euro morgen.
Warum? Weil Geld heute investiert werden kann und Zinsen ($i$) erwirtschaftet. Um Zahlungen vergleichbar zu machen, müssen sie auf denselben Zeitpunkt verschoben werden.

- **Verschieben in die Zukunft (t0 $\to$ tn):** Aufzinsung (Compounding).
    
- **Verschieben in die Vergangenheit (tn $\to$ t0):** Abzinsung (Discounting).


#### 1. Endwert (Future Value)
Der [[Endwert]] ist der Wert einer heutigen Zahlung $CF_0$, die für $n$ Jahre zum Zinssatz $i$ angelegt wird.
$$EW_n = CF_0 \cdot (1+i)^n$$
- $CF_0$: Zahlung im Zeitpunkt 0 (heute).
- $(1+i)^n$: **Aufzinsungsfaktor**.


#### 2. Barwert (Present Value)

Der [[Barwert]] ($BW_0$) ist der heutige Wert eines zukünftigen Zahlungszuflusses $CF_n$, der über $n$ Jahre mit dem Zinssatz $i$ diskontiert wird.
$$BW_0 = \frac{CF_n}{(1+i)^n} = CF_n \cdot (1+i)^{-n}$$
- $CF_n$: Zahlung im Zeitpunkt $n$ (Zukunft).
- $(1+i)^{-n}$: Abzinsungs- bzw. Diskontierungsfaktor.


Warum sind 100€ heute nicht gleich viel wert wie 100€ in einem Jahr? :: Weil heutiges Geld angelegt werden kann und Zinsen erwirtschaftet (Zeitwert des Geldes).
<!--SR:!2025-12-12,4,270-->

Wie nennt man den Vorgang, eine Zahlung in die Zukunft zu verschieben? :: Aufzinsung.
<!--SR:!2025-12-12,4,272-->

Wie nennt man den Vorgang, eine Zahlung in die Vergangenheit (auf heute) zu verschieben? :: Abzinsung (Diskontierung).
<!--SR:!2025-12-09,1,232-->

Wie lautet die Formel für den Endwert einer Einmalzahlung?
?
$$EW_n = CF_0 \cdot (1+i)^n$$
<!--SR:!2025-12-12,4,272-->

Wie lautet die Formel für den Barwert einer zukünftigen Zahlung?
?
$$BW_0 = \frac{CF_n}{(1+i)^n}$$
<!--SR:!2025-12-12,4,270-->

Was ist der Unterschied zwischen Aufzinsungs- und Abzinsungsfaktor?
?
- Aufzinsungsfaktor: $(1+i)^n$ (Wächst mit der Zeit).
- Abzinsungsfaktor: $(1+i)^{-n}$ (Schrumpft mit der Zeit).
<!--SR:!2025-12-11,3,252-->

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Zeitwert des Geldes]]
SORT file.mtime DESC
```