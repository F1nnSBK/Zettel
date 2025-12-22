#Note

2025-12-17

Tags: [[Software Engineering]], [[Phasen]]
#se

---
- **Einsatz in Prozessmodellen:** Methoden werden spezifischen Phasen im Softwarelebenszyklus zugeordnet:
    - **Analyse:** Hier dominieren problemorientierte Methoden wie Funktionsbaum, Geschäftsprozessmodellierung, Datenflussdiagramm (DFD), Entity Relationship Modell (ERM) und Klassendiagramme.
    - **Entwurf:** Hier kommen lösungsorientierte Methoden zum Einsatz, z.B. Klassendiagramme (verfeinert), Sequenzdiagramme und Zustandsautomaten.
    - **Implementierung (Feinentwurf):** Hier werden algorithmus-nahe Methoden genutzt, wie Struktogramme, Programmablaufpläne (PAP) und Pseudocode.
        
- **Semantische Lücke (Semantic Gap):**
    - Beschreibt das Problem, wenn Ergebnisse einer Phase (z.B. Analyse) nicht nahtlos in die nächste Phase (z.B. Entwurf) übertragen werden können, weil die verwendeten Methoden oder Notationen inkompatibel sind (Medienbruch).
    - _Beispiel:_ Die Strukturierte Analyse (SA) eignet sich gut für die Anforderungsdefinition, ihre Ergebnisse lassen sich aber oft schwer direkt in einen objektorientierten Systementwurf (SD) oder Code überführen.

---
#### Flashcards

In welcher Phase wird typischerweise ein Funktionsbaum erstellt? :: Analyse.
<!--SR:!2025-12-23,1,230-->

Für welche Phase eignen sich Struktogramme und Pseudocode am besten? :: Implementierung (bzw. Feinentwurf).

Was beschreibt die "Semantische Lücke" (Semantic Gap)? :: Das Problem, wenn Ergebnisse einer Phase (z.B. Analyse) methodisch nicht nahtlos in die nächste Phase (z.B. Entwurf) übertragbar sind (z.B. SA zu SD).


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Phasen und Methodeneinsatz]]
SORT file.mtime DESC
```