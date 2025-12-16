#Note

2025-12-11

Tags: [[Grundlagen Finanzierung & Investition]], [[Aktie]], [[Kennzahlen]]
#finance

---
Die **Dividende** ist der auf eine einzelne Aktie entfallende Anteil am Bilanzgewinn, der an die Aktionäre ausgeschüttet wird.

#### 1. Prozess der Ausschüttung
Die Dividende ist nicht garantiert.
1. **Vorschlag:** Vorstand und Aufsichtsrat machen einen Gewinnverwendungsvorschlag.
2. **Beschluss:** Die **Hauptversammlung (HV)** beschließt die Höhe der Dividende (mit einfacher Mehrheit).
3. **Auszahlung:** Am dritten Geschäftstag nach der HV.
    

**Wichtige Zeitpunkte (Timeline):**
- **Cum-Dividende:** Die Aktie wird _mit_ dem Anspruch auf die Dividende gehandelt.
- **Ex-Dividende Tag:** Der Tag nach der HV. Die Aktie wird erstmals _ohne_ den Dividendenanspruch gehandelt.
- Dividendenabschlag: Am Ex-Tag fällt der Aktienkurs rechnerisch genau um die Höhe der Brutto-Dividende (da das Geld das Unternehmen verlassen hat).
$$\text{Kurs}_{ex} \approx \text{Kurs}_{cum} - \text{Dividende}$$
#### 2. Kennzahlen
A) Dividendenrendite (Dividend Yield)
Gibt die Verzinsung des eingesetzten Kapitals allein durch die Ausschüttung an (ohne Kursgewinne).

$$\text{Dividendenrendite} = \frac{\text{Dividende je Aktie (DPS)}}{\text{Aktienkurs}} \cdot 100$$

_Interpretation:_ Hohe Dividendenrenditen finden sich oft bei etablierten "Value-Unternehmen" (z.B. Versorger, Telekommunikation) mit geringerem Wachstum.

B) Ausschüttungsquote (Payout Ratio)
Gibt an, wie viel Prozent des Gewinns ausgeschüttet werden.

$$\text{Ausschüttungsquote} = \frac{\text{Dividende je Aktie}}{\text{Gewinn je Aktie (EPS)}} \cdot 100$$

- _Quote < 50 %:_ Unternehmen investiert Gewinne in Wachstum (Thesaurierung).
- _Quote > 80-100 %:_ Warnsignal (Ausschüttung aus der Substanz?).
    

#### 3. Kapitalkosten-Aspekt (Gordon Growth Model)
Die Dividende dient zur Herleitung der Eigenkapitalkosten ($r_{EK}$).
Nach dem Dividendenwachstumsmodell gilt (vereinfacht für konstantes Wachstum $g$):

$$r_{EK} = \frac{\text{Dividende}_1}{\text{Aktienkurs}_0} + g$$

Wenn das Unternehmen **nicht wächst** ($g=0$), entspricht die **Dividendenrendite** exakt den Eigenkapitalkosten.

---
#### Flashcards

Wer beschließt die Höhe der Dividende? :: Die **Hauptversammlung** der Aktionäre (auf Vorschlag von Vorstand/Aufsichtsrat).
<!--SR:!2025-12-17,1,230-->

Was passiert am "Ex-Dividende"-Tag mit dem Aktienkurs? :: Der Kurs sinkt rechnerisch um die Höhe der Dividende (**Dividendenabschlag**), da das Vermögen das Unternehmen verlässt.
<!--SR:!2025-12-17,1,230-->

Wie lautet die Formel für die Dividendenrendite?
?
$$\text{Dividendenrendite} = \frac{\text{Dividende je Aktie}}{\text{Aktienkurs}} \cdot 100$$

Was sagt die Ausschüttungsquote (Payout Ratio) aus? :: Welchen prozentualen Anteil des Jahresüberschusses (Gewinns) das Unternehmen an die Aktionäre auszahlt (vs. Thesaurierung).

Wie lautet die Formel für die Ausschüttungsquote?
?
$$\text{Ausschüttungsquote} = \frac{\text{Dividende je Aktie (DPS)}}{\text{Gewinn je Aktie (EPS)}}$$

Warum haben Wachstumsunternehmen (Tech) oft eine niedrige Dividendenrendite? :: Weil sie Gewinne lieber reinvestieren ([[Thesaurierung]]), um weiteres Wachstum zu finanzieren, statt sie auszuschütten.
<!--SR:!2025-12-17,1,230-->

Ein Unternehmen zahlt 2 € Dividende bei einem Gewinn von 4 € pro Aktie. Wie hoch ist die Ausschüttungsquote? :: 50 %.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Dividende]]
SORT file.mtime DESC
```