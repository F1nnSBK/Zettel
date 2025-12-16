#Note

2025-12-15

Tags: [[Projektmanagement]], [[Schätzung]], [[Planung]], [[Kosten]], [[Termine]]
#pm

---
Schätzungen sind die Basis für Zeit- und Kostenpläne. Sie sind per Definition unsicher und werden im Projektverlauf präzisiert.

#### 1. Der "Cone of Uncertainty" (Trichter der Unsicherheit)
Zu Beginn eines Projekts ist die Unsicherheit am größten. Mit fortschreitendem Projektverlauf und detaillierterer Planung nimmt die Genauigkeit der Schätzungen zu.
- **Projektstart:** Grobe Schätzung (z.B. +/- 50%).
- **Planungsende:** Genauere Schätzung (z.B. +/- 10%).
    

#### 2. Klassische Schätzmethoden

|**Methode**|**Beschreibung**|**Genauigkeit**|**Aufwand**|
|---|---|---|---|
|**Analoge Schätzung**<br><br>  <br><br>(Top-Down)|Vergleich mit _ähnlichen_, vergangenen Projekten. Basiert auf Expertenwissen und historischen Daten.|Gering (Grob)|Gering|
|**Parametrische Schätzung**|Nutzung statistischer Beziehungen zwischen historischen Daten und Projektvariablen (z.B. Baukosten pro $m^2$, Coding-Zeit pro Line-of-Code).|Mittel (abhängig von Datenqualität)|Mittel|
|**Bottom-Up Schätzung**|Schätzung der kleinsten Arbeitspakete im [[Projektstrukturplan]] und Aggregation nach oben.|**Hoch** (Genaueste Methode)|**Hoch** (Zeitintensiv)|
|**Drei-Punkt-Schätzung**<br><br>  <br><br>(PERT)|Berücksichtigt Unsicherheit durch 3 Werte:<br><br>  <br><br>Optimistisch ($O$), Wahrscheinlich ($M$), Pessimistisch ($P$).<br><br>  <br><br>$\text{Erwartungswert} = \frac{O + 4M + P}{6}$|Hoch|Mittel|

#### 3. Agile Schätzmethoden (Relative Schätzung)
In agilen Projekten (z.B. Scrum) wird oft nicht in absoluter Zeit (Stunden), sondern in relativer Größe (**Story Points**) geschätzt.
- Planning Poker:
    Teammitglieder schätzen verdeckt (mit Karten, oft Fibonacci-Zahlen: 1, 2, 3, 5, 8...), decken gleichzeitig auf und diskutieren Abweichungen.
    - _Vorteil:_ Vermeidet "Anker-Effekte" (Beeinflussung durch Wortführer) und nutzt das Schwarmwissen.


#### 4. Was wird geschätzt?
- **Aufwand:** Die reine Arbeitszeit (Personentage/-stunden).
- **Dauer:** Der Zeitraum vom Start bis zum Ende (inkl. Wartezeiten, Wochenende).
- **Kosten:** Bewerteter Aufwand + Sachmittel.
    

---
#### Flashcards

Welche Aussage trifft der "Cone of Uncertainty"? :: Die Schätzgenauigkeit steigt im Projektverlauf an (der Trichter wird enger).
<!--SR:!2025-12-17,1,210-->

Welche Schätzmethode basiert auf dem Vergleich mit früheren, ähnlichen Projekten? :: Die **Analoge Schätzung**.
<!--SR:!2025-12-17,1,210-->

Welche drei Werte benötigt man für die PERT-Schätzung (Drei-Punkt)? :: Optimistischer, Wahrscheinlichster und Pessimistischer Wert.
<!--SR:!2025-12-17,1,210-->

Warum ist die Bottom-Up-Schätzung sehr zeitaufwendig? :: Weil jedes einzelne Arbeitspaket detailliert geschätzt werden muss, bevor summiert werden kann.
<!--SR:!2025-12-17,1,210-->

Was wird beim "Planning Poker" geschätzt (Einheit)? :: Meistens relative Größen wie **Story Points** (statt absoluter Stunden).
<!--SR:!2025-12-17,1,230-->


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Schätzmethoden]]
SORT file.mtime DESC
```