#Note

2026-06-12

Tags: [[Datenbanken]], [[NoSQL]], [[Cassandra]], [[Wide-Column]], [[Architektur]]
#datenbanken 

---
**Apache Cassandra** wurde ursprünglich 2008 von Facebook für die Inbox-Search entwickelt, um sehr große Datenmengen bei hoher Schreiblast ohne Single Point of Failure (SPOF) global verfügbar zu machen. Heute ist es ein Top-Level-Projekt der Apache Software Foundation.

Das Datenmodell (Keyspace & Keys)

Die oberste Ebene in Cassandra ist der **Keyspace** (vergleichbar mit der relationalen Datenbank), in dem die Replikationsstrategie (z.B. `SimpleStrategy`) und der Replikationsfaktor (wie viele Kopien es pro Zeile gibt) festgelegt werden.

Die Tabellenstruktur stützt sich massiv auf den komplexen **Primärschlüssel**, der aus zwei Teilen besteht:

1. **Partition Key:** Er bestimmt, auf welchem physischen Server-Knoten (Node) die Daten landen. Cassandra wendet eine Hash-Funktion (Murmur3) auf diesen Key an, um eine gleichmäßige Verteilung zu garantieren. Als Datentyp wird hier für IDs oft **UUID** (ein 128-Bit Universally Unique Identifier) verwendet, da in verteilten Systemen ohne Master-Server keine fortlaufenden Nummern (1, 2, 3...) kollisionsfrei vergeben werden können.
2. **Clustering Columns:** Diese definieren die Sortierreihenfolge der Zeilen _innerhalb_ einer Partition auf der Festplatte.

CQL und "Query First"

Cassandra nutzt die **Cassandra Query Language (CQL)**. Obwohl die Syntax an SQL angelehnt ist, gibt es fundamentale Unterschiede:

- **Keine JOINs:** Da Daten über ein Netzwerk verteilt sind, wären JOINs viel zu teuer und langsam. Daten werden stattdessen bewusst denormalisiert.
- **Model First vs. Query First:** In SQL baut man erst das normalisierte Modell ("Model First"). In Cassandra überlegt man sich zuerst, welche Leseabfragen die Applikation braucht, und baut die Tabellen exakt um diese Abfragen herum ("Query First").
- **Die WHERE-Falle:** Man darf in CQL standardmäßig nur filtern, wenn der Partition Key angegeben wird, da das System sonst nicht weiß, auf welchem Server es suchen muss. Filtert man ohne diesen Key, muss man explizit `ALLOW FILTERING` anhängen – ein Befehl, der einen Full-Cluster-Scan auslöst und in der Produktion strengstens verboten ist.

Das UPSERT-Konzept

Da Cassandra für extreme Schreibgeschwindigkeit konzipiert ist (ohne zentrale Sperren/Locks), gibt es keine Unterscheidung zwischen `INSERT` und `UPDATE`. Alles ist ein **UPSERT**.

- Existiert die ID noch nicht → Der Datensatz wird neu angelegt.
- Existiert die ID bereits → Der alte Wert wird einfach blind überschrieben.
- _Vorteil:_ Maximaler Durchsatz. _Nachteil:_ Kein Schutz vor versehentlichem Überschreiben.

Konsistenz-Tuning

Cassandra arbeitet standardmäßig mit Eventual Consistency. Man kann die Konsistenz (CL) jedoch pro Abfrage steuern:

- `CONSISTENCY ONE`: Nur ein Server muss das Lesen/Schreiben bestätigen (schnell, aber unsicher).
- `CONSISTENCY QUORUM`: Die absolute Mehrheit der Replikate muss zustimmen (der perfekte Standard-Kompromiss).
- `CONSISTENCY ALL`: Alle Replikate müssen bestätigen (entspricht fast ACID, aber ein einziger Serverausfall blockiert die Abfrage).

---

### Flashcards

Erklären Sie den methodischen Unterschied zwischen „Model First“ (SQL) und „Query First“ (Cassandra).
?
In SQL plant man zuerst die normalisierte Tabellenstruktur ("Model First") und baut die Abfragen später per JOINs zusammen. In Cassandra designt man die Tabellen exakt nach den vorab definierten Leseabfragen der Applikation ("Query First"), da es keine JOINs gibt und die Daten oft denormalisiert und redundant gespeichert werden müssen.

Wie erreicht Cassandra eine lineare horizontale Skalierbarkeit?
?
Durch Hashing und Sharding: Die Datenverteilung über alle Knoten erfolgt vollautomatisch anhand des Partition Keys und einer Hash-Funktion (wie Murmur3). Dadurch können dem Cluster einfach neue Nodes hinzugefügt werden, was quasi linear mehr Kapazität und Performance bringt.

Was versteht man in Cassandra unter einem „UPSERT“?
?
Cassandra unterscheidet physisch nicht zwischen `INSERT` und `UPDATE`. Jede Schreiboperation wird einfach gespeichert. Existiert der Schlüssel (die ID) bereits, wird der alte Wert überschrieben; existiert er nicht, wird er neu angelegt. Das optimiert den Schreibdurchsatz extrem, bietet aber keinen Schutz vor versehentlichem Überschreiben.

Warum wird in Cassandra für IDs anstelle fortlaufender Nummern (Auto-Increment) standardmäßig der Datentyp UUID verwendet?::Eine UUID (Universally Unique Identifier) ist eine 128-Bit-Zahl. Da Cassandra ein verteiltes System ohne zentralen Master-Knoten ist, können sich die Server bei der ID-Vergabe nicht absprechen. Eine zufällig generierte UUID ist mathematisch so eindeutig, dass Kollisionen bei gleichzeitigen Schreibvorgängen auf verschiedenen Servern praktisch unmöglich sind.

Warum ist die Verwendung von `ALLOW FILTERING` in einer CQL-Abfrage auf einer Produktivumgebung hochgradig gefährlich?::Da `ALLOW FILTERING` angewendet wird, wenn man auf Spalten ohne den Partition Key filtert. Das System weiß dann nicht, auf welchem Node die Daten liegen, und muss alle Server im gesamten Cluster durchsuchen (Full-Cluster-Scan), was die Performance massiv einbrechen lässt.

Was regelt die Angabe `CONSISTENCY QUORUM` bei einer Lese- oder Schreibabfrage in Cassandra?::Sie definiert den Konsistenz-Level und erzwingt, dass die absolute Mehrheit der replizierten Knoten der Abfrage zustimmen bzw. diese bestätigen muss, bevor sie dem Client als erfolgreich zurückgemeldet wird.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Cassandra]]
SORT file.mtime DESC
```