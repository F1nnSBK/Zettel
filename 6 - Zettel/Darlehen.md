#Note

2025-12-11

Tags: [[Grundlagen Finanzierung & Investition]], [[Fremdkapital]], [[Fremdkapitalfinanzierung]], [[Darlehen]]
#finance

---
Ein **Darlehen** ist ein schuldrechtlicher Vertrag, bei dem ein Kreditgeber (Gläubiger) einem Kreditnehmer (Schuldner) Geld oder Sachwerte vorübergehend gegen Entgelt (Zinsen) zur Nutzung überlässt.

- **Darlehen:** Meist langfristige Ausleihungen (> 4 Jahre).
- **Kredit:** Oft als Oberbegriff oder für kurzfristige Ausleihungen genutzt.
#### 1. Grundbegriffe

- **Nominalwert:** Der tatsächlich geliehene Betrag (Schuldbetrag), der zurückgezahlt werden muss (z.B. 200.000 €).
- **Nominalzins (Sollzins):** Der auf den Nominalwert bezogene Zinssatz p.a. (per annum).
- **Effektivzins:** Die tatsächlichen Gesamtkosten des Kredits (inkl. Gebühren, Disagio, Tilgungsverrechnung). Er ist die wichtigste Vergleichsgröße.
- **Tilgung:** Die Rückzahlung der Kreditsumme (reduziert die Restschuld).
- **Kapitaldienst:** Die Summe aus Zins und Tilgung pro Periode.
    

---
#### 2. Tilgungsstrukturen
Die Art der Rückzahlung bestimmt den Liquiditätsabfluss.

A) Endfälliges Darlehen (Bullet Loan)
Während der Laufzeit werden nur Zinsen gezahlt. Die komplette Tilgung erfolgt am Ende.
- Jährliche Zahlung: $Zins = C_0 \cdot i$
- Zahlung in $t=n$: $C_0 + (C_0 \cdot i)$

- _Eignung:_ Wenn Rückflüsse aus der Investition erst am Ende anfallen.
    

B) Null-Kupon-Darlehen (Zero Bond)
Keine laufenden Zinszahlungen. Die Zinsen werden angesammelt (thesauriert) und zusammen mit der Tilgung am Ende gezahlt.

- Rückzahlung in $t=n$: $C_n = C_0 \cdot (1+i)^n$

- _Bilanzierung:_ Zinsaufwand muss trotzdem jährlich in der GuV erfasst werden (Aufzinsung der Verbindlichkeit), obwohl kein Cashflow fließt.
- _Eignung:_ Startups/Wachstumsunternehmen (Schonung der Liquidität).
    

C) Annuitätendarlehen
Die jährliche Zahlung (Annuität) bleibt über die gesamte Laufzeit konstant.
Da die Restschuld sinkt, sinkt der Zinsanteil, und der Tilgungsanteil steigt progressiv.

$$Annuität = C_0 \cdot ANF(i, n) = C_0 \cdot \frac{(1+i)^n \cdot i}{(1+i)^n -1}$$

- _Eignung:_ Immobilienfinanzierung (Planbarkeit).
![[8 - Media/Bilder/Annuität.jpeg]]

---
#### 3. Zinsarten
- **Fixer Zins:** Festschreibung über die Laufzeit (Planungssicherheit, aber kein Profitieren von Zinssenkungen).
    
- **Variabler Zins:** Anpassung an einen Referenzzinssatz in bestimmten Perioden (Zinsänderungsrisiko).
    - **EURIBOR:** (Euro Interbank Offered Rate): Zinssatz, zu dem sich europäische Banken untereinander Geld leihen.
    - **LIBOR:** (London Interbank Offered Rate): _Historisch relevant, wurde weitgehend abgelöst._
        
- **Partiarischer Zins:** Erfolgsabhängige Vergütung (Zins + Gewinnbeteiligung). Gläubiger trägt ein höheres Risiko $\rightarrow$ "Mezzanine-Kapital".
- **Angepasster Zins (Staffelzins):** Vertraglich fixierte Stufen (z.B. "Teaser-Zinsen" am Anfang niedrig, später hoch).
    

---
#### 4. Kreditsicherheiten
Sicherheiten reduzieren das Ausfallrisiko (Loss Given Default) für die Bank und senken so den Zins.

**A) Nach Rangposition ([[Insolvenz]])**
1. **Vorrangiges Darlehen (Senior Debt):** Wird im [[Insolvenzfall]] als Erstes bedient.
2. **Nachrangdarlehen (Junior/Subordinated Debt):** Wird erst bedient, wenn alle vorrangigen Gläubiger befriedigt sind (dafür höherer Zins).
    

**B) Nach Art der Sicherheit**

