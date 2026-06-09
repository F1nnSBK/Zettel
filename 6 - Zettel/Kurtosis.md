#Note

2026-05-15

Tags: [[Statistik]], [[Deskriptive Statistik]], [[Normalverteilung]], [[Kurtosis]], [[Anomalieerkennung]]
#deskriptive_statistik

---
Die **Wölbung** (Kurtosis) ist ein Maß für die Form einer Verteilung. Sie gibt an, wie spitz der Gipfel ist und wie flach oder steil die Enden (Tails) der Verteilung auslaufen.

### Klassifizierung der Wölbung

Man vergleicht die empirische Wölbung meist mit der Normalverteilung ($N=3$).

- **Mesokurtisch (Normalwölbung):** Entspricht der Normalverteilung.
    - $\text{Kurtosis} = 3$ bzw. $\text{Excess} = 0$.

- **Leptokurtisch (Steilgewölbt / Super-Gauß):** Höherer Gipfel und „schwerere“ Enden (Heavy Tails). Extremwerte sind wahrscheinlicher als bei der Normalverteilung.
    - $\text{Kurtosis} > 3$ bzw. $\text{Excess} > 0$.

- **Platykurtisch (Flachgewölbt / Sub-Gauß):** Flacherer Gipfel und „leichte“ Enden. Extremwerte sind seltener.
    - $\text{Kurtosis} < 3$ bzw. $\text{Excess} < 0$.


### Mathematische Definition

Der Wölbungskoeffizient $g_2$ (nach Pearson) normiert das vierte zentrale Moment durch das Quadrat der Varianz:

$$g_2 = \frac{\frac{1}{n} \sum_{i=1}^n (x_i - \bar{x})^4}{s^4}$$

Da die Kurtosis einer Normalverteilung immer 3 ergibt, nutzt man in der Praxis oft den **Excess** (Exzess):

$$\text{Excess} = g_2 - 3$$

### Bedeutung im Machine Learning & Finanzen

- **Asset Pricing:** Renditen von Aktien sind oft leptokurtisch. Das bedeutet, "Black Swan"-Events (extreme Einbrüche) passieren häufiger, als es ein Normalverteilungsmodell vorhersagen würde.

- **ICA (Independent Component Analysis):** Die Kurtosis wird hier als Zielfunktion genutzt, um unabhängige Signale zu trennen, da Mischsignale (nach dem Zentralen Grenzwertsatz) tendenziell mesokurtischer sind als die Originalsignale.

- **Data Cleaning:** Eine extrem hohe Kurtosis ist oft ein technischer Indikator für unentdeckte Ausreißer oder Messfehler.


---

### Flashcards

Was beschreibt der Begriff "Heavy Tails" im Zusammenhang mit einer hohen Kurtosis?::Er bedeutet, dass die Enden der Verteilung langsamer gegen Null sinken als bei einer Normalverteilung, wodurch extreme Abweichungen (Ausreißer) eine signifikant höhere Wahrscheinlichkeit haben.

Warum zieht man in der Statistik oft 3 vom berechneten Kurtosis-Wert ab?::Um den **Excess** zu erhalten. Da eine Normalverteilung eine Kurtosis von 3 hat, lässt sich am Excess sofort ablesen, ob die vorliegende Verteilung steiler (positiv) oder flacher (negativ) als die Normalverteilung ist.
<!--SR:!2026-06-09,1,230-->

Wie unterscheiden sich leptokurtische und platykurtische Verteilungen visuell von einer Normalverteilung?
?
Leptokurtische Verteilungen haben einen spitzeren Gipfel und dickere Enden (Ausreißergefahr). Platykurtische Verteilungen sind flacher, eher plateau-artig und haben sehr dünne, kurz auslaufende Enden.

Warum ist die Kurtosis ein "riskanteres" Maß als die Varianz?
?
Die Varianz misst nur die durchschnittliche Streuung. Die Kurtosis zeigt jedoch an, ob diese Streuung durch viele kleine Abweichungen (mesokurtisch) oder durch seltene, aber extrem große Abweichungen (leptokurtisch) zustande kommt.
<!--SR:!2026-06-09,1,230-->


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Kurtosis]]
SORT file.mtime DESC
```