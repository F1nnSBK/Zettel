#Note

2025-12-11

Tags: [[Grundlagen Finanzierung & Investition]], [[Fremdkapitalfinanzierung]], [[Risikomanagement]], [[Fremdkapital]]
#finance

---
**Covenants** (Financial Covenants & General Covenants) sind vertragliche **Nebenabreden** in Kreditverträgen. Der Kreditnehmer verpflichtet sich gegenüber der Bank, während der Laufzeit bestimmte Kennzahlen einzuhalten oder bestimmte Handlungen vorzunehmen bzw. zu unterlassen.

**Zweck:** Sie dienen der Bank als **Frühwarnsystem**. Verschlechtert sich die Lage des Schuldners, greifen die Covenants, _bevor_ die Zahlungsunfähigkeit eintritt.

#### 1. Folgen eines Vertragsbruchs (Covenant Breach)

Verletzt der Kreditnehmer eine Klausel, gilt dies als Vertragsbruch. Die Bank hat dann meist folgende Rechte (Eskalationsstufen):

1. **Waiver Fee:** Der Kreditnehmer zahlt eine Gebühr, damit die Bank einmalig auf ihr Recht verzichtet ("Heilung").
2. **Margin Step-up:** Der Zinssatz (Risikoprämie) wird erhöht.
3. **Nachbesicherung:** Die Bank fordert zusätzliche Sicherheiten.
4. **Kündigung (Acceleration):** Der Kredit wird sofort fällig gestellt (schlimmster Fall $\rightarrow$ oft Insolvenzauslöser).

---

#### 2. Arten von Covenants

Man unterscheidet quantitative (finanzielle) und qualitative Covenants.
A) Financial Covenants (Finanzkennzahlen)
Verpflichtung, bestimmte finanzielle Grenzwerte nicht zu verletzen.
- **Eigenkapitalquote:** "Muss $> 30\%$ betragen."
- **Verschuldungsgrad (Leverage Ratio):** "Net Debt / EBITDA muss $< 3,5x$ sein."
- **Zinsdeckungsgrad (Interest Cover):** "EBITDA / Zinsaufwand muss $> 5x$ sein."
    

**B) Non-Financial Covenants (Verhaltenspflichten)**
- Information Covenants:
    Pflicht zur regelmäßigen Berichterstattung (Quartalsberichte, Budgets) oder Ad-hoc-Meldung bei gravierenden Ereignissen (z.B. Klagen, Verlust von Großkunden).
- Affirmative Covenants (Gebote):
    Handlungen, die das Unternehmen tun muss.
    - _Beispiel:_ Instandhaltung der Vermögenswerte, Einhaltung von Gesetzen (Compliance), Versicherungsschutz aufrechterhalten.
- Negative Covenants (Verbote):
    Handlungen, die das Unternehmen unterlassen muss.
    - **Negative Pledge (Negativerklärung/Verpfändungsverbot):** Verbot, anderen Gläubigern Sicherheiten an Vermögenswerten zu geben, wenn die Bank keine erhält.
    - **Disposal of Assets Restriction:** Verbot, wesentliche Vermögenswerte (z.B. profitable Tochtergesellschaften) ohne Zustimmung der Bank zu verkaufen.

---
#### 3. Wichtige Schutzklauseln

Diese Klauseln regeln das Verhältnis zu _anderen_ Gläubigern:
- Pari-Passu-Klausel (Gleichrangigkeit):
    Zusicherung, dass der Kredit im Insolvenzfall im gleichen Rang steht wie alle anderen unbesicherten Verbindlichkeiten (Schutz vor nachträglicher Unterordnung).
- Cross-Default-Clause (Drittverzugsklausel):
    "Fällt ein Stein, fallen alle."
    Wenn der Schuldner bei einem anderen Kreditgeber in Verzug gerät (Default), gilt der Kreditvertrag mit der Bank auch automatisch als gebrochen und kann gekündigt werden.
    - _Ziel:_ Verhindert, dass eine Bank stillhält, während andere schon das Vermögen pfänden.

---
#### Flashcards

Was sind Covenants (Kreditklauseln)? :: Vertragliche Nebenabreden im Kreditvertrag, in denen sich der Kreditnehmer zu bestimmtem Verhalten oder der Einhaltung von Kennzahlen verpflichtet.
<!--SR:!2025-12-17,1,230-->

Was ist der Zweck von Covenants aus Sicht der Bank? :: Sie dienen als **Frühwarnsystem**, um Risiken zu erkennen und einzugreifen, _bevor_ der Kreditnehmer zahlungsunfähig wird.
<!--SR:!2025-12-17,1,228-->

Was sind **Financial Covenants**? :: Verpflichtungen zur Einhaltung quantitativer Finanzkennzahlen (z.B. Mindest-Eigenkapitalquote, Höchst-Verschuldungsgrad).

Was sind **Affirmative Covenants**? :: Gebote, bestimmte Handlungen vorzunehmen (z.B. Instandhaltung von Vermögenswerten, Einreichen von Quartalsberichten).

Was sind **Negative Covenants**? :: Verbote, bestimmte Handlungen zu unterlassen (z.B. keine weiteren Kredite aufnehmen, keine Vermögenswerte verkaufen).
<!--SR:!2025-12-17,1,228-->

Was besagt die **Negative Pledge** Klausel (Negativerklärung)? :: Das Verbot, anderen Gläubigern Sicherheiten zu gewähren, ohne den aktuellen Kreditgeber gleichzustellen (Verpfändungsverbot).

Was besagt die **Pari-Passu** Klausel? :: Die Zusicherung, dass der Kredit im Insolvenzfall **im gleichen Rang** steht wie alle anderen unbesicherten Verbindlichkeiten (Gleichrangigkeit).
<!--SR:!2025-12-17,1,228-->

Was besagt die **Cross-Default-Clause** (Drittverzugsklausel)? :: Wenn der Schuldner bei einem _anderen_ Gläubiger in Verzug gerät, gilt auch dieser Kreditvertrag als gebrochen (Kündigungsrecht).

Was passiert typischerweise bei einem "Covenant Breach" (Vertragsbruch)? :: Die Bank erhält Sanktionsrechte: Strafgebühr (Waiver Fee), Zinserhöhung (Margin Step-up), Nachbesicherung oder sofortige Kündigung.

Was ist eine "Waiver Fee"? :: Eine Gebühr, die der Kreditnehmer zahlt, damit die Bank einmalig auf ihr Kündigungsrecht nach einem Covenant Breach verzichtet (Verzichtserklärung).

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Covenants]]
SORT file.mtime DESC
```