|**Kriterium**|**Personalsicherheiten**|**Realsicherheiten (Sachsicherheiten)**|
|---|---|---|
|**Gegenstand**|Eine weitere **Person** haftet mit ihrem Vermögen.|Ein **Sachwert** (Immobilie, Maschine) dient als Haftung.|
|**Beispiele**|• **Bürgschaft**<br><br>  <br><br>• Garantie<br><br>  <br><br>• Patronatserklärung|• **Grundpfandrechte** (Hypothek, Grundschuld)<br><br>  <br><br>• **Sicherungsübereignung** (bewegl. Sachen)<br><br>  <br><br>• **Zession** (Forderungsabtretung)|

**C) Nach Abhängigkeit zur Forderung**

- Akzessorisch (Streng abhängig):
    Die Sicherheit ist fest an das Bestehen der Forderung gekoppelt. Ist der Kredit getilgt, erlischt die Sicherheit automatisch.
    - _Beispiele:_ **Bürgschaft**, **Hypothek**, Pfandrecht.
        
- Nicht-Akzessorisch (Fiduziarisch / Abstrakt):
    Die Sicherheit besteht rechtlich unabhängig von der Forderung weiter (muss nach Tilgung aktiv zurückgegeben werden). Flexibler handhabbar.
    - _Beispiele:_ **Grundschuld** (Standard bei Immo-Finanzierung!), **Sicherungsübereignung**, Sicherungsabtretung.


---
#### Flashcards

Was ist ein Darlehen rechtlich gesehen? :: Ein schuldrechtlicher Vertrag, bei dem Kapital oder Sachen auf Zeit gegen Entgelt (Zins) überlassen werden.

Was ist der Unterschied zwischen Nominalzins und Effektivzins? :: Der **Nominalzins** ist die Basis für die Zinsberechnung p.a., der **Effektivzins** beinhaltet alle Nebenkosten (Gebühren, Disagio) und dient als Vergleichsgröße.

Was versteht man unter dem Kapitaldienst? :: Die Summe aus **Zins** und **Tilgung**, die pro Periode an den Kreditgeber zu zahlen ist.

Wie verläuft der Zahlungsstrom beim "Endfälligen Darlehen" (Bullet Loan)? :: Während der Laufzeit werden nur Zinsen gezahlt; die gesamte Tilgung erfolgt in einer Summe am Laufzeitende.

Wie verläuft der Zahlungsstrom beim "Null-Kupon-Darlehen" (Zero Bond)? :: Es gibt keine laufenden Zahlungen. Zinsen werden angesammelt (thesauriert) und am Ende zusammen mit der Tilgung gezahlt.

Was ist das Kennzeichen eines Annuitätendarlehens? :: Die jährliche Rate (Annuität) ist konstant. Der Zinsanteil sinkt, der **Tilgungsanteil steigt** über die Laufzeit.

Wie lautet die Formel für den Annuitätenfaktor (ANF)?
?
$$ANF(i, n) = \frac{(1+i)^n \cdot i}{(1+i)^n -1}$$

Was ist ein partiarisches Darlehen? :: Ein Darlehen, bei dem der Zins vom Erfolg (z.B. Gewinn oder Umsatz) des Unternehmens abhängt (Gewinnbeteiligung).

Wofür steht die Abkürzung EURIBOR? :: Euro Interbank Offered Rate (Zinssatz, zu dem sich Banken untereinander Geld leihen; Referenz für variable Kredite).

Was ist eine **akzessorische** Sicherheit? :: Eine Sicherheit, die rechtlich zwingend vom Bestehen der Forderung abhängt (z.B. Bürgschaft, Hypothek). Ist der Kredit getilgt, erlischt die Sicherheit.

Was ist eine **fiduziarische** (nicht-akzessorische) Sicherheit? :: Eine Sicherheit, die rechtlich abstrakt/unabhängig von der Forderung besteht (z.B. Grundschuld, Sicherungsübereignung).

Was ist der Unterschied zwischen Hypothek und Grundschuld? :: Die **Hypothek** ist akzessorisch (an den Kredit gebunden), die **Grundschuld** ist nicht-akzessorisch (bleibt auch nach Tilgung bestehen, flexibler).

Wer ist bei einer Sicherungsübereignung Eigentümer und wer Besitzer der Sache? :: Der Kreditgeber (Bank) wird **Eigentümer** (Sicherheit), der Kreditnehmer bleibt **Besitzer** (nutzt die Maschine weiter).

Wer wird im Insolvenzfall zuerst bedient: Vorrangige oder nachrangige Gläubiger? :: Die **vorrangigen** Gläubiger (Senior Debt). Nachrangige (Mezzanine) erhalten erst Geld, wenn alle Vorrangigen befriedigt sind.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Darlehen]]
SORT file.mtime DESC
```