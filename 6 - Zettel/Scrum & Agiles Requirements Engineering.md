#Note

2025-12-17

Tags: [[Software Engineering]], [[Scrum]]
#se

---
- **Der Scrum-Prozess:**
    - **Rollen:** **Product Owner** (verantwortlich für "Was"), **Scrum Master** (verantwortlich für den Prozess/Hindernisse), **Entwicklungsteam** (verantwortlich für "Wie").
    - **Events:** Sprint Planning (Planung), Daily Scrum (täglicher Abgleich), Sprint Review (Abnahme des Inkrements), Sprint Retrospective (Prozessverbesserung).
    - **Artefakte:** Product Backlog (Priorisierte Liste aller Anforderungen), Sprint Backlog (Plan für den aktuellen Sprint), Inkrement (lauffähige Software am Ende des Sprints).
        
- **Anforderungsarten:**
    - **Epic:** Eine große, übergeordnete Anforderung, die zu umfangreich ist, um innerhalb eines Sprints umgesetzt zu werden. Sie dient als Container für detailliertere User Stories.
    
    - **User Story (US):** Eine kurze funktionale Anforderungsbeschreibung aus Benutzersicht.
        - _Schablone:_ "Als *Rolle* will ich *Ziel/Aktion*, sodass *Nutzen*".
        - _Größe:_ Sollte in einer Iteration (1-5 Tage) umsetzbar sein.
        
- **Qualitätskriterien:**
    
    - **INVEST (für User Stories):**
        - **I**ndependent (Unabhängig)
        - **N**egotiable (Verhandelbar)
        - **V**aluable (Wertvoll für den Kunden)
        - **E**stimatable (Schätzbar)
        - **S**mall (Klein genug für einen Sprint)
        - **T**estable (Testbar)
            
    - **DoR (Definition of Ready):** Kriterienkatalog, wann eine User Story bereit ist, in den Sprint _aufgenommen_ zu werden (Input-Qualität). Beispiele: Klar beschrieben, geschätzt, keine offenen Abhängigkeiten.
        
    - **DoD (Definition of Done):** Kriterienkatalog, wann eine User Story als _fertig_ gilt (Output-Qualität). Beispiele: Code geschrieben, Unit-Tests bestanden, Dokumentation aktualisiert.
        

---

#### Flashcards

Wofür steht das Akronym INVEST bei User Stories? :: Independent, Negotiable, Valuable, Estimatable, Small, Testable.

Was ist der Unterschied zwischen Definition of Ready (DoR) und Definition of Done (DoD)? :: DoR prüft, ob eine Aufgabe bereit für den Start (Sprint-Aufnahme) ist; DoD prüft, ob eine Aufgabe vollständig abgeschlossen ist (Qualitätssicherung am Ende).

Wie lautet die Standardschablone für eine User Story? :: Als *Rolle* will ich *Ziel*, sodass *Nutzen*.

Was ist ein Epic in der agilen Entwicklung? :: Eine große Anforderung, die zu umfangreich für einen einzelnen Sprint ist und in kleinere User Stories zerlegt werden muss.


---

### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Scrum & Agiles Requirements Engineering]]
SORT file.mtime DESC
```