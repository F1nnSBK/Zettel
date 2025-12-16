#Note

2025-12-08

Tags: [[Grundlagen Finanzierung & Investition]], [[Finanzierung]]
#finance

---
Der **WACC** (Weighted Average Cost of Capital) beziffert die durchschnittlichen Kapitalkosten eines Unternehmens. Er repräsentiert die **Mindestrendite**, die ein Unternehmen erwirtschaften muss, um die Ansprüche _aller_ Kapitalgeber (Eigen- und Fremdkapitalgeber) zu befriedigen.

#### Formel & Berechnung

Die Berechnung erfolgt als gewichtetes Mittel.
**1. Grundformel (Vor Steuern):**

$$WACC = \underbrace{\frac{EK}{GK} \cdot r_{EK}}_{\text{Gewichtete EK-Kosten}} + \underbrace{\frac{FK}{GK} \cdot r_{FK}}_{\text{Gewichtete FK-Kosten}}$$

2. Praxis-Formel (Nach Steuern / Tax Shield):
Da Fremdkapitalzinsen steuerlich abzugsfähig sind, sind die effektiven FK-Kosten geringer. Dies nennt man Tax Shield.

$$WACC = \frac{EK}{GK} \cdot r_{EK} + \frac{FK}{GK} \cdot r_{FK} \cdot (1 - s)$$

**Legende:**
- $GK$: Gesamtkapital ($EK + FK$)
- $r_{EK}$: Eigenkapitalkostensatz (Cost of Equity) $\rightarrow$ meist via CAPM bestimmt.
- $r_{FK}$: Fremdkapitalkostensatz (Cost of Debt).
- $s$: Ertragssteuersatz (Tax Rate).

#### Zusammenhänge

- **$r_{EK} > r_{FK}$:** Eigenkapital ist fast immer teurer als Fremdkapital, da Eigentümer ein höheres Risiko tragen (keine festen Ansprüche, Nachrangigkeit im Insolvenzfall) und eine Risikoprämie fordern.
    
- **Leverage-Effekt:** Durch die Aufnahme von günstigem Fremdkapital kann der WACC gesenkt werden (bis zu einem gewissen Grad).

---
#### Flashcards

Wofür steht die Abkürzung WACC? :: Weighted Average Cost of Capital (Gewichtete durchschnittliche Kapitalkosten).
<!--SR:!2025-12-17,1,228-->

Wie lautet die WACC-Formel?
?
$$WACC = \frac{EK}{GK} \cdot r_{EK} + \frac{FK}{GK} \cdot r_{FK}$$
<!--SR:!2025-12-17,1,228-->

Warum muss der Term $(1-s)$ bei den Fremdkapitalkosten berücksichtigt werden? :: Weil Fremdkapitalzinsen steuerlich absetzbar sind (Betriebsausgaben) und somit die effektive Steuerlast senken (**Tax Shield**).
<!--SR:!2025-12-17,1,224-->

Warum ist $r_{EK}$ in der Regel höher als $r_{FK}$? :: Weil Eigenkapitalgeber ein höheres Risiko tragen (Haftung, Unsicherheit) und dafür eine **Risikoprämie** verlangen.
<!--SR:!2025-12-17,1,230-->

Was sagt der WACC aus Investitionssicht aus? :: Er ist die **Mindestrendite** (Hurdle Rate), die eine Investition erwirtschaften muss, um für das Unternehmen wertsteigernd zu sein.
<!--SR:!2025-12-17,1,224-->

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[WACC]]
SORT file.mtime DESC
```