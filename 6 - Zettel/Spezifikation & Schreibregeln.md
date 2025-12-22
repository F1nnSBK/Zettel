#Note

2025-12-17

Tags: [[Software Engineering]], [[UseCases]]
#se

---
- **Use Case Template:** Ein standardisiertes Formular zur Erfassung. Wichtige Felder:
    - **Name:** Verb + Objekt (z.B. "Geld abheben").
    - **Ziel:** Was soll erreicht werden?
    - **Auslösendes Ereignis (Trigger):** Was startet den Use Case?
    - **Akteure:** Primäre und sekundäre Akteure.
    - **Vorbedingung:** Was muss _vor_ dem Start erfüllt sein (z.B. "Benutzer ist eingeloggt")?
    - **Nachbedingung:** Zustand _nach_ dem Ablauf (Erfolg: "Geld ausgezahlt"; Fehlschlag: "Fehlermeldung angezeigt").
    - **Ablauf:** Die eigentlichen Schritte.
        
- **Ablauf-Struktur:**
    - **Standardablauf (Happy Path):** Der ideale Weg ohne Fehler zum Ziel.
    - **Erweiterungen/Alternativen:** Abweichungen vom Standardweg (z.B. "PIN falsch", "Karte gesperrt", "Konto nicht gedeckt"). Diese werden oft unter dem Standardablauf oder an "Extension Points" referenziert.
        
- **Regeln für "Gute" Use Cases (Best Practices nach Cockburn):**
    - **Grammatik:** Sätze im **Subjekt-Verb-Objekt**-Stil schreiben (z.B. "Der Kunde gibt die PIN ein"). Aktiv statt Passiv verwenden.
    - **Perspektive ("Who has the ball?"):** Es muss immer klar sein, wer gerade handelt (Akteur oder System).
    - **Essenz:** Fokus auf die _Absicht_ des Akteurs, nicht auf technische Details oder GUI-Elemente.
        - _Schlecht:_ "Der Benutzer klickt auf den OK-Button."
        - _Gut:_ "Der Benutzer bestätigt die Eingabe."
            
    - **Validieren statt Prüfen:** Ergebnisorientiert schreiben.
        - _Schlecht:_ "Das System prüft die PIN." (Was passiert danach?)
        - _Gut:_ "Das System validiert die PIN." (Impliziert: Prüfung + Entscheidung über Erfolg/Misserfolg).
        
---
#### Flashcards

Welche grammatikalische Struktur sollte ein Schritt in einem Use Case haben? :: Subjekt - Verb - Objekt (z.B. "Der Kunde bestätigt den Auftrag").
<!--SR:!2025-12-21,1,230-->

Was bedeutet die Regel "Essenz" beim Schreiben von Use Cases? :: Man soll die Absicht beschreiben, nicht die technische Umsetzung oder GUI-Details (kein "Klicke Button", sondern "Bestätige Eingabe").
<!--SR:!2025-12-21,1,230-->

Warum sollte man "validieren" statt "prüfen" schreiben? :: "Validieren" ist ergebnisorientiert (impliziert Prüfung und Ergebnis), während "Prüfen" nur die Tätigkeit beschreibt.
<!--SR:!2025-12-21,1,230-->

Was gehört in die Nachbedingung eines Use Cases? :: Der Zustand des Systems nach Beendigung des Use Cases (sowohl für den Erfolgsfall als auch für Fehlerfälle).
<!--SR:!2025-12-21,1,230-->

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Spezifikation & Schreibregeln]]
SORT file.mtime DESC
```