#Note

2025-12-17

Tags: [[Software Engineering]], [[Agile]]
#se

---
- **Taxonomie agiler Verfahren:**
    - Klassifizierung agiler Methoden anhand von zwei Dimensionen: **Detaillierungsgrad** (Umfang der Festlegungen) und **Flexibilität**.
        
    - _Einordnung:_ **XP** (hoher Detaillierungsgrad, weniger flexibel als Scrum), **Scrum** (sehr flexibel, wenig Vorgaben/Rahmenwerk), **Crystal** (mittig angesiedelt) .
        
- **Crystal Methodenfamilie (Cockburn):**
    - Kein starrer "One-Size-Fits-All"-Ansatz, sondern eine Familie von Methoden, die an die **Projektgröße** (Anzahl Mitarbeiter) und die **Kritikalität** (Schadenspotenzial bei Fehlern) angepasst wird.
        
    - _Farb-Codes:_ Je kritischer/größer, desto "dunkler" die Farbe (mehr Formalismus).
        - **Crystal Clear:** Für kleine Teams (bis 6 Personen) und unkritische Projekte (z.B. nur finanzieller Verlust, kein Leben). Fokus auf Kommunikation in einem Raum.
            
        - Weitere Stufen: Yellow, Orange, Red (für große/kritische Projekte).
            
- **Kriterien zur Methodenauswahl (Spider-Chart/Radar-Chart):**
    
    - Ein Modell (nach Boehm/Turner) zur Abwägung, ob ein agiles oder klassisches Vorgehen sinnvoller ist.
        
    - **5 Dimensionen:**
        1. **Personal:** Fähigkeit und Erfahrung der Entwickler (Agil braucht eher Level 2/3, Klassisch kommt mit Level 1B klar).
        2. **Kritikalität:** Verlustpotenzial (Leben vs. Komfort/Geld). Agil eher bei geringer Kritikalität.
        3. **Dynamik:** Änderungsrate der Anforderungen. Hoch = Agil.
        4. **Teamgröße:** Anzahl Mitarbeiter. Klein = Agil, Groß = Klassisch.
        5. **Unternehmenskultur:** Belohnung von Initiative (Agil) vs. Belohnung von Gehorsam/Ordnung (Klassisch).

---
#### Flashcards

Welche zwei Dimensionen spannen die Taxonomie agiler Verfahren auf? :: Detaillierungsgrad und Flexibilität.

Wovon hängt ab, welche "Farbe" der Crystal-Familie gewählt wird? :: Von der Teamgröße (Anzahl Mitarbeiter) und der Kritikalität (Schadenspotenzial).
<!--SR:!2025-12-23,1,230-->

Nenne die 5 Dimensionen des Spider-Charts zur Methodenauswahl (Boehm/Turner). 
? 
Personal, Kritikalität, Dynamik, Teamgröße, Unternehmenskultur.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Methodenwahl & Crystal]]
SORT file.mtime DESC
```