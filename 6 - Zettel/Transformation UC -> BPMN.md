#Note

2025-12-17

Tags: [[Software Engineering]], [[BPMN]]
#se

---
- **Standardablauf $\rightarrow$ Sequenzfluss:**
    - Die nummerierten Schritte im Use Case (z.B. "1. Kunde gibt Daten ein") werden in BPMN zu **Tasks** (Aktivitäten).
    - Diese werden mit Pfeilen (Sequenzfluss) in der Reihenfolge verbunden, wie sie im Text stehen.
        
- **Alternativen/Fehlschläge $\rightarrow$ XOR-Gateways:**
    - _Im Text:_ Erweiterungen oder alternative Abläufe wie "2a. Wenn Daten ungültig, dann..." oder "3a. Wenn Ware nicht lieferbar...".
        
    - _In BPMN:_ Ein **XOR-Gateway** (Raute mit X) nach dem prüfenden Task.
        - Ein Pfad führt weiter im Standardablauf ("gültig").
        - Ein zweiter Pfad zweigt ab zur Fehlerbehandlung oder zum Abbruch ("ungültig").
        
- **Parallele Schritte $\rightarrow$ AND-Gateways:**
    - _Im Text:_ Formulierungen wie "Gleichzeitig wird X und Y gemacht" oder "Parallel dazu...".

    - _In BPMN:_ Ein **AND-Gateway** (Raute mit +) teilt den Pfad auf. Beide Zweige müssen später oft wieder mit einem AND-Gateway zusammengeführt (synchronisiert) werden.
    
- **Akteure $\rightarrow$ Lanes:**
    - Jeder Akteur, der im Use Case (Kopfdaten oder Text) genannt wird (z.B. "Kunde", "System", "Sachbearbeiter"), erhält eine eigene **Lane** (Schwimmbahn) innerhalb des Pools.

    - Der Sequenzfluss wechselt die Lane, wenn die Zuständigkeit im Ablauf wechselt ("Ping-Pong-Spiel").
    

---
#### Flashcards

Wie wird eine Entscheidung ("Wenn X, dann Y, sonst Z") aus einem Use Case in BPMN dargestellt?
?
Mit einem XOR-Gateway (Exklusives ODER).

Was passiert mit den Akteuren eines Use Cases bei der Transformation in BPMN?
?
Jeder Akteur bekommt eine eigene Lane (Schwimmbahn) im BPMN-Diagramm.

Wie stellt man parallele Schritte ("Gleichzeitig...") in BPMN dar?
?
Mit einem AND-Gateway (Parallel Gateway, "+").

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Transformation UC -> BPMN]]
SORT file.mtime DESC
```