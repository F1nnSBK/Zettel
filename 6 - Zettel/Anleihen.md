#Note

2025-12-11

Tags: [[Grundlagen Finanzierung & Investition]], [[Fremdkapital]], [[Kapitalmarkt]], [[Finanzierungsinstrument]]

---
Die **Anleihe** (auch: Bond, Rentenpapier, Obligation, Schuldverschreibung) ist ein wertpapiermäßig verbriefter Kredit, der am Kapitalmarkt handelbar ist.
Der Käufer der Anleihe wird zum Gläubiger, der Emittent (Herausgeber) zum Schuldner.

#### 1. Die Anatomie einer Anleihe

Eine klassische Festzinsanleihe (Straight Bond) wird durch vier Parameter definiert:
1. **Emittent:** Wer schuldet das Geld? (z.B. Staat = Staatsanleihe, Unternehmen = Corporate Bond).
2. **Nennwert (Nominalwert):** Der Betrag, der am Ende der Laufzeit zurückgezahlt wird (Basis für die Zinsberechnung).
3. **Kupon (Nominalzins):** Die festgelegte, regelmäßige Zinszahlung in Prozent des Nennwerts.
4. **Laufzeit:** Der Zeitraum bis zur Rückzahlung.
    

#### 2. Kursnotierung & Rendite

Anleihen werden an der Börse in **Prozent des Nennwerts** notiert.
- **Par (zu pari):** Kurs = 100 %. (Marktzins = Kupon).
- **Über Par (Above Par):** Kurs > 100 %. (Marktzins < Kupon). Die Anleihe ist "wertvoller", weil sie höhere Zinsen zahlt als der aktuelle Markt.
- **Unter Par (Below Par):** Kurs < 100 %. (Marktzins > Kupon). Die Anleihe ist "billiger", um die niedrigen Zinsen auszugleichen.

Wichtig: Die inverse Zins-Kurs-Beziehung
Steigen die Marktzinsen, fallen die Kurse bestehender Anleihen (und umgekehrt).

Grund: Wenn neue Anleihen 4% Zinsen bringen, will niemand mehr eine alte 2%-Anleihe zu 100% kaufen. Der Kurs der alten Anleihe muss fallen, bis ihre Rendite wieder dem Marktniveau entspricht.

$$\text{Barwert (Preis)} = \sum_{t=1}^{n} \frac{\text{Kupon}}{(1+i)^t} + \frac{\text{Nennwert}}{(1+i)^n}$$

#### 3. Besondere Formen

- **[[Null-Kupon-Anleihe]] (Zero Bond):** Keine laufenden Zinsen. Rendite entsteht nur durch die Differenz zwischen Ausgabekurs (z.B. 80%) und Rückzahlung (100%).
- **Wandelanleihe (Convertible Bond):** Gibt dem Inhaber das Recht, die Anleihe während der Laufzeit in **Aktien** des Unternehmens zu tauschen. (Hybridform FK $\rightarrow$ EK).
- **Floating Rate Note (Floater):** Variabler Zinssatz, der regelmäßig an einen Referenzzins (z.B. EURIBOR) angepasst wird.
    

#### 4. Risiken

1. **Bonitätsrisiko (Default Risk):** Der Emittent wird zahlungsunfähig ([[Rating]], [[Credit Spread]]).
2. **Zinsänderungsrisiko:** Das Risiko von Kursverlusten bei steigenden Marktzinsen (siehe oben).

---
#### Flashcards

Was ist eine Anleihe (Bond)? :: Ein wertpapiermäßig verbriefter Kredit, der am Kapitalmarkt gehandelt wird.

Wie reagiert der Kurs einer Festzinsanleihe, wenn der allgemeine Marktzins steigt? :: Der Kurs der Anleihe **fällt** (Inverse Beziehung).

Was bedeutet es, wenn eine Anleihe "unter pari" notiert? :: Der Kurs liegt unter 100 % des Nennwerts.

Was ist eine Wandelanleihe (Convertible Bond)? :: Eine Anleihe, die dem Inhaber das Recht gibt, sie in **Aktien** des Unternehmens umzutauschen.

Was unterscheidet die Rendite einer Anleihe vom Kupon? :: Der **Kupon** ist der feste Zins auf den Nennwert. Die **Rendite** ist der tatsächliche Gewinn pro Jahr unter Berücksichtigung des **Kaufkurses**.

Warum notieren Anleihen über 100% (über pari)? :: Weil ihr Kupon **höher** ist als das aktuelle Marktzinsniveau (Investoren zahlen einen Aufpreis für den hohen Zins).

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Anleihen]]
SORT file.mtime DESC
```