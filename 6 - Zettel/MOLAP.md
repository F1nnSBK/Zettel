#Note

2026-06-12

Tags: [[Datenbanken]], [[OLAP]], [[Data Warehouse]], [[Architektur]], [[MOLAP]]
#datenbanken 

---
**MOLAP (Multidimensional OLAP)** ist der native Gegenentwurf zu ROLAP. Anstatt die Komplexität eines multidimensionalen Raums über ein relationales Sternschema in flachen Tabellen zu _simulieren_, speichert MOLAP die Daten physisch direkt als mehrdimensionales Array-Konstrukt.

Die 3 Architektur-Vorteile von MOLAP

Durch den Wechsel der Speichertechnologie (Array statt Tabelle) gewinnt MOLAP fundamentale Performance-Vorteile:

1. **Direkte Adressierung (Keine JOINs):** Daten werden nicht mehr über rechenintensive Fremdschlüssel-Suchen oder JOINs ermittelt. Stattdessen nutzt man die Koordinaten im Raum (die Dimensionen), um direkt und verzögerungsfrei auf den Wert in der Array-Zelle zuzugreifen.
2. **Vorausberechnung (Pre-Aggregation):** Der Würfel wird im Vorfeld "gebaut". Bereits beim Laden der Daten berechnet das System alle Kennzahlen auf sämtlichen vordefinierten Hierarchiestufen (z.B. Tages-, Monats- und Jahresumsatz) und speichert sie fix ab. Dadurch entfallen zur Laufzeit (wenn der Analyst auf den Knopf drückt) jegliche Berechnungen.
3. **Konstante Antwortzeiten:** Egal wie komplex die Abfrage des Analysten ist – da die Daten vorab berechnet sind und direkt adressiert werden, ist die Antwortzeit immer konstant und extrem schnell.

Cube-Operationen und Speichereffizienz

- **Slicing & Dicing:** Das Navigieren und "Herausschneiden" von Daten-Scheiben erfolgt bei MOLAP auf systemnaher Ebene schlichtweg durch das _Einschränken der Array-Indizes_.
- **Drill-down / Roll-up:** Da alle Hierarchien schon vorberechnet sind, muss für einen Drill-down (z.B. vom Jahr auf den Monat) nichts neu berechnet werden, man springt lediglich zu einer anderen Koordinate im Array.
- **Sparse Data (Leere Zellen):** In einem multidimensionalen Raum gibt es enorm viele Zellen, für die es keine realen Verkäufe gibt (z.B. Winterjacken im Hochsommer in Spanien). MOLAP-Systeme benötigen daher spezielle, hochkomplexe Kompressionsverfahren, um diese unzähligen leeren Zellen speichereffizient zu verwalten.

Marktsituation

Der absolute Pionier ("Ur-Vater") dieses Ansatzes ist _Oracle Essbase_, ein weiterer bekannter Vertreter ist _IBM Planning Analytics (TM1)_. Da MOLAP durch die Pre-Aggregation jedoch keine echten Echtzeit-Analysen zulässt und enorm viel Speicher für die vorberechneten Daten benötigt, bewegt sich der Markt heute sehr stark weg von MOLAP und hin zu **In-Memory-Relationalen Systemen wie SAP HANA**.

---

### Flashcards

Was ist der fundamentale architektonische Unterschied bei der Datenspeicherung zwischen ROLAP und MOLAP?::ROLAP _simuliert_ einen Datenwürfel mittels zweidimensionaler Tabellen (Sternschema) in einer SQL-Datenbank. MOLAP speichert die Daten nativ und direkt in einem optimierten, mehrdimensionalen Array-Konstrukt ab.

Warum erreicht MOLAP bei Analyse-Abfragen extrem schnelle und konstante Antwortzeiten, unabhängig von der Komplexität der Abfrage?::Weil MOLAP eine strikte **Vorausberechnung (Pre-Aggregation)** durchführt. Alle Kennzahlen auf allen Hierarchiestufen werden bereits beim Laden des Cubes berechnet und gespeichert. Zudem erfolgt der Zugriff über **direkte Adressierung** der Array-Koordinaten (völlig ohne JOINs).

Wie werden analytische Operationen wie Slicing und Dicing in einem nativen MOLAP-Cube technisch realisiert?::Das "Herausschneiden" von Teilmengen aus dem Datenwürfel erfolgt in MOLAP nativ durch die schlichte Einschränkung der zugrunde liegenden Array-Indizes.

Was versteht man im Kontext von MOLAP unter "Sparse Data" und wie gehen die Systeme damit um?::Sparse Data bezeichnet die gigantische Menge an "leeren Zellen" im multidimensionalen Datenwürfel (Kombinationen von Dimensionen, für die keine Fakten/Messwerte vorliegen). MOLAP-Systeme nutzen spezielle Kompressionsverfahren, um diese Ineffizienz abzufedern.

Welcher bekannte Technologietrend (mit Beispiel) verdrängt aktuell zunehmend die klassischen MOLAP-Systeme vom Markt?::Der Markt bewegt sich stark in Richtung schneller **In-Memory-Datenbanken** (z.B. SAP HANA), die relationale Flexibilität mit In-Memory-Geschwindigkeit vereinen.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[MOLAP]]
SORT file.mtime DESC
```