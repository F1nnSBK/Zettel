#Note

2025-12-11

Tags: [[Grundlagen Finanzierung & Investition]], [[Rentabilität]], [[Verschuldung]] 
#finance

---
Der **Leverage-Effekt** (Hebelwirkung) beschreibt die Sensitivität der Eigenkapitalrendite ($r_{EK}$) in Abhängigkeit vom Verschuldungsgrad. Er besagt, dass sich die Eigenkapitalrentabilität durch den Einsatz von Fremdkapital steigern lässt, solange die Gesamtkapitalrentabilität ($r_{GK}$) höher ist als der Fremdkapitalzins ($r_{FK}$).

- **Positiver Leverage-Effekt:** $r_{GK} > r_{FK}$ $\rightarrow$ Aufnahme von Schulden erhöht die EK-Rendite.
- **Negativer Leverage-Effekt:** $r_{GK} < r_{FK}$ $\rightarrow$ Aufnahme von Schulden "frisst" das Eigenkapital auf (Verlusthebel).

**Formel (Leverage-Gleichung):**

$$r_{EK} = r_{GK} + (r_{GK} - r_{FK}) \cdot \frac{FK}{EK}$$

- $r_{EK}$: Eigenkapitalrentabilität
- $r_{GK}$: Gesamtkapitalrentabilität (Return on Assets)
- $r_{FK}$: Fremdkapitalzinssatz
- $\frac{FK}{EK}$: Verschuldungsgrad (Hebel/Leverage)

Risiko:
Mit steigendem Verschuldungsgrad nimmt die Variabilität der Eigenkapitalrendite zu. Zudem steigt das Insolvenzrisiko, weshalb Banken bei hoher Verschuldung meist höhere Zinsen ($r_{FK}$) fordern, was den Effekt wieder abschwächen kann.

---
#### Flashcards

Was beschreibt der Leverage-Effekt? :: Die Hebelwirkung des Fremdkapitals auf die Eigenkapitalrentabilität bei steigendem Verschuldungsgrad.

Wie lautet die zentrale Bedingung für einen positiven Leverage-Effekt?
?
$$r_{GK} > r_{FK}$$
(Die Gesamtkapitalrendite muss höher sein als der Fremdkapitalzins).
<!--SR:!2025-12-17,1,230-->

Wie lautet die Formel für den Leverage-Effekt ($r_{EK}$)?
?
$$r_{EK} = r_{GK} + (r_{GK} - r_{FK}) \cdot \frac{FK}{EK}$$
<!--SR:!2025-12-17,1,230-->

Was passiert beim "Negativen Leverage-Effekt"? :: Die Gesamtkapitalrendite ist kleiner als der Fremdkapitalzins ($r_{GK} < r_{FK}$), wodurch jeder Euro zusätzliche Schulden die Eigenkapitalrendite verringert (Verlust).
<!--SR:!2025-12-17,1,230-->

Welches Risiko steigt mit zunehmendem Leverage (Verschuldung)? :: Das **Insolvenzrisiko** und die Volatilität der Rendite (Risiko für die Eigenkapitalgeber).

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Note]]
SORT file.mtime DESC
```