#Note

2025-12-11

Tags: [[Grundlagen Finanzierung & Investition]], [[Fremdkapital]], [[Fremdkapitalfinanzierung]], [[Risikomanagement]]
#finance

---
Die **Kreditprüfung** ist der standardisierte Prozess einer Bank zur Beurteilung des Risikos vor der Kreditvergabe. Sie bestimmt maßgeblich den Zinssatz (Preis) und die Entscheidung über die Kreditvergabe.

#### 1. Der Prozess der Kreditprüfung
1. **Bonitätsanalyse:** Prüfung der wirtschaftlichen Verhältnisse (Jahresabschluss, Kennzahlen) $\rightarrow$ [[Bonität]]sscore.
2. **Sicherheitenbewertung:** Analyse und Bewertung der angebotenen Sicherheiten (Beleihungswert).
3. **[[Rating]]:** Zusammenführung von Bonität und Sicherheiten zu einer Risikoklasse (Rating).
4. **Konditionengestaltung:** Festlegung des Risikozuschlags und der Covenants.
5. **Angebot:** Festlegung von Nominalzins, Kreditlinien und Bereitstellungszinsen.
    

---
#### 2. Kennzahlenanalyse (Quantitative Bonität)

Zwei Kennzahlen sind für die Schuldentragfähigkeit zentral:

A) Kapitaldienstfähigkeit
Misst, ob der operative Cashflow ausreicht, um Zins und Tilgung zu decken.

$$ \text{Kapitaldienstfähigkeit} = \frac{\text{Operativer Cash Flow}}{\text{Zinszahlungen} + \text{Tilgungszahlungen}}$$

(Ersatzweise EBITDA, falls OCF nicht verfügbar).

- **Zielwert:** $\ge 1$ (bzw. 100%). Je höher, desto sicherer.
    

B) Dynamischer Verschuldungsgrad
Gibt an, wie viele Jahre es theoretisch dauern würde, die Schulden aus dem Cashflow vollständig zu tilgen.

$$ \text{Dyn. Verschuldungsgrad} = \frac{\text{Finanzschulden (Net Debt)}}{\text{Operativer Cash Flow}}$$

- **Zielwert:** $< 7$ Jahre (Faustregel).

---
#### 3. Sicherheiten

Ziel ist die Reduzierung des **Loss Given Default** (Verlust bei Ausfall).

A) Bürgschaft (§ 765 BGB)
Ein Dritter verpflichtet sich, für die Schulden des Hauptschuldners einzustehen. Es ist eine akzessorische Sicherheit (abhängig von der Forderung).

- Gewöhnliche Bürgschaft (Ausfallbürgschaft):
    Der Bürge hat die Einrede der Vorausklage (§ 771 BGB). Die Bank muss erst versuchen, beim Hauptschuldner zu pfänden (Zwangsvollstreckung). Erst wenn das erfolglos ist, muss der Bürge zahlen.
    
- Selbstschuldnerische Bürgschaft:
    Der Bürge verzichtet auf die Einrede der Vorausklage (§ 773 BGB). Die Bank kann sofort auf den Bürgen zugreifen, wenn der Schuldner nicht zahlt. (Standard bei Bankbürgschaften).

B) Grundschuld
Ein dingliches Recht an einem Grundstück zur Zahlung einer Geldsumme.
- **Nicht-Akzessorisch (Abstrakt):** Besteht unabhängig von der Forderung. Flexibler als die Hypothek.
- Standard bei Immobilienfinanzierungen.
    

**C) Sicherungsübereignung**
- **Prinzip:** Kreditnehmer bleibt **Besitzer** (nutzt die Maschine), Bank wird **Eigentümer** (Sicherheit).
- **Raumsicherungsübereignung:** Übereignung aller Waren in einem bestimmten Lagerraum (für Umlaufvermögen/Vorräte). _Nachteil:_ Manipulationsanfällig $\rightarrow$ Hoher Risikoabschlag.
    

