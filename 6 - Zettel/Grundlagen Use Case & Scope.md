#Note

2025-12-17

Tags: [[Software Engineering]], [[UseCases]]
#se

---
- **Definition Use Case:** Eine Menge von Aktivitäten (Szenario), die von einem Akteur ausgeführt werden, um ein bestimmtes Ergebnis (Ziel) von beobachtbarem Wert zu erreichen.
- **Akteure:** Rollen, die außerhalb des Systems liegen und mit diesem interagieren (Personen oder Nachbarsysteme/Maschinen).
    
- **Scope & Abgrenzung (Zwiebel-Modell):**
    - **Business Use Case (Geschäftsprozess):** Betrachtet das Unternehmen als "Black Box". Umfasst manuelle und IT-gestützte Schritte. Fokus: Wertschöpfung für das Unternehmen.

    - **Product Use Case (System-Use-Case):** Betrachtet das zu entwickelnde Software-System als "Black Box" (Systemgrenze). Fokus: Interaktion zwischen Akteur und Software.
    
- **Cockburn-Modell (Ebenen/Ziele):**
    - **Wolke/Drachen (Summary Level):** Zusammenfassende Ziele über mehrere Sitzungen oder Tage (High-Level).
    - **Meeresoberfläche (User Goal Level):** Das eigentliche Ziel, das ein Benutzer in einer Sitzung erreichen will ("Ich will jetzt...").
        - _Coffee Break Test:_ Ein User Goal UC sollte in einer Sitzung von 2 bis 20 Minuten erledigt sein (so lange wie eine Kaffeepause).
        
    - **Fische/Muscheln (Sub-Function Level):** Technische Teilschritte oder Unterfunktionen (z.B. "Logge dich ein"), die allein keinen direkten Business-Wert haben.
        

---
#### Flashcards

Was ist ein Akteur im Use-Case-Kontext? :: Eine Rolle (Person oder System) außerhalb der Systemgrenze, die mit dem System interagiert.

Was unterscheidet einen Business Use Case von einem Product Use Case? :: Business UC betrachtet den gesamten Geschäftsprozess (inkl. manueller Schritte); Product UC fokussiert sich rein auf das zu entwickelnde Softwaresystem.

Auf welcher Ebene des Cockburn-Modells liegt das klassische "User Goal"? :: Auf der Meeresoberfläche (Sea Level).

Was besagt der "Coffee Break Test" für Use Cases? :: Ein Use Case auf User-Goal-Ebene sollte idealerweise in einer Sitzung von 2 bis 20 Minuten (Kaffeepause) durchführbar sein.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Grundlagen Use Case & Scope]]
SORT file.mtime DESC
```