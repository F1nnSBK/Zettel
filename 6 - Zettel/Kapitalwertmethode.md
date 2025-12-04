#Note

2025-12-04

Tags: [[Dynamische Investitionsrechenverfahren]], [[Kapitalwert]]
#finance

---
Die Kapitalwertmethode ist eine [[Dynamische Investitionsrechenverfahren|dynamische Investitionsrechnungsmethode]] zur Beurteilung der Wirtschaftlichkeit eines [[Investitionsobjekt|Projekts]], indem sie die Summe aller abgezinsten Ein- und Auszahlungen (den Kapitalwert oder Nettobarwert) berechnet.

| Kapitalwert | Bedeutung                                                                                                            | Entscheidung                |
| ----------- | -------------------------------------------------------------------------------------------------------------------- | --------------------------- |
| $KW_0 > 0$  | **Vermögenszuwachs:** Die Rendite des Projekts liegt _oberhalb_ des Kalkulationszinssatzes. Es wird Wert geschaffen. | Investieren                 |
| $KW_0 = 0$  | **Mindestverzinsung:** Die Rendite entspricht exakt dem Kalkulationszinssatz.                                        | Indifferent (im Zweifel ja) |
| $KW_0 < 0$  | **Vermögensminderung:** Die Rendite liegt _unterhalb_ des Kalkulationszinssatzes. Kapitalvernichtung.                | Nicht investieren           |
**Auswahlproblem:** Bei zwei positiven Alternativen wähle das Projekt mit dem **höheren Kapitalwert** (absoluter Vermögenszuwachs).

**Vorteile:**
- Basiert auf **Cash Flows**, nicht auf manipulierbaren Gewinngrößen des Rechnungswesens.
- Berücksichtigt den **Zeitwert des Geldes** (Zinseffekte) explizit durch Diskontierung.
**Nachteile:**
- Der Kapitalwert ist eine **absolute Kennzahl** (in €). Ein Vergleich von Projekten unterschiedlicher Größe ist schwierig (im Gegensatz zu relativen %-Größen wie [[Return on Investment|ROI]]).


Wie lautet die Formel für den Kapitalwert bei einer Investition mit Restwert? ::
$$KW_{0} = -I_{0} + \sum_{t=1}^{n} \frac{CF_{t}}{(1+i)^{t}} + \frac{R_{n}}{(1+i)^{n}}$$

Was bedeutet ein Kapitalwert von exakt 0? :: Die Investition erwirtschaftet genau den Kalkulationszinssatz (Mindestverzinsung). Es entsteht kein zusätzlicher Vermögenszuwachs.

Welches Entscheidungskriterium gilt bei der Auswahl zwischen zwei vorteilhaften Investitionen gemäß Kapitalwertmethode? :: Wähle das Projekt mit dem höheren absoluten Kapitalwert.

Nenne einen Vorteil der Kapitalwertmethode gegenüber statischen Verfahren (z.B. Gewinnvergleich). :: Berücksichtigung des Zeitwerts des Geldes (Zinseffekte) ODER Verwendung von objektiven Cash Flows statt manipulierbaren Gewinnen. 

Nenne einen Nachteil der Kapitalwertmethode. :: Als absolute Kennzahl ist sie schlecht geeignet, um Projekte unterschiedlicher Größe zu vergleichen.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Kapitalwertmethode]]
SORT file.mtime DESC
```