#Note

2026-06-09

Tags: [[Datenbanken]], [[Datenbankentwurf]], [[Normalisierung]]
#datenbanken 

---
Die **Normalisierung** ist ein Kernprozess in der relationalen Datenbankmodellierung. Das Ziel ist es, Daten so zu strukturieren, dass **Redundanzen (Mehrfachspeicherungen) minimiert** und sogenannte **Datenanomalien vermieden** werden. Dabei werden große Tabellen schrittweise in kleinere, über Fremdschlüssel verknüpfte Tabellen zerlegt.

### Warum normalisieren? Das Problem der Anomalien

Wenn Daten redundant gespeichert werden, führt das bei Änderungen unausweichlich zu logischen Fehlern (Anomalien).

**Beispiel-Tabelle (Unnormalisiert):** `Studenten(MatrikelNr [PK], Name, StudiengangNr, StudiengangName)`

1. **Einfügeanomalie (Insertion Anomaly):** Daten können nicht eingefügt werden, weil der Primärschlüssel fehlt.
    - _Beispiel:_ Wir wollen einen neuen Studiengang "Informatik" anlegen. Das geht nicht, weil wir noch keinen Studenten (MatrikelNr = Primärschlüssel) haben, der ihn belegt.
2. **Löschanomalie (Deletion Anomaly):** Beim Löschen eines Datensatzes gehen ungewollt auch unabhängige Zusatzinformationen verloren.
    - _Beispiel:_ Wenn sich der letzte Student des Studiengangs "Physik" exmatrikuliert und wir seinen Datensatz löschen, vergisst die Datenbank komplett, dass der Studiengang "Physik" je existiert hat.
3. **Änderungsanomalie (Update Anomaly):** Eine Änderung muss an hunderten Stellen gleichzeitig gemacht werden. Wird eine vergessen, ist die Datenbank inkonsistent.
    - _Beispiel:_ Der Studiengang "BWL" wird in "Digital Business" umbenannt. Wir müssen dies bei 500 Studenten in jeder einzelnen Zeile ändern.

--------------------------------------------------------------------------------

Die 3 wichtigsten Normalformen (mit Beispielen)

Der Weg zur perfekten Datenbank verläuft über feste, aufeinander aufbauende Regeln.

1. Normalform (1NF) - Atomare Werte

- **Regel:** Jedes Feld in der Tabelle darf nur einen einzigen, unteilbaren (atomaren) Wert enthalten. Es darf keine "Wiederholungsgruppen" (Listen in einer Zelle) geben.
- **Das Problem:** Ein Mieter mietet mehrere Autos. In der Zelle "Fahrzeugtyp" steht `["Opel Corsa", "VW Golf"]`.
- **Die Lösung:** Die Zeile wird aufgespalten. Es entstehen zwei separate Zeilen. Der Primärschlüssel muss oft zusammengesetzt werden (z.B. `MieterNr` + `WagenNr`), damit jede Zeile eindeutig bleibt. _(Achtung: Dies erhöht im ersten Schritt die Redundanz!)_

2. Normalform (2NF) - Volle funktionale Abhängigkeit

- **Bedingung:** Die Tabelle ist in der 1NF.
- **Regel:** Jedes Nicht-Schlüsselattribut muss vom _gesamten_ (zusammengesetzten) Primärschlüssel abhängen, nicht nur von einem Teil davon.
- **Das Problem:** Primärschlüssel ist `(MieterNr, WagenNr)`. Das Attribut `KundenName` hängt aber nur von der `MieterNr` ab, völlig egal, welchen Wagen er mietet. Das Attribut `Baujahr` hängt nur von der `WagenNr` ab.
- **Die Lösung:** Alles, was nur von einem Teil des Schlüssels abhängt, wird in eigene Tabellen ausgelagert.
    - _Tabelle 1:_ `Mieter (MieterNr [PK], KundenName)`
    - _Tabelle 2:_ `Wagen (WagenNr [PK], Baujahr)`
    - _Tabelle 3 (Beziehungstabelle):_ `Vermietung (MieterNr [PK], WagenNr [PK], Mietdauer)`

