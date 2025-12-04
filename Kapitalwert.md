#Note

2025-12-04

Tags: [[Dynamische Investitionsrechenverfahren]], [[Grundlagen Finanzierung & Investition]], [[Kapital]], [[Kapitalwertmethode]]

---
Der Kapitalwert $KW_0$ (Net Present Value $\hat{=}$ NPV) eines [[Investitionsobjekt|Investitionsprojekts]] ist der [[Barwert]] sämtlicher Ein- und Auszahlungen einer Investition.

$$
KW_0=\frac{CF_0}{(1+i)^0}+\frac{CF_1}{(1+i)^1}+\dots+\frac{CF_n}{(1+i)^n}
$$
$$
KW_0 = \sum_{t = 0}^{n} \frac{CF_t}{(1+i)^t}
$$

$CF_t$: Cash Flow im Zeitpunkt $t$ (Einzahlungsüberschüsse)
$i$: Kalkulationszinssatz

Bei [[Investition|Investitionen]] gibt es im Regelfall einen hohen [[Cash Flow|Investitions-Cash Flow]] $I_0$ am Beginn der Investition und eine hohe Restwertzahlung $R_n$ bei Verkauf/Liquidation der Investition.

$$
KW_0 = -I_0 + \sum_{t = 1}^{n} \frac{CF_t}{(1+i)^t} + \frac{R_n}{(1+i)^n}
$$
 $I_0$: Anschaffungsauszahlung (in $t=0$)
$R_n$: Restwert am Ende der Laufzeit


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Kapitalwert]]
SORT file.mtime DESC
```