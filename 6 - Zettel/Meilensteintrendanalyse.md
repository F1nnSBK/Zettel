#Note

2025-12-15

Tags: [[Projektmanagement]], [[Controlling]], [[Termine]], [[Meilensteine]]
#pm

---
Die **Meilensteintrendanalyse (MTA)** ist ein einfaches, aber mächtiges Instrument zur Überwachung von Terminen. Sie visualisiert die Prognosen für Meilensteintermine über den Zeitverlauf und wird oft als "Fieberkurve" des Projekts bezeichnet.

#### 1. Aufbau des Diagramms

Das Diagramm besteht aus einem rechtwinkligen Dreieck (wegen der Zeitachse).
- **X-Achse (Horizontal):** Die **Berichtszeitpunkte** (Wann frage ich ab? z.B. monatliche Statusmeetings).
- **Y-Achse (Vertikal):** Die geschätzten **Termine der Meilensteine** (Wann werden wir fertig sein?).
    

#### 2. Funktionsweise

Zu jedem Berichtszeitpunkt wird das Team gefragt: "Wann erreichen wir Meilenstein X?". Dieser Punkt wird eingetragen und mit dem vorherigen Punkt verbunden. So entsteht für jeden Meilenstein eine Linie (Trend).

#### 3. Interpretation der Linien

Wie verläuft die Kurve?

- **Horizontaler Verlauf ($\rightarrow$):**
    - _Bedeutung:_ Der geplante Termin wird immer wieder bestätigt.
    - _Fazit:_ **Alles nach Plan.** Das Projekt läuft stabil.
        
- **Steigender Verlauf ($\nearrow$):**
    - _Bedeutung:_ Der geschätzte Termin verschiebt sich immer weiter in die Zukunft (nach oben).
    - _Fazit:_ **Verzug!** Es gibt Probleme oder Verzögerungen. Maßnahmen sind nötig.
        
- **Fallender Verlauf ($\searrow$):**
    - _Bedeutung:_ Der Termin rückt näher (früher als geplant).
    - _Fazit:_ **Puffer / Beschleunigung.** Wir sind schneller als gedacht (oder haben zu viel Puffer eingeplant).
    
- **Zick-Zack-Verlauf:**
    - _Bedeutung:_ Große Unsicherheit im Team über den tatsächlichen Status.
        

#### 4. Ziel

Frühzeitiges Erkennen von Abweichungen, _bevor_ der Endtermin gerissen wird. "Trends" sind oft wichtiger als der aktuelle Status.

---
#### Flashcards (Text-Version)

Was visualisiert die Meilensteintrendanalyse (MTA)? :: Die Entwicklung der **Terminprognosen** für Meilensteine über den Projektverlauf.
<!--SR:!2025-12-17,1,210-->

Was bedeutet eine waagerechte Linie in der MTA? :: Der Termin wird wie geplant eingehalten (Prognose ist stabil).
<!--SR:!2025-12-17,1,210-->

Was signalisiert eine ansteigende Kurve in der MTA? :: Eine **Terminverzögerung** (der Meilenstein wird später fertig als gedacht).
<!--SR:!2025-12-17,1,230-->

Welche Achse repräsentiert in der MTA die Berichtszeitpunkte? :: Die **X-Achse** (Horizontale).
<!--SR:!2025-12-17,1,210-->

Wie wird die MTA umgangssprachlich oft genannt? :: Die **Fieberkurve** des Projekts.
<!--SR:!2025-12-17,1,230-->

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Meilensteintrendanalyse]]
SORT file.mtime DESC
```