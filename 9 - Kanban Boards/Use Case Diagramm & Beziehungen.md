#Note

2025-12-17

Tags: [[]], [[]], [[]]
#se

---
- **Notation:** Akteure (Strichmännchen), System (Rechteck/Grenze), Use Cases (Ovale), Kommunikation (Linien) .
    
- **Beziehungen:**
    
    - **`<<include>>`:** Wiederverwendung. UC A _benötigt_ UC B zwingend (wie Unterprogramm). B weiß nicht, wer ihn aufruft .
        
    - **`<<extend>>`:** Optionale Erweiterung. UC B erweitert UC A unter Bedingung (Extension Point). A weiß theoretisch nichts von B (lose Kopplung) .

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Use Case Diagramm & Beziehungen]]
SORT file.mtime DESC
```