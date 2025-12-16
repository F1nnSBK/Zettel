#Note

2025-12-15

Tags: [[Bilanzierung]], [[Jahresabschlussanalyse]], [[Kennzahlen]], [[KPI]]
#finance

---
#### 1. Beurteilung der Ertragslage (Rentabilität)

Wie effizient arbeitet das Unternehmen?
**A) EBIT & EBITDA**
- **EBIT** (Earnings Before Interest and Taxes): Operatives Ergebnis. Zeigt die Stärke des Kerngeschäfts unabhängig von der Finanzierung (Zinsen) und dem Standort (Steuern).
    - _Ziel:_ Muss größer sein als der Zinsaufwand.
    
- **EBITDA:** EBIT vor Abschreibungen. Zeigt die "kassenwirksame" Ertragskraft (Proxy für operativen Cashflow).
+ **Jahresüberschuss**: Größer als 0.

B) Umsatzrendite (Return on Sales - ROS)
Wie viel Cent bleiben von 1 € Umsatz als Gewinn hängen?
$$ \text{Umsatzrendite} = \frac{\text{Jahresüberschuss}}{\text{Umsatzerlöse}} \cdot 100$$

- _Faustregel:_ Sollte $> 5\%$ sein (branchenabhängig).

C) Eigenkapitalrentabilität (Return on Equity - RoE)
Verzinsung des eingesetzten Eigenkapitals.

$$ \text{EK-Rentabilität} = \frac{\text{Jahresüberschuss}}{\varnothing \text{Eigenkapital}} \cdot 100$$

- _Benchmark:_ Sollte deutlich über dem Kapitalmarktzins liegen (Risikoprämie), ca. > 8-10%.
#### 2. Beurteilung der Finanzlage (Sicherheit/Liquidität)

Droht Zahlungsunfähigkeit?
A) Zinsdeckungsgrad (Interest Coverage) 

Kann das Unternehmen seine Zinsen aus dem operativen Gewinn zahlen?

$$ \text{Zinsdeckungsgrad} = \frac{\text{EBIT}}{\text{Zinsaufwand}}$$

- _Faustregel:_ Sollte für gesunde Firmen $> 2$ (besser $> 3$) sein.

B) Eigenkapitalquote (Equity Ratio)
Wie hoch ist der Anteil des eigenen Geldes am Gesamtkapital? (Verlustpuffer).

$$ \text{EK-Quote} = \frac{\text{Eigenkapital}}{\text{Gesamtkapital}} \cdot 100$$

- _Faustregel:_ $> 33\%$ gilt als solide. $< 0\%$ bedeutet Überschuldung.

C) Operativer Cash Flow (OCF)
Muss positiv sein und idealerweise die Investitionen decken (Free Cash Flow).

#### 3. Beurteilung der Vermögensstruktur (Working Capital)

Wie effizient wird das Kapital gebunden?
- **Cash Conversion Cycle (CCC):** Wie lange dauert es, bis aus Wareneinsatz wieder Geld wird?.
    - **DIO (Days Inventory):** Lagerdauer (kurz ist gut).
    - **DRO (Days Receivables):** Dauer bis Kunden zahlen (kurz ist gut).
    - **DPO (Days Payables):** Dauer bis wir Lieferanten zahlen (lang ist gut für Liquidität)

---
#### Flashcards

Was ist der Zweck der Kennzahl **EBIT**? :: Sie zeigt die Stärke des **operativen Kerngeschäfts** eines Unternehmens, da sie von Zinsen und Steuern unabhängig ist.
<!--SR:!2025-12-17,1,230-->

Was zeigt das **EBITDA** an und wofür wird es als Proxy verwendet? :: Es zeigt die Ertragskraft vor Zinsen, Steuern und Abschreibungen (DA) und dient als Näherungswert für den **operativen Cashflow**.

Wie lautet die Formel zur Berechnung der Umsatzrendite (ROS)?
?
$$ \text{Umsatzrendite} = \frac{\text{Jahresüberschuss}}{\text{Umsatzerlöse}} \cdot 100$$
<!--SR:!2025-12-17,1,230-->

Was ist die primäre Aussage der **Eigenkapitalrentabilität (RoE)**? :: Sie misst die **Verzinsung** des von den Eigentümern eingesetzten Kapitals.
<!--SR:!2025-12-17,1,230-->

Wie lautet die Formel zur Berechnung des Zinsdeckungsgrades (Interest Coverage)?
?
$$ \text{Zinsdeckungsgrad} = \frac{\text{EBIT}}{\text{Zinsaufwand}}$$

Was ist der Zielwert für den **Zinsdeckungsgrad** bei gesunden Unternehmen? :: Er sollte idealerweise **$> 2$** (besser $> 3$) sein.

Welche Funktion erfüllt die **Eigenkapitalquote** im Hinblick auf die Unternehmenssicherheit? :: Sie dient als **Verlustpuffer** und ist ein wichtiger Indikator für die Bonität und Krisenfestigkeit (Solvenz).

Ab welchem Richtwert gilt die **Eigenkapitalquote** als solide? :: Ab **$> 33\%$**.

Was ist die Hauptanforderung an den **Operativen Cash Flow (OCF)**? :: Er muss **positiv** sein und im Idealfall die **Investitionen** decken (dann spricht man von Free Cash Flow).

Was misst der **Cash Conversion Cycle (CCC)**? :: Die Dauer in Tagen, bis aus einer Investition in Waren/Materialien durch Verkauf und Zahlungseingang wieder **flüssige Mittel** generiert werden.

Welche der drei Working Capital Kennzahlen (DIO, DRO, DPO) sollte **lang** sein, um die Liquidität zu verbessern? :: **DPO** (Days Payables Outstanding), da die Zahlungsfrist an die Lieferanten verlängert wird.

Was bedeutet ein kurzer **DIO** (Days Inventory Outstanding)? :: Die Lagerdauer ist kurz, d.h., das Unternehmen hat wenig Kapital im **Lager** gebunden.
<!--SR:!2025-12-17,1,230-->


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Jahresabschlusserstellung]]
SORT file.mtime DESC
```