#Note

2025-12-17

Tags: [[Software Engineering]], [[Prozessmodelle]]
#se

---
- **Definition Prozessmodell:** Ein organisatorischer Rahmen für die Softwareentwicklung. Er definiert die Aufbau- und Ablauforganisation und besteht aus definierten **Aktivitäten**, die definierte **Ergebnisse (Produkte)** liefern.

- **Inhalt eines Prozessmodells:** Legt Reihenfolge der Abläufe, durchzuführende Aktivitäten, Teilprodukte (inkl. Layout/Inhalt), Fertigstellungskriterien sowie Rollen und Kompetenzen fest.

- **Top-Risiken der Softwareentwicklung:**
    - Personelle Defizite (falsche Skills).
    - Unrealistische Termin- und Kostenvorgaben.
    - Entwicklung falscher Funktionen oder GUIs (mangelnde Benutzerbeteiligung).
    - "Vergolden" (Gold Plating): Umsetzung unnötiger Features.
    - Kontinuierliche Anforderungsänderungen (Scope Creep) .
        
- **Das WHISCY-Syndrom:** "Why isn't Sam coding yet?" – Beschreibt den Druck (oft vom Management), sofort mit der Programmierung zu beginnen, anstatt Anforderungen zu klären oder zu entwerfen. Führt oft zu "Code & Fix".

- **Code & Fix (Anti-Pattern):**
    - _Vorgehen:_ Programmieren $\rightarrow$ Fehler finden $\rightarrow$ Flicken $\rightarrow$ Wiederholen.
    - _Nachteile:_ Nach Fehlerbehebung wird Struktur oft schlechter (Wartbarkeit sinkt), Fehlerbehebung wird teurer, Anforderungen und Benutzerfreundlichkeit kommen zu kurz, da Analyse- und Entwurfsphasen fehlen.

---
#### Flashcards

Was ist ein Prozessmodell? :: Ein organisatorischer Rahmen, der Aktivitäten definiert, die zu bestimmten Ergebnissen (Produkten) führen.

Was bedeutet das WHISCY-Syndrom? :: "Why isn't Sam coding yet?" – Der Drang/Druck, sofort zu coden, statt zu planen.

Nenne zwei Nachteile des "Code & Fix"-Vorgehens. :: Strukturzerfall (teure Wartung), fehlende Berücksichtigung von Anforderungen (da keine Analyse/Entwurf).

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Grundlagen Prozessmodelle & Anti-Patterns]]
SORT file.mtime DESC
```