D) [[Covenants]] (Kreditklauseln)
Vertragliche Nebenabreden, bestimmte Kennzahlen (z.B. EK-Quote > 30%) einzuhalten. Bei Bruch (Breach) drohen Sanktionen (Zinserhöhung, Kündigung).

---

#### 4. Preiskalkulation (Der Nominalzins)

Wie setzt sich der Zins zusammen, den die Bank verlangt?

$$\text{Nominalzins} = \underbrace{\text{Refinanzierungszins}}_{\text{Kosten des Geldes}} + \underbrace{\text{Betriebskosten}}_{\text{Abwicklung}} + \underbrace{\text{Risikokosten}}_{\text{Risikoprämie}} + \underbrace{\text{Gewinnmarge}}_{\text{Profit}}$$

1. **Refinanzierung:** Was kostet es die Bank, sich das Geld zu beschaffen? (EZB-Leitzins, EURIBOR, Einlagenzins).
2. **Betriebskosten:** Personal, IT, Miete (Stückkosten pro Kredit).
3. **Risikokosten (Standard-Risikokosten):** Prämie für den erwarteten Verlust (Expected Loss) basierend auf dem Rating. Schlechte Bonität = Hoher Zuschlag.
4. **Gewinnmarge (Eigenkapitalkosten):** Verzinsung des Eigenkapitals der Bank.
    

---

#### Flashcards

Was ist der Zweck der Kapitaldienstfähigkeit? :: Sie misst, ob der operative Cashflow ausreicht, um die laufenden Zins- und Tilgungszahlungen zu decken.
<!--SR:!2025-12-17,1,222-->

Wie lautet die Formel für die Kapitaldienstfähigkeit?
?
$$\text{Kapitaldienstfähigkeit} = \frac{\text{Operativer Cash Flow}}{\text{Zinszahlungen} + \text{Tilgungszahlungen}}$$
<!--SR:!2025-12-17,1,230-->

Wie lautet die Formel für den dynamischen Verschuldungsgrad?
?
$$\text{Dynamischer Verschuldungsgrad}=\frac{\text{Finanzschulden}}{\text{Operativer Cash Flow}}$$
<!--SR:!2025-12-17,1,222-->

Welcher Wert wird als Obergrenze für den dynamischen Verschuldungsgrad angesehen? :: Maximal **7 Jahre** (Faustregel für die theoretische Entschuldungsdauer).
<!--SR:!2025-12-17,1,230-->

Was ist der entscheidende Unterschied zwischen einer gewöhnlichen und einer selbstschuldnerischen Bürgschaft? :: Bei der **gewöhnlichen** Bürgschaft muss die Bank erst beim Schuldner vollstrecken (Einrede der Vorausklage). Bei der **selbstschuldnerischen** kann sie sofort den Bürgen in Anspruch nehmen.
<!--SR:!2025-12-17,1,230-->

Warum bevorzugen Banken die Grundschuld gegenüber der Hypothek? :: Weil die Grundschuld **nicht-akzessorisch** (abstrakt) ist. Sie erlischt nicht automatisch mit der Tilgung und kann flexibel für neue Kredite wiederverwendet werden.
<!--SR:!2025-12-17,1,222-->

Wer ist bei einer Sicherungsübereignung Eigentümer der Sache? :: Die **Bank** (Sicherungsnehmer). Der Kreditnehmer bleibt nur Besitzer.
<!--SR:!2025-12-17,1,230-->

Aus welchen vier Komponenten setzt sich der Nominalzins einer Bank kalkulatorisch zusammen? :: Refinanzierungskosten, Betriebskosten, Risikokosten (Risikoprämie), Gewinnmarge.
<!--SR:!2025-12-17,1,222-->

Was passiert bei einem "Covenant Breach" (Verletzung von Kreditklauseln)? :: Die Bank erhält Sonderrechte: Zinserhöhung, Nachbesicherung oder Kündigung des Kredits.
<!--SR:!2025-12-17,1,230-->



---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Kreditprüfung]]
SORT file.mtime DESC
```