#Note

2026-06-12

Tags: [[Datenbanken]], [[OLAP]], [[Data Warehouse]], [[Architektur]], [[Sternschema]]
#datenbanken 

---
Das **Sternschema (Star Schema)** ist der De-facto-Standard, um multidimensionale Datenanalysen in einer relationalen SQL-Datenbank abzubilden.

Der Name ergibt sich aus der visuellen Anordnung der Tabellen, die einem Stern gleicht:

1. Die Faktentabelle (Das Zentrum)

Die Faktentabelle bildet den Kern des Sterns. Sie ist oft gigantisch groß (Milliarden Zeilen) und enthält:

- **Quantitative Kennzahlen (Fakten):** Messbare, aggregierbare Werte wie Umsatz, Stückzahl oder Dauer.
- **Fremdschlüssel:** Verweise auf alle assoziierten Dimensionstabellen.
- _(Beispiel: Ein einzelner Datensatz in "Kaufauftrag" hat die Fremdschlüssel Ort_ID, Produkt_ID, Zeit_ID, Kunden_ID und speichert als Fakten die "Anzahl" und den "Umsatz"__.)_

2. Die Dimensionstabellen (Die Strahlen)

Diese Tabellen gruppieren sich sternförmig um das Zentrum. Sie enthalten die **deskriptiven Attribute** (also die Kriterien, nach denen Analysten filtern wollen, z. B. Produktname, Region, Zeit).

- **Wichtige Regel:** Es existiert pro Dimension exakt _eine_ einzige Tabelle. Das macht die Struktur extrem übersichtlich.

Das Geheimnis: Strategische Denormalisierung

Um die Abfragegeschwindigkeit in OLAP-Systemen hoch zu halten, wendet man in den Dimensionstabellen die **strategische Denormalisierung** an. Das bedeutet: Redundanzen und ein erhöhter Speicherbedarf werden völlig bewusst in Kauf genommen. Man verstößt absichtlich gegen die Normalisierungsregeln, um die Anzahl der rechenintensiven `JOIN`-Operationen bei komplexen Analysen zu minimieren.

**Warum ist das erlaubt?** Weil OLAP-Systeme (Data Warehouses) fast ausschließlich für lesende Zugriffe (Read-Only) historischer Daten optimiert sind. Da Endnutzer in diesen Systemen keine Daten überschreiben oder anlegen, können die gefürchteten Update-Anomalien gar nicht erst auftreten und werden schlichtweg "akzeptiert".

Grenzen des Modells

Obwohl das Sternschema der Standard ist, hat es Nachteile: Bei sehr umfangreichen multidimensionalen Datenbanken stößt die Leistungsfähigkeit von normalen relationalen Systemen an ihre physikalischen Grenzen. Zudem ist das Formulieren von komplexen SQL-Abfragen über dieses Schema für Analysten extrem aufwendig und sehr fehleranfällig.

---

### Flashcards

Welche zwei grundlegenden Tabellen-Typen bilden die Architektur eines Sternschemas?::Eine zentrale **Faktentabelle** (enthält Kennzahlen und Fremdschlüssel) und mehrere sternförmig darum angeordnete **Dimensionstabellen** (enthalten die beschreibenden Filter-Attribute).

Welche Art von Daten befindet sich typischerweise im Zentrum eines Sternschemas (der Faktentabelle)?::Quantitative Kennzahlen (die messbaren Fakten, z.B. Umsatz, Verkaufsmenge) sowie die Fremdschlüssel zu allen assoziierten Dimensionstabellen.

Was versteht man im Kontext von ROLAP und dem Sternschema unter "strategischer Denormalisierung"?::Das bewusste Aufgeben von Normalisierungsregeln in den Dimensionstabellen. Redundanzen und erhöhter Speicherbedarf werden gezielt in Kauf genommen, um die Anzahl der notwendigen JOINs zu minimieren und so Leseabfragen zu beschleunigen.

Warum sind die durch Denormalisierung entstehenden "Update-Anomalien" in einem Sternschema architektonisch kein Problem?::Weil OLAP-Systeme (Data Warehouses) primär für lesende Zugriffe (Read-Only) auf historische Daten optimiert sind. Nutzer führen hier keine schreibenden Updates durch, weshalb die Anomalien akzeptiert werden.

Nennen Sie zwei wesentliche Nachteile/Grenzen, wenn man multidimensionale Daten mit einem Sternschema in relationalen Datenbanken abbildet.::1. Die Leistungsfähigkeit des relationalen RDBMS stößt bei sehr großen multidimensionalen Datenbanken an Grenzen. 2. Das Formulieren der nötigen SQL-Abfragen ist sehr aufwendig und fehleranfällig.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Sternschema]]
SORT file.mtime DESC
```