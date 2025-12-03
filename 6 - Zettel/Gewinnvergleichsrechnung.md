#Note

2025-12-02

Tags: [[Statische Investitionsrechenverfahren]], [[Rentabilitätsvergleichsrechnung]], [[]]
#finance

---
Die **Gewinnvergleichsrechnung** ist ein [[Statische Investitionsrechenverfahren|statisches Investitionsrechenverfahren]]. Das Ziel ist die Gewinnmaximierung anhand des durchschnittlich zu erwatenden Gewinns pro Jahr. Ist dieser Gewinn positiv, soll investiert werden.

$$
Gewinn = Erlös - Kosten
$$
#### Entscheidungsmöglichkeiten
1. Investition oder Nicht-Investition
   Wenn die durchschnittlichen Gewinne einer Investition positiv sind -> :: Investition tätigen.
2. Investition in A und B
   Wenn die durchschnittlichen Gewinne einer Investition A höher sind als die einer Alternative B -> :: investiere in A.

#### Ermittlung von Kosten & Erlöse
+ [[Kosten]] sind der bewertete, betriebszweckbezogene Güter**verbrauch** eines Unternehmens. Betriebszweckbezogen bedeutet: 1. für die relevante Periode und 2. im normalen Geschäftsbetrieb angefallen.
	+ [[Kalkulatorische Abschreibungen]]:$$Jährlicher\space Wertverlust \space (Abschreibung) = \frac{Anfangsinvestition - Restwert}{Nutzungsdauer}$$
	+ [[Kalkulatorische Zinsen]]: $$
Kalkulatorische\space Zinskosten = durchschnittlich\space eingesetztes\space Kapital \cdot Kapitalkostensatz
$$$$
Durchschnittlich\space investiertes\space Kapital = \frac{Anfangsinvestition + Restwert}{2}
$$
+ [[Erlöse]] sind Erträge aus Verkauf von Produkten und der Erbringung von Dienstleistungen.

Gewinn für ein [[Investitionsobjekt]]:

$$ G = \underbrace{(x \cdot p)}_{\text{Erlöse}} - \left( \underbrace{(x \cdot k_{var}) + K_{fix}}_{\text{Betriebskosten}} + \underbrace{\frac{I_0 - R_n}{n}}_{\text{Kalk. Abschreibung}} + \underbrace{\frac{I_0 + R_n}{2} \cdot i}_{\text{Kalk. Zinsen}} \right) $$

𝐺 = Gewinn (pro Jahr) 
𝑥 = Produktionsmenge (pro Jahr) 
𝑝 = Absatzpreis (pro Stück) 
$𝑘_{𝑣𝑎𝑟}$ = laufende variable Kosten (pro Stück) 
$𝐾_{𝑓𝑖𝑥}$ = laufende Fixkosten (pro Jahr) 
$I_0$ = Investitions- bzw. Anschaffungsausgabe 
$𝑅_𝑛$ = Restwert bzw. Liquidationserlös 
𝑛 = Nutzungsdauer
𝑖 = kalkulatorischer Zinssatz

#### Interpretation
+ Kurzfristigkeit des Gewinnvergleiches: Üblicherweise erfolgt die Berechnung für ein Jahr, das ist besonders problematisch, wenn es das erste Jahr der Nutzung ist.
	  Bei Alternativen mit unterschiedlicher Nutzungsdauer können wir keine Aussage für den Differenzzeitraum treffen.
	  Die Methode benachteiligt tendenziell die günstigere Investition, weil sie das **Gewinnpotenzial des gesparten Geldes** künstlich auf den Zinssatz deckelt. Sie ignoriert, dass du mit dem Differenzbetrag "Alpha" (Überrendite) generieren könntest.
+ Zurechenbarkeit der Erlöse: Es kann Schwierigkeiten bei der **Zuordnung** von Erlösen kommen, wenn ein Produkt auf mehreren Maschinen gefertigt wird.
+ Nichtberücksichtigung des Kapitaleinsatzes: Die Einbeziehung des Kapitaleinsatzes zeigt erst, inwieweit eine Investition wirklich rentabel ist.

Was passiert bei der Gewinnvergleichsrechnung? :: Bei der Gewinnvergleichsrechnung wird der durchschnittlich zu erwartende Gewinn pro Jahr ermittelt und auf dessen Basis entschieden. Ziel ist die **Gewinnmaximierung**.

Vorgehensweise Gewinnvergleichsrechnung (Algorithmus)
?
1. **Erlöse** ermitteln ($x \cdot p$).
2. **Operative Kosten** ermitteln ($x \cdot k_{var} + K_{fix}$).
3. **Kalk. Abschreibung** berechnen ($\frac{AK-RW}{n}$).
4. **Kalk. Zinsen** berechnen ($\frac{AK+RW}{2} \cdot i$).
5. **Gewinn** = 1 - (2 + 3 + 4).
6. **Entscheidung**: Wähle max(Gewinn), sofern > 0.

Was sind 3 Probleme der GVR? :: Kurzfristigkeit des Gewinnvergleiches, d.h. Berechnungen sind üblicherweise für ein Jahr, die Zukunft wird nicht betrachtet. Zurechenbarkeit der Erlöse: Wird ein Produkt auf mehreren Maschinen produziert? -> Welche Maschine trägt welchen bei? Nichtberücksichtigung des Kapitaleinsatzes: Die Einbeziehung des Kapitaleinsatzes zeigt erst, inwieweit eine Investition wirklich rentabel ist.

---
### Verwendung
```dataview
list from [[Gewinnvergleichsrechnung]]
```