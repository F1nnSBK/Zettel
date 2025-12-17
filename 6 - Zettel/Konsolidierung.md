#Note

2025-12-17

Tags: [[Software Engineering]], [[Entscheidungstabelle]]
#se

---
- **Ziel:** Die Übersichtlichkeit der Entscheidungstabelle erhöhen und Redundanz vermeiden, ohne die logische Aussage zu verändern.
    
- **Regel:** Zwei Regeln (Spalten) können zu einer einzigen Regel zusammengefasst werden, wenn zwei Voraussetzungen erfüllt sind:
    
    1. Sie führen zu exakt den **gleichen Aktionen** (identische Aktionsmarkierungen).
        
    2. Sie unterscheiden sich in nur **einer einzigen Bedingung** (eine Regel hat "Ja", die andere "Nein").
        
- **Ergebnis:**
    
    - Die beiden Regeln werden verschmolzen.
    - Die Bedingung, in der sie sich unterscheiden, wird als **"Don't Care"** markiert (üblicherweise mit einem Strich "–").
    - **Bedeutung:** Für diese Regel ist es irrelevant, welchen Wert diese Bedingung annimmt (Ja oder Nein); das Ergebnis (die Aktion) bleibt gleich.
        

---
#### Flashcards

Welche zwei Voraussetzungen müssen erfüllt sein, um Regeln zu konsolidieren? 
?
1. Gleiche Aktionen. 2. Unterschied in genau einer Bedingung.
    

Was ist das Ziel der Konsolidierung bei Entscheidungstabellen? :: Erhöhung der Übersichtlichkeit und Reduktion des Umfangs (Redundanzvermeidung) bei gleicher Logik.

Wie wird eine irrelevante Bedingung nach der Konsolidierung gekennzeichnet? :: Mit einem "Don't Care"-Zeichen (oft ein Strich "–").

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Konsolidierung]]
SORT file.mtime DESC
```