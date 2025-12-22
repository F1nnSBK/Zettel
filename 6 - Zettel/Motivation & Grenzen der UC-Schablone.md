#Note

2025-12-17

Tags: [[Software Engineering]], [[BPMN 2.0]]
#se

---
- **Das Sequenz-Problem:**
    - Textuelle Use-Case-Schablonen suggerieren durch die Nummerierung der Schritte (1., 2., 3., ...) oft eine strikte, zeitliche Reihenfolge (Sequenz) der Abarbeitung.
    - In der Realität können viele Schritte jedoch unabhängig voneinander, parallel oder in flexibler Reihenfolge ablaufen (z.B. können "Lieferbarkeit prüfen" und "Rechnung erstellen" oft gleichzeitig passieren).
        
- **Lösung:**
    - Grafische Diagramme wie **Aktivitätsdiagramme (AD)** oder **BPMN** (Business Process Model and Notation) werden genutzt, um diese Logik korrekt abzubilden.
    - Sie visualisieren explizit **Nebenläufigkeiten (Parallelität)**, komplexe Verzweigungen und Zusammenführungen, die im reinen Text untergehen oder missverständlich sind.
        
- **Kontext:**
    - Dies ist der Schritt "Formal modellieren" im RE-Vorgehensmodell, der auf die textuelle Spezifikation folgt, um Präzision zu schaffen.
        

---
#### Flashcards

Was ist der Hauptnachteil rein textueller Use-Case-Schablonen in Bezug auf den Ablauf? :: Sie suggerieren oft eine strikte sequenzielle Reihenfolge, obwohl Schritte real parallel oder optional sein könnten.

Welche Diagrammarten lösen das Sequenz-Problem der Use Cases? :: Aktivitätsdiagramme (UML) oder BPMN (Business Process Model and Notation).

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Motivation & Grenzen der UC-Schablone]]
SORT file.mtime DESC
```