#Note

2026-06-12

Tags: [[Datenbanken]], [[Architektur]], [[OLAP]], [[Data Warehouse]], [[Sternschema]]
#datenbanken 

---
Um Datenmengen strategisch auszuwerten, reicht die Architektur einer normalen relationalen Datenbank nicht aus. Hier entsteht der fundamentale **Analyse-Konflikt**:

- **OLTP (Online Transaction Processing):** Optimiert für das operative Tagesgeschäft (z. B. Bestellungen schreiben). Die Tabellen sind hochgradig normalisiert (3. NF), um Redundanzen und Anomalien beim Schreiben zu vermeiden.
- **OLAP (Online Analytical Processing):** Optimiert für komplexe, lesende Auswertungen über Millionen Datensätze. Würde man solche Analysen auf einem OLTP-System ausführen, würde das System zusammenbrechen und das operative Geschäft blockieren.

Daher baut man eigenständige Analyse-Systeme (Data Warehouses), die mit mehrdimensionalen Datenstrukturen (**Data Cubes**) arbeiten.

Der Data Cube und seine Operationen

Informationen werden in einem logischen Würfel dargestellt:

- **Dimensionen (Die Achsen):** Die Auswertungskriterien (z. B. Zeit, Produkt, Region). Sie können Hierarchien bilden (Tag → Monat → Quartal).
- **Fakten (Der Inhalt):** Die quantitativen Werte im Zentrum (z. B. Umsatz, Stückzahl).

Analysten navigieren durch diesen Würfel mit 4 Kern-Operationen:

1. **Slicing:** Ausschneiden einer 2D-Scheibe (z. B. Umsatz aller Produkte nur in der Region "West").
2. **Dicing:** Auswahl eines kleineren Teilwürfels durch Filtern mehrerer Dimensionen.
3. **Roll-up (Verdichten):** Aggregation auf eine höhere Hierarchie-Ebene (z. B. von Monats- auf Jahresumsatz).
4. **Drill-down (Aufschlüsseln):** Zoom in die Details (z. B. von der Region auf die einzelne Stadt).

ROLAP: Die Umsetzung als Sternschema

Um diesen Würfel in einer SQL-Datenbank abzubilden, nutzt ROLAP das **Sternschema (Star Schema)**:

1. **Faktentabelle (Das Zentrum):** Enthält die reinen Kennzahlen (Umsatz, Anzahl) und ausschließlich die Fremdschlüssel zu den Dimensionen.
2. **Dimensionstabellen (Die Strahlen):** Gruppieren die beschreibenden Attribute (z.B. Produktkategorie, Land) sternförmig um das Zentrum.

**Das Geheimnis: Strategische Denormalisierung** Dimensionstabellen werden im Sternschema ganz bewusst denormalisiert! Man nimmt Redundanzen in Kauf, um die Anzahl der Tabellen zu reduzieren. Dadurch entfallen extrem rechenintensive SQL-`JOIN`s. Da OLAP-Systeme primär für lesende Zugriffe (Read-Only) optimiert sind und historische Daten analysieren, sind die sonst so gefürchteten "Update-Anomalien" hier kein Problem und werden einfach akzeptiert.

---

### Flashcards

Offizielle Prüfungsfrage 6: Unterscheiden Sie operative Datenbanksysteme (OLTP) von analytischen Systemen (OLAP) hinsichtlich ihres primären Zwecks.
?
**OLTP (Online Transaction Processing)** dient der schnellen Abwicklung des operativen Tagesgeschäfts (Fokus auf präzises, normalisiertes Schreiben von Transaktionen). **OLAP (Online Analytical Processing)** dient der Entscheidungsunterstützung durch die multidimensionale Analyse riesiger historischer Datenbestände (Fokus auf komplexe, lesende Abfragen).

Aus welchen zwei fundamentalen Tabellen-Typen besteht ein Sternschema in einer ROLAP-Architektur?
?
Es besteht aus einer zentralen **Faktentabelle** (enthält die quantitativen Kennzahlen wie Umsatz und Fremdschlüssel) und mehreren sternförmig angeordneten **Dimensionstabellen** (enthalten die beschreibenden Attribute wie Zeit, Ort oder Produkt).

Warum werden Dimensionstabellen in einem ROLAP-Sternschema "strategisch denormalisiert" (also absichtlich gegen die Regeln der 3. Normalform verstoßen)?::Redundanzen und ein erhöhter Speicherbedarf werden bewusst in Kauf genommen, um die Anzahl der notwendigen JOINs zu minimieren. Dies beschleunigt komplexe, lesende Analyse-Abfragen extrem.

Warum sind Update-Anomalien, die durch die Denormalisierung im Sternschema entstehen, für OLAP-Systeme in der Praxis meist unproblematisch?::Weil OLAP-Systeme (Data Warehouses) primär für lesende Zugriffe (Read-Only) auf historische Datenbestände konzipiert sind. Die Daten werden meist im Hintergrund geladen und nicht durch Endnutzer aktualisiert.

Erklären Sie den Unterschied zwischen den Cube-Operationen "Roll-up" und "Drill-down".::**Roll-up** bedeutet das Verdichten der Daten auf eine höhere Hierarchieebene (z.B. die Aggregation von Monatsumsätzen zu einem Jahresumsatz). **Drill-down** ist das Gegenteil: Das Aufschlüsseln der Daten in detailliertere Ebenen (z.B. vom Land in die einzelnen Regionen).


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[ROLAP]]
SORT file.mtime DESC
```