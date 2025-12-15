#Note

2025-12-15

Tags: [[Projektmanagement]], [[Agile]], [[Kanban]], [[Vorgehensmodelle]]
#pm

---
**Kanban** ("Signalkarte") ist eine Methode des evolutionären Change Managements, die auf dem **Pull-Prinzip** und der Begrenzung der parallelen Arbeit basiert. Ursprung: Toyota Produktionssystem (Lean).

#### 1. Die Stacey-Matrix: Wann welches Modell?

Die Wahl des Vorgehensmodells hängt vom Grad der Unsicherheit ab (Anforderungen vs. Technologie).
- **Einfach:** "Malen nach Zahlen" $\rightarrow$ Best Practices / Checklisten.
- **Kompliziert:** Ursache-Wirkung erkennbar, aber Experten nötig $\rightarrow$ **Wasserfall / V-Modell** (gute Planbarkeit).
- **Komplex:** Zusammenhänge erst im Rückblick klar, viele Unbekannte $\rightarrow$ **Scrum** (Empirie, "Probe-Sense-Respond").
- **Chaotisch:** Sofortiges Handeln nötig (Notfall) $\rightarrow$ **Kanban** / "Act-Sense-Respond" (Fokus auf Abarbeitung).

_(Hinweis: Kanban eignet sich auch hervorragend für "komplexe" Umfelder mit stetigem Arbeitsfluss, z.B. Wartung/Support, wo Sprints zu starr wären)._

#### 2. Kernpraktiken von Kanban

1. Visualisiere den Arbeitsfluss:
    Das Kanban-Board macht Arbeit sichtbar. Spalten zeigen den Prozess (z.B. To Do $\rightarrow$ Dev $\rightarrow$ Test $\rightarrow$ Done).
2. Limitiere die laufende Arbeit (Limit WiP):
    Jede Spalte hat ein Limit für gleichzeitige Tickets (Work in Progress).
    - _Ziel:_ "Stop starting, start finishing." Vermeidung von Multitasking und Staus.
    - _Effekt:_ Wenn das Limit voll ist, darf nichts Neues gezogen werden ("Pull"), bis etwas fertig ist.
        
3. Manage den Arbeitsfluss (Flow):
    Messung der Durchlaufzeit (Lead Time / Cycle Time). Engpässe (Bottlenecks) werden sofort sichtbar (dort stauen sich die Karten).
    
4. Mache Prozessregeln explizit:
    Wann darf ein Ticket in die nächste Spalte? (Definition of Done für jeden Schritt).
    

#### 3. Unterschied: Scrum vs. Kanban

|**Merkmal**|**Scrum**|**Kanban**|
|---|---|---|
|**Taktung**|Feste Taktung (**Sprints**, Timebox)|Kontinuierlicher Fluss (**Flow**)|
|**Rollen**|3 feste Rollen (PO, SM, Dev)|Keine vorgeschriebenen Rollen|
|**Änderungen**|Im laufenden Sprint nicht erlaubt|Jederzeit möglich (sofern Kapazität frei)|
|**Commitment**|Team committet auf Sprint-Ziel|Commitment auf Service-Level (Durchlaufzeit)|
|**Reset**|Board wird nach jedem Sprint geleert|Board läuft endlos weiter|

---
#### Flashcards

Wofür steht WiP in Kanban? :: **Work in Progress** (Laufende Arbeit).

Warum limitiert man den WiP? :: Um **Multitasking** zu verhindern und Staus (Bottlenecks) sofort sichtbar zu machen ("Stop starting, start finishing").

Welches Prinzip gilt in Kanban für die Arbeitsaufnahme: Push oder Pull? :: **Pull** (Arbeit wird gezogen, wenn Platz ist).

Wann ist Kanban besonders geeignet (im Vergleich zu Scrum)? :: Bei Aufgaben mit **kontinuierlichem Eingang** (z.B. Support, Wartung) oder wenn Flexibilität wichtiger ist als Planungssicherheit.

Welche Methode empfiehlt die Stacey-Matrix für "chaotische" Situationen? :: Einfaches Handeln ("Act-Sense-Respond"), oft unterstützt durch Kanban-Boards zur Übersicht.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Kanban]]
SORT file.mtime DESC
```