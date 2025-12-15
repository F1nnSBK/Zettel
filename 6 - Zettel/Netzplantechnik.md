#Note

2025-12-15

Tags: [[Projektmanagement]], [[Terminplanung]], [[Netzplan]], [[Kritischer Pfad]]
#pm

---
Die **Netzplantechnik** (Critical Path Method - CPM) ist das zentrale Tool zur Terminplanung. Sie visualisiert logische Abhängigkeiten und berechnet Pufferzeiten.

#### 1. Der Vorgangsknoten (Node)
Die Darstellung erfolgt als "Knoten" mit definierten Feldern für die Zeitwerte.

|**FAZ / ES**|**Dauer / D**|**FEZ / EF**|
|---|---|---|
|**GP / TF**|**Name**|**FP / FF**|
|**SAZ / LS**|**GP / TF**|**SEZ / LF**|

**Legende (Deutsch / Englisch):**
- **FAZ / ES:** Frühester Anfangszeitpunkt (_Early Start_)
- **FEZ / EF:** Frühester Endzeitpunkt (_Early Finish_)
- **SAZ / LS:** Spätester Anfangszeitpunkt (_Late Start_)
- **SEZ / LF:** Spätester Endzeitpunkt (_Late Finish_)
- **GP / TF:** Gesamtpuffer (_Total Float_)
- **FP / FF:** Freier Puffer (_Free Float_)

#### 2. Berechnungsschritte (Der Weg durch das Netz)

**A) Vorwärtsrechnung (Forward Pass)** $\rightarrow$ Ermittelt die _früheste_ Lage.
- **Start:** Bei $t=0$ (oder 1).
- **Formel:** $ES + Dauer = EF$ (bzw. $ES + D - 1$ je nach Zählweise*).
- **Konvergenz (Zusammenführung):** Hat ein Vorgang mehrere Vorgänger, bestimmt der **späteste** (höchste) EF-Wert den ES des Nachfolgers.
    - _Regel:_ "Man kann erst anfangen, wenn ALLE Vorgänger fertig sind."
        

**B) Rückwärtsrechnung (Backward Pass)** $\rightarrow$ Ermittelt die _späteste_ Lage.
- **Start:** Vom Projektende her (LF des letzten Vorgangs = EF).
- **Formel:** $LF - Dauer = LS$.
- **Divergenz (Verzweigung):** Hat ein Vorgang mehrere Nachfolger, bestimmt der **früheste** (niedrigste) LS-Wert den LF des Vorgängers.
    
    - _Regel:_ "Man muss so fertig sein, dass der DRINGENDSTE Nachfolger nicht warten muss."
        

**C) Puffer & Kritischer Pfad**
- **Gesamtpuffer (Total Float):** $LF - EF$ (oder $LS - ES$). Zeit, die man trödeln kann, ohne das **Projektende** zu verschieben.
- **Freier Puffer (Free Float):** Zeit, die man trödeln kann, ohne den **frühesten Start des Nachfolgers** zu verschieben.
- **Kritischer Pfad:** Die Kette von Vorgängen mit **Puffer = 0**.
    - Bestimmt die **Mindestdauer** des Projekts.
    - Verzögerungen hier schlagen sofort auf den Endtermin durch.
    
#### 3. Anordnungsbeziehungen (AOB)

Die logische Verknüpfung zwischen zwei Vorgängen (Vorgänger $\rightarrow$ Nachfolger).
- **Ende-Anfang (Finish-to-Start - FS):** Standard. B startet, wenn A fertig ist.
- **Anfang-Anfang (Start-to-Start - SS):** B startet, wenn A startet.
- **Ende-Ende (Finish-to-Finish - FF):** B ist fertig, wenn A fertig ist.
- **Anfang-Ende (Start-to-Finish - SF):** B ist fertig, wenn A startet (selten).
    

---
#### Flashcards

Wofür steht **ES** im Netzplan? :: Early Start (Frühester Anfang).

Wofür steht **LF** im Netzplan? :: Late Finish (Spätestes Ende).

Wie berechnet man den Gesamtpuffer (Total Float)? :: $LF - EF$ (Spätes Ende minus Frühes Ende).

Welchen Wert wählt man bei der Vorwärtsrechnung, wenn mehrere Pfade zusammenlaufen? :: Den **höchsten** (Maximum) der EF-Werte der Vorgänger.

Welchen Wert wählt man bei der Rückwärtsrechnung, wenn sich ein Pfad aufteilt? :: Den **niedrigsten** (Minimum) der LS-Werte der Nachfolger.

Was ist der Unterschied zwischen Gesamtpuffer und Freiem Puffer? :: Gesamtpuffer schützt den **Projektendtermin**, Freier Puffer schützt den **frühesten Start des Nachfolgers**.



---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Netzplantechnik]]
SORT file.mtime DESC
```