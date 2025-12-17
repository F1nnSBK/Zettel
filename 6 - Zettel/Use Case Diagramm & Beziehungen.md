#Note

2025-12-17

Tags: [[Software Engineering]], [[UseCases]]
#se

---
- **Notation:**
    - **Akteure:** Werden als "Strichmännchen" dargestellt und repräsentieren Rollen außerhalb des Systems.
    - **System:** Wird als Rechteck (Systemgrenze) dargestellt, das die Use Cases umschließt.
    - **Use Cases:** Werden als Ovale innerhalb der Systemgrenze gezeichnet.
    - **Kommunikation:** Durchgezogene Linien (Assoziationen) verbinden Akteure mit Use Cases.
        
- **Beziehungen:**
    - **`<<include>>` (Einschluss):**
        - Beschreibt eine **zwingende** Wiederverwendung. Der Basis-UC _benötigt_ den inkludierten UC zwingend, um ausgeführt zu werden (vergleichbar mit einem Funktionsaufruf).
            
        - Der inkludierte UC weiß nicht, wer ihn aufruft. Dient der Vermeidung von Redundanz.
            
    - **`<<extend>>` (Erweiterung):**
        - Beschreibt eine **optionale** Erweiterung. Der erweiternde UC fügt sein Verhalten nur unter bestimmten Bedingungen an einem definierten **Extension Point** in den Basis-UC ein.
            
        - Der Basis-UC weiß nichts von der Erweiterung (lose Kopplung), was das System flexibler macht.
            

---
#### Flashcards

Wie wird ein Akteur im Use-Case-Diagramm grafisch dargestellt? :: Als Strichmännchen.

Was ist der zentrale Unterschied zwischen `<<include>>` und `<<extend>>`? 
?
`<<include>>` ist zwingend erforderlich (der Basis-UC braucht es); `<<extend>>` ist optional (passiert nur unter Bedingungen).

Wer kennt wen bei einer `<<extend>>`-Beziehung? :: Der erweiternde UC kennt den Basis-UC; der Basis-UC weiß nichts von der Erweiterung (lose Kopplung).

Wozu dienen `<<include>>`-Beziehungen hauptsächlich? :: Zur Wiederverwendung von Funktionalität (Vermeidung von Redundanz) in mehreren Use Cases.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Use Case Diagramm & Beziehungen]]
SORT file.mtime DESC
```