3. Normalform (3NF) - Transitive Unabhängigkeit

- **Bedingung:** Die Tabelle ist in der 2NF.
- **Regel:** Kein Nicht-Schlüsselattribut darf von einem anderen Nicht-Schlüsselattribut abhängen ("Aus keinem Nicht-Schlüssel folgt ein anderer Nicht-Schlüssel").
- **Das Problem:** Wir haben die Tabelle `Wagen (WagenNr [PK], Fahrzeugtyp, Mietsatz_pro_Tag)`. Der Mietsatz hängt zwar vom Wagen ab, aber _eigentlich_ hängt der Mietsatz vom `Fahrzeugtyp` ab (z.B. alle VW Golf kosten 99€). `WagenNr -> Fahrzeugtyp -> Mietsatz`. Das ist eine transitive Kette.
- **Die Lösung:** Wir lagern die transitive Abhängigkeit in eine neue Tabelle aus:
    - _Tabelle 1:_ `Fahrzeugkategorie (Fahrzeugtyp [PK], Mietsatz)`
    - _Tabelle 2:_ `Wagen (WagenNr [PK], Fahrzeugtyp [FK])`

#### Fazit & Praxisrelevanz

Normalisierung (meist bis zur 3NF) ist der Standard für Transaktionssysteme (OLTP wie Online-Shops, Banking), da sie **Redundanz vermeidet**, **Datenintegrität** sicherstellt und die **Pflege vereinfacht**. Für komplexe Analysezwecke (Data Warehouse, Big Data) wird oft absichtlich _denormalisiert_, da die durch Normalisierung entstehenden Tabellen-Joins die Lese-Performance stark einbrechen lassen.

--------------------------------------------------------------------------------

### Flashcards

Was ist das Hauptziel der Datenbank-Normalisierung?::Die Minimierung von redundanten Daten (Mehrfachspeicherungen), um Datenanomalien bei Schreib-, Lösch- und Änderungsoperationen zwingend zu verhindern.

Erkläre die "Löschanomalie" an einem einfachen Beispiel.
?
Wenn in einer unnormalisierten Tabelle ein Datensatz gelöscht wird, gehen ungewollt Zusatzinformationen verloren. Beispiel: Löscht man den letzten Studenten eines Studiengangs, geht in der Datenbank die Information verloren, dass dieser Studiengang überhaupt existiert.

Was fordert die 1. Normalform (1NF)?::Jedes Attribut einer Tabelle muss atomar (unteilbar) sein. Es darf an keinem Kreuzungspunkt von Zeile und Spalte Listen oder Wiederholungsgruppen geben.

Was fordert die 2. Normalform (2NF) und wann ist sie automatisch erfüllt?
?
Jedes Nicht-Schlüsselattribut muss vom _gesamten_ Primärschlüssel abhängen (volle funktionale Abhängigkeit) und darf nicht nur durch einen Teil eines zusammengesetzten Schlüssels erklärt werden können. Besteht der Primärschlüssel aus nur einem einzigen Attribut, ist die 2NF (sofern 1NF gegeben) automatisch erfüllt.

Was fordert die 3. Normalform (3NF)?
?
Sie verbietet transitive Abhängigkeiten. Kein Nicht-Schlüsselattribut darf von einem anderen Nicht-Schlüsselattribut abhängen. Alles muss direkt vom Primärschlüssel abhängen.

Welchen großen Nachteil hat eine vollständig (bis zur 3NF) normalisierte Datenbank?
?
Da die Daten auf viele kleine Tabellen verteilt sind, werden SQL-Leseabfragen sehr komplex. Das Zusammenführen über JOINs kostet bei großen Datenmengen massiv Performance.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Normalisierung]]
SORT file.mtime DESC
```