#Note

2025-12-17

Tags: [[]], [[]], [[]]
#se

---
- **Ziel:** Übersichtlichkeit erhöhen, ohne die Logik zu verändern.
    
- **Regel:** Zwei Regeln können zusammengefasst werden, wenn sie:
    
    1. Zu den **gleichen Aktionen** führen UND
        
    2. Sich nur in **einer einzigen Bedingung** unterscheiden.
        
- **Ergebnis:** Die irrelevante Bedingung wird als "Don't Care" (z.B. mit einem Strich "–") markiert. Das bedeutet: Egal ob Ja oder Nein, das Ergebnis bleibt gleich.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Konsolidierung]]
SORT file.mtime DESC
```