#Note

2025-12-17

Tags: [[]], [[]], [[]]
#se

---
- **Standardablauf $\rightarrow$ Sequenzfluss:** Die nummerierten Schritte im UC ("1. Kunde gibt Daten ein") werden zu Tasks, verbunden mit Pfeilen.
    
- **Alternativen/Fehlschläge $\rightarrow$ XOR-Gateways:**
    
    - _Text:_ "2a. Wenn Daten ungültig, dann..."
        
    - _BPMN:_ XOR-Gateway nach der Prüfung. Ein Pfad "gültig" (weiter im Text), ein Pfad "ungültig" (zum Fehler-Event oder Abbruch) 18.
        
- **Parallele Schritte $\rightarrow$ AND-Gateways:** Wenn im UC steht "Gleichzeitig wird X und Y gemacht", nutzt du das Plus-Gateway.
    
- **Akteure $\rightarrow$ Lanes:** Jeder Akteur aus dem UC-Kopf (z.B. "Kunde", "System") bekommt eine eigene Lane (Schwimmbahn). Nachrichten zwischen ihnen sind Sequenzflüsse (innerhalb eines Pools).

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Transformation UC -> BPMN]]
SORT file.mtime DESC
```