#Note

2026-06-12

Tags: [[Datenbanken]], [[NoSQL]], [[Dokumentendatenbank]], [[MongoDB]], [[BSON]]
#datenbanken 

---
Die **Dokumentenorientierte Datenbank** (Document Store) wurde speziell für moderne Webdienste entwickelt, um eine nahtlose Integration mit JavaScript und JSON-basierten Web-APIs zu ermöglichen. Statt Daten in starre Zeilen und Spalten zu pressen, werden zusammengehörige Informationen als ein geschlossenes digitales Dokument betrachtet.

Auf der obersten Ebene funktioniert eine Dokumenten-DB fast wie ein Key-Value-Store: Ein eindeutiger Schlüssel (die Dokument-ID) verweist auf einen Wert. Dieser "Wert" ist hier jedoch kein flacher String, sondern ein strukturiertes Dokument (JSON) mit rekursiv verschachtelten Attribut-Wert-Paaren und Arrays.

Strukturelles Mapping: Relational vs. Document Store

Um die neue Welt zu verstehen, muss man die Vokabeln übersetzen:

- **Database** ↔ **Database:** Das identische Konzept als oberster Container.
- **Table** ↔ **Collection:** Dokumente werden in "Sammlungen" gruppiert. Im Gegensatz zur Tabelle haben Collections jedoch kein vordefiniertes Schema.
- **Row** ↔ **Document:** Eine Zeile wird zu einem JSON/BSON-Dokument.
- **Column** ↔ **Field:** Eine Spalte wird zu einem Key-Value-Paar (Feld) innerhalb des JSON-Dokuments.

Schemafreiheit (Schema-on-Read) und die Trade-Offs

In einer Collection kann Dokument A völlig andere Felder besitzen als Dokument B.

- **Die Vorteile:** Man benötigt keine DDL-Skripte vor der Dateneingabe. Es ist ideal für unstrukturierte, heterogene oder sich schnell ändernde Daten (wie CMS, Produktkataloge im E-Commerce). Man kann agil iterieren.
- **Die Kosten (Trade-offs):** Das Datenbanksystem erzwingt keine referenzielle Integrität (keine Fremdschlüssel-Prüfung). Zur Beschleunigung der Performance werden Daten oft bewusst denormalisiert (Redundanzen entstehen), und wenn Daten doch stark vernetzt sind, werden Abfragen unverhältnismäßig komplex. Die Schemaverantwortung wandert vollständig vom Datenbank-Administrator in die Applikation der Softwareentwickler.

Der Marktführer: MongoDB und BSON

MongoDB speichert Daten intern nicht als reinen JSON-Text, sondern als **BSON (Binary JSON)**. Das hat enorme Vorteile: Es lässt sich performanter parsen und fügt wichtige Datentypen hinzu, die es im reinen JSON nicht gibt (z. B. IEEE 754 Dezimalzahlen, hochpräzise Datumsformate und Binärdaten). Zudem weist MongoDB jedem eingefügten Dokument automatisch einen einzigartigen Primärschlüssel im Feld `_id` zu, falls dieser nicht explizit mitgegeben wird.

Zur Skalierung und Ausfallsicherheit nutzt MongoDB:

- **Replica Sets:** Daten werden auf mehrere Server (Primary / Secondary) gespiegelt, um automatisches Failover bei Ausfällen zu garantieren.
- **Sharding:** Horizontale Verteilung extremer Datenmengen über sogenannte Shards, basierend auf einem Partitionierungsschlüssel (Shard Key).

---

### Flashcards

Wie unterscheidet sich die Datenspeicherung in einer Dokumentendatenbank strukturell von einer relationalen Tabelle?::Sie speichert Datensätze nicht in flachen Zeilen und Spalten, sondern als in sich geschlossene, strukturierte Dokumente (meist im JSON- oder BSON-Format), welche auch baumartig verschachtelte Objekte und Arrays enthalten dürfen.

Was entspricht in einer dokumentenorientierten Datenbank (wie MongoDB) einer "Tabelle" und einer "Zeile" aus der relationalen Welt?::Die relationale Tabelle entspricht einer **Collection** (Sammlung). Die relationale Zeile (Tupel) entspricht einem einzelnen **Dokument**.

Was versteht man unter „Schemafreiheit“ (Schema-on-Read) bei Dokumentendatenbanken und wo liegt die Hauptverantwortung für die Struktur?::Schemafreiheit bedeutet, dass die Datenstruktur nicht vorab definiert werden muss; jedes Dokument in einer Collection kann individuelle Attribute besitzen. Die Verantwortung für die korrekte Datenstruktur und Gültigkeit verlagert sich dadurch vom DBMS komplett in die Applikationslogik.

Welche architektonischen "Kosten" (Trade-offs) nimmt man bei der Nutzung von Dokumentendatenbanken für die hohe Agilität bewusst in Kauf?::Man verzichtet auf systemseitig erzwungene referenzielle Integrität (Fremdschlüssel) und nimmt bewusst Datenredundanz (fehlende Normalisierung) in Kauf. Zudem können Abfragen bei stark vernetzten Daten deutlich komplexer werden.

Welchen internen Datentyp nutzt MongoDB zur Speicherung von Dokumenten und welche Vorteile bietet dieser gegenüber reinem Text-JSON?::MongoDB nutzt **BSON** (Binary JSON). Die binäre Repräsentation sorgt für viel performanteres Parsen und erweitert den JSON-Standard um typisierte, maschinennahe Daten (wie Datumsformate, IEEE 754 High-Precision Zahlen oder Binärdaten).

Wie garantiert MongoDB Hochverfügbarkeit und wie horizontale Skalierbarkeit für Big Data?::Hochverfügbarkeit wird über **Replica Sets** (Spiegelung auf Primary/Secondary-Knoten mit automatischem Failover) erreicht. Horizontale Skalierbarkeit wird durch **Sharding** (Aufteilung der Daten über mehrere Cluster-Knoten anhand eines Shard-Keys) realisiert.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Dokumentendatenbank]]
SORT file.mtime DESC
```