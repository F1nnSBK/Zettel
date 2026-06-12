#Note

2026-06-12

Tags: [[Datenbanken]], [[NoSQL]], [[Wide-Column]], [[Big Data]], [[Architektur]]
#datenbanken 

---
Der **Wide-Column Store** entstand aus der Notwendigkeit von Internet-Giganten (wie Google und Facebook), Milliarden von Datensätzen (wie Suchindizes oder Inbox-Nachrichten) zu speichern, an denen relationale Datenbanken zerbrachen.

Das Problem der relationalen Welt

Klassische RDBMS haben drei große Schwächen bei massiven Datenmengen:

1. **Sparse Data:** Wenn eine Tabelle 10.000 Spalten hat, ein Datensatz aber nur 5 davon nutzt, bestehen die restlichen 9.995 Spalten aus `NULL`-Werten. Das verschwendet enormen Speicherplatz und Performance.
2. **Zeilenspeicherung (Row-Store):** Um den Wert einer einzigen Spalte zu lesen, muss das System oft den kompletten Datensatz (die ganze Zeile) von der Festplatte in den RAM laden.
3. **Starrheit:** Jede Zeile wird in das exakt gleiche Spalten-Korsett gezwungen.

Die Lösung: Spaltenfamilien (Column Families)

Wide-Column Stores werfen das Konzept der starren Zeile über Bord. Die Erkenntnis: _Oft werden nur bestimmte Gruppen von Spalten (Column Families) gemeinsam abgefragt. Warum also nicht diese Gruppen als physische Speichereinheit nutzen?_

Die Daten einer Spaltenfamilie werden physisch zusammen in einer eigenen Datei (sogenannten _SSTables_) gespeichert.

- **Der Vorteil:** Wenn eine Abfrage nur die "Familie A" braucht, wird auch nur "Familie A" von der Festplatte gelesen (massive I/O-Effizienz). Zudem lassen sich ähnliche Daten in diesen Spalten extrem gut komprimieren.

Das logische Modell: Die 4D-Map

Anstelle von Tabellenzeilen muss man sich einen Wide-Column-Store als eine sortierte, mehrdimensionale Map vorstellen. Ein Wert wird über 4 Koordinaten lokalisiert: `RowKey, ColumnFamily, Column, Timestamp -> Value`

1. **Row Key:** Die eindeutige ID des Datensatzes. Sie bestimmt via Hashing, auf welchem Server-Knoten im Cluster die Daten physisch landen.
2. **Column Family:** Die physische Gruppierung auf der Festplatte.
3. **Column:** Der dynamische Name der Spalte. Hier greift die Schema-Flexibilität: Zeile A kann völlig andere Spalten besitzen als Zeile B in derselben Familie.
4. **Timestamp:** Die zeitliche Dimension. Er ist essenziell für die Versionierung (die Datenbank speichert z.B. die letzten 3 Versionen), für die Konfliktlösung in verteilten Systemen (_Last Write Wins_) und für das automatische Löschen veralteter Daten via TTL (Time To Live).

**Typische Einsatzgebiete:** Time-Series (Zeitreihendaten), Logging, IoT-Sensordaten und massive Analytics. Zu den bekanntesten Vertretern gehören _Google BigTable_ (der Pionier), _Apache HBase_ und _Apache Cassandra_.

---

### Flashcards

Was ist das grundlegende Problem von "Sparse Data" in relationalen Datenbanken und wie umgehen Wide-Column-Stores dieses Problem?::"Sparse Data" bedeutet, dass ungenutzte Spalten mit `NULL`-Werten befüllt werden, was massiv Speicher und Performance verschwendet. Wide-Column-Stores speichern Spalten dynamisch: Eine Spalte existiert für einen Datensatz physisch nur dann, wenn auch wirklich ein Wert vorhanden ist.

Was ist die zentrale Erkenntnis hinter der Einführung von "Column Families" (Spaltenfamilien) für die physische Speicherung?::Die Erkenntnis ist, dass in der Praxis oft bestimmte Gruppen von Spalten gemeinsam abgefragt werden. Werden diese als eigene physische Speichereinheit (SSTable) abgelegt, muss bei einer Abfrage nicht mehr die komplette Zeile, sondern I/O-effizient nur die benötigte Spaltenfamilie von der Festplatte geladen werden.

Aus welchen vier Komponenten besteht der Pfad zur Adressierung eines exakten Wertes im logischen Modell (der sortierten Map) eines Wide-Column-Stores?::`RowKey`, `ColumnFamily`, `Column` und `Timestamp`.

Welche drei zentralen Aufgaben übernimmt der "Timestamp" im logischen Datenmodell eines Wide-Column Stores?::1. **Versionierung** (Speicherung mehrerer historischer Versionen eines Wertes), 2. **Konfliktlösung** in verteilten Systemen (nach dem Prinzip "Last Write Wins") und 3. **Automatisches Cleanup** (Löschen von Daten über Time To Live / TTL).

Nennen Sie drei typische Einsatzszenarien für Wide-Column-Datenbanken.::Time-Series (Zeitreihendaten), Logging, IoT-Daten (Internet of Things) und Analytics.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Wide-Column Store]]
SORT file.mtime DESC
```