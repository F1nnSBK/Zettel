#Note

2025-12-17

Tags: [[Software Engineering]], [[Prozessmodelle]]
#se

---
- **Prototypen-Modell:**
    - **Ziel:** Frühzeitige Erstellung ablauffähiger Modelle zur Risiko- und Unsicherheitsreduktion.
        
    - **3 Arten:**
        1. **Experimenteller Prototyp (Labormuster):** Zur Machbarkeitsprüfung technischer Probleme.
        2. **Explorativer Prototyp (Wegwerf-Prototyp):** Zur Klärung von Anforderungen mit dem Anwender.
        3. **Evolutionärer Prototyp (Pilotsystem):** Wird zum Endsystem weiterentwickelt.
            
    - **Horizontale vs. Vertikale Prototypen:**
        - _Horizontal:_ Realisiert eine Ebene breit (z.B. nur die GUI, "Fassade"), aber keine Tiefe.
        - _Vertikal:_ Realisiert einen ausgewählten Teil durch alle Schichten (GUI, Logik, Daten) ("Durchstich").

    - **Kreislauf des Verstehens:** Zentrales Konzept der Analyse. Der Analytiker übersetzt Anwenderwünsche in Modelle, übersetzt diese zurück in Anwendersprache (z.B. Prototyp/GUI), und der Anwender korrigiert Missverständnisse. Führt zu "Aha-Effekten".
    
- **Evolutionäres Prozessmodell:**
    - Startet mit den **Kern-Anforderungen** (Produktkern/Nullversion), die entworfen und implementiert werden .
    
    - Der Auftraggeber sammelt Erfahrung mit der Version, daraus entstehen neue Anforderungen für die nächste Version (Version X++) .
    
    - **Merkmal:** Code-getrieben; gut geeignet, wenn Anforderungen zu Beginn noch unklar sind .
    
- **Inkrementelles Prozessmodell:**
    - **Unterschied zum Evolutionären:** Es wird zu Beginn ein **vollständiges** Analysemodell (Gesamtsystem) erstellt.
    
    - Die Umsetzung erfolgt dann schrittweise (in Inkrementen), aber der Gesamtplan steht fest. Dies sichert, dass die Teile zusammenpassen .


- **Vergleich der Modelle (Tabelle):**

| Modell                 | Ziel                               | Fokus              | Benutzerbeteiligung                              | Ablauf                     |
|------------------------|------------------------------------|--------------------|--------------------------------------------------|----------------------------|
| Wasserfall / V-Modell  | Qualität & Sicherheit              | Dokumentation      | Gering                                           | Sequenziell                |
| Prototypenmodell       | Risikominimierung                  | Code (Teilsysteme) | Hoch                                             | Iterativ                   |
| Evolutionäres Modell   | Minimale Entwicklungszeit          | Code               | Mittel (sofortiges Kernsystem)                   | Iterativ / Weiterentwicklung |
| Inkrementelles Modell  | Minimale Entwicklungszeit & Risiko | Code               | Mittel (vollständige Definition vorab)           | Inkrementell               |



---
#### Flashcards

Was ist der Unterschied zwischen einem horizontalen und einem vertikalen Prototypen? :: Horizontal: Deckt eine Schicht breit ab (z.B. nur GUI). Vertikal: Deckt einen funktionalen Ausschnitt über alle Schichten ab ("Durchstich").
<!--SR:!2025-12-21,1,230-->

Was ist der entscheidende Unterschied zwischen dem evolutionären und dem inkrementellen Modell? :: Beim inkrementellen Modell liegt zu Beginn eine vollständige Spezifikation (Analyse) vor; beim evolutionären Modell startet man nur mit einem Kern und entwickelt Anforderungen weiter.
<!--SR:!2025-12-21,1,228-->

Wozu dient der "Kreislauf des Verstehens"? :: Zur Validierung und Klärung von Anforderungen zwischen Anwender und Analytiker durch Übersetzung und Feedback (z.B. mittels Prototypen).
<!--SR:!2025-12-21,1,228-->


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Iterative Prozessmodelle & Prototyping]]
SORT file.mtime DESC
```