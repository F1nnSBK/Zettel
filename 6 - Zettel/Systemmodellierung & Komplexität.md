#Note

2025-12-17

Tags: [[Software Engineering]], [[Modellierung]]
#se

---
- **Die 4 Sichten der Modellierung:**
    1. **Daten:** Fokus auf statische Strukturen und Beziehungen (z.B. Entity Relationship Modell ERM, Data Dictionary).
    2. **Funktionen:** Fokus auf Aufgaben und Transformationen (z.B. Funktionsbaum, Datenflussdiagramm DFD).
    3. **Dynamik:** Fokus auf zeitabhängiges Verhalten und Zustände (z.B. Petri-Netz, Sequenzdiagramm, Zustandsautomat).
    4. **GUI:** Fokus auf die Benutzeroberfläche und Interaktion (z.B. Grafik-Editor, Maskengenerator).
        
- **Komplexitätsarten:** Softwaresysteme werden nach verschiedenen Komplexitäten unterschieden: Daten, Funktionen, Algorithmen, zeitabhängiges Verhalten, Systemumgebung und GUI.
    
- **Basiskonzepte (Zuordnung):** Welches Diagramm löst welche Komplexität?
    - **Komplexität der Daten** $\rightarrow$ Data Dictionary, ERM, Klassendiagramm.
    - **Komplexität der Funktionen** $\rightarrow$ Funktionsbaum, Geschäftsprozesse, Datenflussdiagramm.
    - **Komplexität der Algorithmen** $\rightarrow$ Pseudocode, Programmablaufplan (PAP), Struktogramm, Entscheidungstabelle.
    - **Komplexität des zeitabhängigen Verhaltens** $\rightarrow$ Petri-Netz, Zustandsautomat, Sequenzdiagramm, Aktivitätsdiagramm.

---
#### Flashcards

Welche vier Sichten der Systemmodellierung werden unterschieden? 
? 
Daten, Funktionen, Dynamik (Verhalten), GUI.

Welches Diagramm eignet sich besonders für hohe "Komplexität der Daten"?
?
Entity Relationship Model (ERM) oder Klassendiagramm.
<!--SR:!2025-12-23,1,230-->

Mit welchen Methoden beschreibt man "Komplexität der Algorithmen"? 
? 
Pseudocode, Struktogramm, Programmablaufplan (PAP), Entscheidungstabellen.

Welche Diagramme modellieren das zeitabhängige Verhalten (Dynamik)? 
? 
Zustandsautomat, Sequenzdiagramm, Petri-Netz, Aktivitätsdiagramm.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Systemmodellierung & Komplexität]]
SORT file.mtime DESC
```