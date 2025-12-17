#Note

2025-12-17

Tags: [[Software Engineering]], [[Requirements Engineering]]
#se

---
- **Das RE-Vorgehensmodell:**
    - Besteht aus 4 aufeinanderfolgenden Tätigkeiten:

    1. **Identifizieren:** Quellen finden, Ereignisliste erstellen.
    2. **Abgrenzen:** Systemgrenze ziehen (Was gehört dazu, was nicht?), Business Use Cases definieren.
    3. **Spezifizieren:** Detaillierte Beschreibung der Anforderungen (Produktdomäne).
    4. **Formal modellieren:** Umsetzung in Diagramme (z.B. UML).
    
- **Zerlegung von Anforderungen (Input/Output):**
    - **Problemdomäne (Verstehen):** Fokus auf Geschäftsprozesse und Ereignisse (Business Use Cases).
    
    - **Produktdomäne (Lösung):**
        - **Funktionale Anforderungen (FA):** Was _tut_ das System? Beschreibt das Verhalten/Funktionen (Hauptfokus von Use Cases).
        - **Nicht-funktionale Anforderungen (NFA):** Qualitätsmerkmale (Performance, Sicherheit, Usability). Diese sind meist _nicht_ direkt im UC-Diagramm sichtbar, sondern werden textuell oder als Randbedingungen erfasst.
        - **Rahmenbedingungen:** Externe Vorgaben, die nicht verhandelbar sind (z.B. Gesetze, Budget, technische Standards, Hardware-Vorgaben).
            
- **Abgrenzungsmethoden:**
    - **SA-Kontextdiagramm:** (Älter) Methode der Strukturierten Analyse. Zeigt Datenflüsse über die Systemgrenze.
    
    - **Use-Case-Diagramm:** (Aktuell) Standard der UML. Zeigt Akteure außerhalb und Anwendungsfälle innerhalb der Systemgrenze.
    
![[uc-diagram.png]]


---
#### Flashcards

Nenne die 4 Schritte des RE-Vorgehensmodells in der richtigen Reihenfolge.
?
Identifizieren $\rightarrow$ Abgrenzen $\rightarrow$ Spezifizieren $\rightarrow$ Formal modellieren.

Was ist der Unterschied zwischen funktionalen und nicht-funktionalen Anforderungen?
?
Funktionale Anforderungen beschreiben, was das System tut (Verhalten); Nicht-funktionale Anforderungen beschreiben wie gut es das tut (Qualität/Performance).

Welche zwei Diagrammarten eignen sich zur Systemabgrenzung?
?
SA-Kontextdiagramm (alt) und Use-Case-Diagramm (aktuell/UML).


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[RE-Vorgehen & Anforderungsarten]]
SORT file.mtime DESC
```