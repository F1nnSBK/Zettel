#Note

2026-06-12

Tags: [[Datenbanken]], [[NoSQL]], [[MongoDB]], [[JSON]], [[Architektur]]
#datenbanken 

---
**MongoDB** (entwickelt ab 2007 von 10gen, Release 2009) ist die weltweit bekannteste Dokumentendatenbank. Sie richtet sich primär an agile Web-Architekturen, bei denen Datenstrukturen oft im JSON-Format vorliegen und sich schnell ändern.

Das Strukturelle Mapping (SQL vs. MongoDB)

Um sich in MongoDB zurechtzufinden, muss man die relationale Terminologie übersetzen:

- **Database:** Bleibt identisch (der oberste Container).
- **Table (Tabelle)** → **Collection (Sammlung):** Eine Gruppe von Dokumenten. Anders als eine Tabelle hat eine Collection jedoch keine festen Spalten.
- **Row (Zeile)** → **Document:** Der eigentliche Datensatz, gespeichert als BSON-Einheit.
- **Column (Spalte)** → **Field:** Ein einzelnes Key-Value-Paar (Schlüssel-Wert-Assoziation) innerhalb des Dokuments.

Skalierung und Hochverfügbarkeit

MongoDB ist für Big Data konzipiert und nutzt dafür zwei zentrale Mechanismen:

1. **Replica Sets (Verfügbarkeit):** Daten werden automatisch auf mehrere Server gespiegelt (Primary für Read/Write, Secondaries als Backup/Read). Fällt der Primary aus, erfolgt ein automatisches Failover.
2. **Sharding (Skalierung):** Um Petabytes an Daten zu bewältigen, wird die Datenbank horizontal über mehrere Cluster-Teile (Shards) verteilt. Die Verteilung erfolgt anhand eines gewählten _Shard Keys_ (Partitionierungsschlüssel).

Abfragen und Java-Integration

Da es kein SQL gibt, nutzt MongoDB die **MQL (MongoDB Query Language)**. Operationen werden direkt als JSON-Objekte übergeben:

- **CRUD:** `insertOne()`, `find()`, `updateOne()`, `deleteOne()`.
- **Operatoren:** Anstatt "=, <, >" nutzt MQL Modifikatoren wie `$set` (Feld updaten), `$inc` (Zahl erhöhen), `$lt` (kleiner als) oder `$gt` (größer als).

**In Java (JDBC-Alternative):** Da Java native `{ }`-JSON-Blöcke im Code nicht als Objekte versteht, muss man den Java-Treiber (`MongoClient`) nutzen. Ein Dokument wird in Java über die Klasse `org.bson.Document` instanziiert und Attribute werden nacheinander mit `.append("Key", "Value")` hinzugefügt, bevor sie an die Datenbank gesendet werden.

---

### Flashcards

Terminologie-Mapping: Nennen Sie die Entsprechungen für „Tabelle“, „Zeile“ und „Spalte“ in der MongoDB-Welt.
?
- **Tabelle** → **Collection** (Sammlung).
- **Zeile** (Tupel) → **Document** (Dokument).
- **Spalte** → **Field** (Feld / Schlüssel-Wert-Paar).

Wie stellt MongoDB die Eindeutigkeit von Dokumenten sicher, wenn der Nutzer beim Einfügen keinen eigenen Primärschlüssel definiert?
?
MongoDB generiert in diesem Fall vollautomatisch eine eindeutige `ObjectId` und speichert diese im zwingend erforderlichen Primärschlüssel-Feld `_id` des Dokuments ab.

Wie garantiert MongoDB auf Architektur-Ebene Hochverfügbarkeit (Schutz vor Serverausfällen)?
?
Durch den Einsatz von **Replica Sets**. Die Daten werden auf mehrere Knoten gespiegelt (ein Primary-Node und mehrere Secondary-Nodes). Fällt der Primary aus, führt das System ein automatisches Failover auf einen Secondary durch.

Was ist "Sharding" in MongoDB und wozu dient es?
?
Sharding ist der Mechanismus zur **horizontalen Skalierung** bei extrem großen Datenmengen. Die Daten einer Collection werden anhand eines Partitionierungsschlüssels (Shard Key) in Fragmente zerschnitten und auf verschiedene Cluster-Teile (Shards) verteilt, was eine fast lineare Skalierung ermöglicht.

Wie unterscheidet sich die Syntax zur Erstellung eines neuen Dokuments in der MongoDB-Shell von der Implementierung im Java-Backend?
?
In der MongoDB-Shell nutzt man direkt die native JSON-Syntax mit geschweiften Klammern `{ "name": "Anna" }`. In Java muss man aufgrund der Sprachsyntax ein `org.bson.Document`-Objekt instanziieren und die Felder programmatisch über die Methode `.append("name", "Anna")` anfügen.

Welche Aufgabe übernehmen die MQL-Operatoren `$set` und `$inc` bei einem Update-Befehl?
?
`$set` aktualisiert den Wert eines bestehenden Feldes oder fügt das Feld neu hinzu, falls es noch nicht existiert. `$inc` (increment) erhöht einen bestehenden numerischen Wert atomar um eine definierte Zahl.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[MongoDB]]
SORT file.mtime DESC
```