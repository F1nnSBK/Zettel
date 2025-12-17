#Note

2025-12-17

Tags: [[]], [[]], [[]]
#se

---
- **Unterschied zu UML:** Fokus auf fachliche Prozesse, "elegantere Lösung", aber kein UML-Standard .
    
- **Kern-Elemente:**
    
    - **Events:** Start (Kreis), Ende (dicker Kreis), Zwischenereignis (Doppelkreis, z.B. Timer/Zeit) .
        
    - **Activities:** Aufgabe (Task, eckiges Rechteck).
        
    - **Container:** Pools (Ganze Organisation) und Lanes (Abteilungen/Rollen) .
        
    - **Daten:** Datenobjekt (Dokument-Icon) & Datenspeicher (Tonne) .
        
- **Gateways (Verzweigungen):**
    
    - **Exklusives ODER (X):** Genau ein Pfad wird gewählt .
        
    - **Paralleles UND (+):** Alle Pfade werden gleichzeitig ausgeführt.
        
    - **Inklusives ODER (O):** Einer oder mehrere Pfade möglich.





---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[BPMN 2.0]]
SORT file.mtime DESC
```