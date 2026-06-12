#Note

2026-06-12

Tags: [[Datenbanken]], [[Verteilte Systeme]], [[Eventual Consistency]], [[BASE]], [[Cassandra]]
#datenbanken 

---
**Eventual Consistency (Verzögerte Konsistenz)** ist die am weitesten verbreitete Konsistenzstrategie in modernen, verteilten NoSQL-Datenbanken (wie Apache Cassandra). Sie bildet den scharfen Kontrast zur sofortigen, strikten Konsistenz (Strong Consistency) klassischer relationaler ACID-Datenbanken.

Der Mechanismus (Asynchrone Replikation)

In einer relationalen Datenbank mit strenger Konsistenz muss ein Schreibvorgang auf alle Replikate geschrieben und bestätigt werden, bevor der Nutzer ein "Erfolgreich" (Commit) zurückgemeldet bekommt. Das ist extrem sicher, aber furchtbar langsam.

Bei **Eventual Consistency** wird diese Sperre aufgehoben:

1. Der Nutzer sendet ein Update (Schreibaktion).
2. Ein einziger Serverknoten (oder ein kleines Quorum) nimmt das Update an und meldet dem Nutzer **sofort** einen Erfolg zurück, ohne auf die anderen Knoten zu warten.
3. Die Aktualisierung wird erst danach ("nach und nach") über das Netzwerk an die restlichen replizierten Knoten verteilt.

**Das Versprechen:** Das System garantiert lediglich, dass bei Ausbleiben neuer Updates _irgendwann_ alle Replikate im Knotennetz denselben Wert aufweisen.

Die Praxis: Tunable Consistency in Cassandra

Da "irgendwann" für manche Geschäftsfälle zu unsicher ist, bieten Wide-Column-Stores wie Apache Cassandra keine starre Vorgabe, sondern eine **einstellbare Konsistenz (Tunable Consistency)** pro einzelner Abfrage an. Der Entwickler steuert über den sogenannten _Consistency Level (CL)_, wie viele Nodes eine Lese- oder Schreibanfrage bestätigen müssen:

- **CONSISTENCY ONE:** Es reicht, wenn ein einziger Server das Schreiben/Lesen bestätigt. (Maximal schnell, extrem hohe Gefahr für veraltete Daten).
- **CONSISTENCY QUORUM:** Die absolute Mehrheit der Replikate muss dem Schreib-/Lesevorgang zustimmen. (Der perfekte Kompromiss aus Performance und Sicherheit, meist der De-facto-Standard).
- **CONSISTENCY ALL:** Alle Replikate im Cluster müssen bestätigen. (Entspricht fast der starken Konsistenz von ACID, blockiert aber das System sofort, wenn auch nur ein einziger Server offline ist).

---

### Flashcards

Offizielle Prüfungsfrage 10: Was versteht man unter „Eventual Consistency“ (verzögerte Konsistenz) in verteilten Systemen?
?
Das System garantiert nicht die sofortige Sichtbarkeit eines Schreibvorgangs auf allen Server-Knoten gleichzeitig. Es wird lediglich garantiert, dass Schreibaktionen nach und nach im Netzwerk verteilt werden und – sofern keine neuen Updates hinzukommen – _irgendwann_ („eventually“) alle Datenkopien denselben, konsistenten Wert aufweisen.

Warum akzeptieren moderne NoSQL-Systeme wie Cassandra standardmäßig "Eventual Consistency", anstatt starke Konsistenz wie relationale Datenbanken zu erzwingen?::Um gemäß dem CAP-Theorem und dem BASE-Modell bei massiv verteilten Systemen eine maximale Ausfallsicherheit (Verfügbarkeit / AP) und lineare horizontale Skalierbarkeit zu gewährleisten. Strikte Konsistenz würde bei Netzwerkfehlern unweigerlich zu Systemblockaden führen.

Was versteht man unter "Tunable Consistency" (einstellbarer Konsistenz) am Beispiel von Apache Cassandra?::Anstatt auf "Eventual Consistency" festgenagelt zu sein, kann der Entwickler in Cassandra für jede einzelne Abfrage den "Consistency Level (CL)" festlegen (z.B. ONE, QUORUM, ALL). Er kann so dynamisch entscheiden, ob er für diese spezifische Abfrage lieber maximale Geschwindigkeit (ONE) oder absolute Sicherheit (ALL) benötigt.

Was bewirkt der Consistency Level `CONSISTENCY QUORUM` in Cassandra?::Er erzwingt, dass die absolute Mehrheit der replizierten Server-Knoten (das Quorum) einer Lese- oder Schreibanfrage zustimmen muss, bevor sie als erfolgreich gilt. Dies ist der Standard-Kompromiss zwischen Performance und Konsistenz.

Was ist das große Risiko, wenn man in einem Cassandra-Cluster mit 5 Nodes den Consistency Level für Leseanfragen auf `CONSISTENCY ALL` setzt?::Wenn auch nur ein einziger der 5 Knoten aufgrund eines Netzwerkfehlers oder Updates gerade nicht erreichbar ist, wird die Leseanfrage komplett abgewiesen, da nicht "alle" Knoten bestätigen können. Man opfert damit die gesamte Ausfallsicherheit (Verfügbarkeit) des Clusters zugunsten der Konsistenz.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Eventual Consistency]]
SORT file.mtime DESC
```