#Note

2025-12-08

Tags: [[Grundlagen Finanzierung & Investition]], [[Dynamische Investitionsrechenverfahren]], [[Interne Zinsfußmethode]]
#finance

---
Der **Interne Zinsfuß** (IZF / IRR) ist derjenige Diskontierungszinssatz $i$, bei dem der **Kapitalwert ($KW_0$) einer Investition exakt gleich Null ist**.

- **Interpretation:** Er stellt die tatsächliche jährliche Verzinsung des gebundenen Kapitals über die Laufzeit dar.
- **Ziel:** Ermittlung der Rendite in Prozent (Return on Investment).
#### Berechnung

Man setzt die Kapitalwertformel gleich 0 und löst nach $i$ auf.

$$0 = -I_{0} + \sum_{t=1}^{n} \frac{CF_{t}}{(1+i)^{t}} + \frac{R_{n}}{(1+i)^{n}}$$

- $I_0$: Investitionsausgabe (in $t=0$)
- $R_n$: Restwert / Liquidationserlös (in $t=n$)2.

_(Hinweis: Analytisch nur schwer lösbar bei $t > 2$. In der Klausur oft via Interpolation oder vorgegebenen Szenarien)._
$I_{IZF}$ ohne Restwert:
$$

0 = -C_0 + \sum_{t=1}^{n} \frac{CF_t}{(1+i)^t}

$$

$$

 \rightarrow i_{IZF}=\sqrt{\frac{CF_t}{C_0}}-1

$$
#### Entscheidungskriterium

Vergleich des $IZF$ mit dem vom Unternehmen geforderten Mindestzinssatz (Hurdle Rate / Kapitalkosten $i_{kalk}$).

| **Situation**                         | **Regel**            | **Logik**                                                                      |
| ------------------------------------- | -------------------- | ------------------------------------------------------------------------------ |
| **Investition vs. Nicht-Investition** | **$IZF > i_{kalk}$** | Die Investition rentiert sich besser als die Kapitalkosten. **Wertschaffung.** |
| **Auswahlproblem (A vs. B)**          | **Max($IZF$)**       | Wähle das Projekt mit der höheren Rendite.                                     |

#### Die Falle

Bei Konflikten zwischen Kapitalwertmethode (NPV) und IZF-Methode (z.B. Projekt A hat höheren NPV, Projekt B hat höheren IZF):

$\rightarrow$ Immer die Kapitalwertmethode bevorzugen!

Grund: Wir wollen den absoluten Vermögenszuwachs (Euro) maximieren, nicht die prozentuale Rendite. 50% auf 1€ sind weniger wert als 10% auf 1 Mio. €5.

---
#### Flashcards

Wie ist der Interne Zinsfuß mathematisch definiert? :: Als der Zinssatz $i$, für den der Kapitalwert $KW_0$ der Investition gleich 0 ist.

Wann ist eine Investition nach der IZF-Methode vorteilhaft? :: Wenn der Interne Zinsfuß ($IZF$) höher ist als die Kapitalkosten (Kalkulationszins).

Wie lautet die allgemeine Formel zur Bestimmung des IZF (Ansatz)?
?
$$0 = -I_{0} + \sum_{t=1}^{n} \frac{CF_{t}}{(1+i)^{t}} + \frac{R_{n}}{(1+i)^{n}}$$


Wie lautet die spezifische $i_{IZF}$ Formel für vorgegebene Szenarien (Ohne Restwert)?
?
$$

 \rightarrow i_{IZF}=\sqrt{\frac{CF_t}{C_0}}-1

$$

Welches Verfahren hat Vorrang: Kapitalwert oder Interner Zinsfuß? :: Die **Kapitalwertmethode** hat Vorrang, da sie den absoluten Vermögenszuwachs maximiert (NPV > IRR).


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Interner Zinsfuß]]
SORT file.mtime DESC
```