#Note

2025-12-17

Tags: [[Software Engineering]]
#se

---
- **Unterschied zu UML:**
    - BPMN (Business Process Model and Notation) gilt als die "elegantere Lösung" für die Modellierung von Geschäftsprozessen im Vergleich zu UML-Aktivitätsdiagrammen.
    - Es ist ein eigener Standard (OMG), gehört aber **nicht** zur UML-Familie.
    - Fokus liegt stärker auf fachlichen Prozessen und deren Ausführbarkeit.
        
- **Kern-Elemente:**
    
    - **Events (Ereignisse):**
        - _Start:_ Dünner Kreis (Prozess beginnt).
        - _Ende:_ Dicker Kreis (Prozess ist fertig).
        
    - **Activities (Aktivitäten):**
        - _Task (Aufgabe):_ Ein abgerundetes Rechteck, stellt einen Arbeitsschritt dar.
            
    - **Container:**
        - _Pool:_ Repräsentiert eine ganze Organisation oder einen Teilnehmer (z.B. "Firma A").
        - _Lane (Schwimmbahn):_ Unterteilt einen Pool in Zuständigkeiten (z.B. "Buchhaltung", "Vertrieb").
            
    - **Daten:**
        - _Datenobjekt:_ Dokument-Icon (Papier mit Eselsohr), repräsentiert Input/Output (z.B. "Rechnung").
        - _Datenspeicher:_ Tonnen-Symbol, repräsentiert persistente Speicherung (z.B. "Datenbank").
            
- **Gateways (Verzweigungen):**
    - **Exklusives ODER (X):** Raute mit einem "X" (oder leer). Genau ein Pfad wird gewählt (Entweder-Oder).
    - **Paralleles UND (+):** Raute mit einem "+". Alle ausgehenden Pfade werden gleichzeitig (parallel) gestartet; alle eingehenden müssen warten (Synchronisation).
    - **Inklusives ODER (O):** Raute mit einem "O". Ein oder mehrere Pfade können gewählt werden.

---
#### Flashcards

Gehört BPMN 2.0 zum UML-Standard? :: Nein, BPMN ist ein eigenständiger Standard (OMG), auch wenn er ähnlich wie Aktivitätsdiagramme genutzt wird.

Wie wird ein "Start-Ereignis" in BPMN grafisch dargestellt? :: Als dünner Kreis.
<!--SR:!2025-12-23,1,230-->

Was bedeutet ein Gateway mit einem "+" Zeichen in der Mitte? :: Paralleles UND: Alle Pfade werden parallel ausgeführt (Split) oder zusammengeführt (Join/Synchronisation).

Was ist der Unterschied zwischen einem Pool und einer Lane? :: Ein Pool repräsentiert eine eigenständige Organisation/Teilnehmer; eine Lane unterteilt einen Pool in interne Verantwortlichkeiten (Abteilungen/Rollen).


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[BPMN 2.0]]
SORT file.mtime DESC
```