#Note

2026-06-12

Tags: [[Datenbanken]], [[Verteilte Systeme]], [[Partitionierung]], [[Sharding]], [[Cassandra]]
#datenbanken 

---
**Partitionierung** bezeichnet die logische Aufteilung gigantischer Datenmengen in getrennte Teilmengen (Fragmente). Jede Partition enthält nur einen Ausschnitt der Gesamtdaten. Dies ist der Schlüssel, um große Datenmengen **horizontal zu skalieren**, anstatt Server immer weiter mit RAM und CPU aufzurüsten (vertikale Skalierung).

Die zwei Schnittrichtungen

1. **Horizontale Partitionierung (Der Standard):** Die Tabelle wird nach Zeilen aufgeteilt. Zum Beispiel landen die Kunden A-M in Fragment 1 und die Kunden N-Z in Fragment 2.
2. **Vertikale Partitionierung (Seltener):** Die Tabelle wird nach Spalten aufgeteilt. _Wichtig:_ Damit die Daten später bei einer Abfrage wieder per JOIN zusammengesetzt werden können, muss der Primärschlüssel in _jedem_ vertikalen Fragment zwingend als Redundanz mitgeführt werden.

Sharding = Physische Verteilung

Während Partitionierung oft nur die logische Trennung beschreibt, ist **Sharding** eine spezielle Form der Partitionierung: Hierbei werden die Fragmente _physisch_ auf verschiedene Rechner (Nodes) in einem Cluster verteilt.

- _Beispiel:_ Mitarbeiter mit Nachnamen A-F liegen physisch auf Knoten 1, G-L auf Knoten 2.
- _Der Mechanismus:_ Die Zuweisung, auf welchen Server ein Datensatz wandert, basiert auf einem sogenannten **Shard Key** (Partitionierungsschlüssel).

Deep Dive: Wie Cassandra partitioniert (Hashing)

In Wide-Column Stores wie Cassandra wird der Primärschlüssel in zwei Bestandteile zerlegt: `PRIMARY KEY ((partition_key), clustering_column)`

1. **Der Partition Key (Wo liegen die Daten?):** Er definiert den Container (den Node) für zusammengehörige Datensätze. Die Datenbank wendet standardmäßig einen Hashing-Algorithmus (Murmur3) auf diesen Key an. Der resultierende Hashwert (Token) entscheidet vollautomatisch, auf welchem physischen Server die Daten gespeichert werden. Dies garantiert eine extrem gleichmäßige Datenverteilung.
2. **Die Clustering Column (Wie sind die Daten sortiert?):** Sie legt ausschließlich die physische Zeilenreihenfolge (Sortierung) _innerhalb_ einer Partition auf der Festplatte des jeweiligen Servers fest.

_Sicherheitshinweis für Abfragen:_ In verteilten Systemen muss bei einer `WHERE`-Abfrage fast immer der Partition Key zwingend angegeben werden. Versucht man nur über eine Clustering Column (oder ein normales Feld) zu filtern, ohne den Partition Key zu nennen, lehnt das System die Abfrage ab oder verlangt das gefährliche Konstrukt `ALLOW FILTERING`, welches das gesamte Cluster lahmlegen kann, da alle Server durchsucht werden müssen.

---

### Flashcards

Erklären Sie den Unterschied zwischen horizontaler und vertikaler Fragmentierung (Partitionierung).
?
**Horizontal:** Die Tabelle wird nach Zeilen (Datensätzen) aufgeteilt (häufigster Fall). **Vertikal:** Die Tabelle wird nach Spalten (Attributen) aufgeteilt. Dabei ist zwingend erforderlich, dass der Primärschlüssel in jedem vertikalen Fragment redundant vorhanden ist, um die Datenrelation wiederherstellen zu können.

Was ist der Unterschied zwischen einfacher logischer Partitionierung und dem Konzept des "Sharding"?::Partitionierung ist die reine logische Aufteilung der Daten in Teilmengen. Sharding ist eine spezielle Form der Partitionierung, bei der diese Fragmente _physisch_ auf verschiedene Rechner (Nodes) in einem Netzwerk verteilt werden.

Wie entscheidet ein verteiltes System wie Cassandra vollautomatisch, auf welchem physischen Knoten (Node) ein neuer Datensatz gespeichert wird?::Das System berechnet anhand des **Partition Keys** (mit einem Hashing-Algorithmus wie z. B. Murmur3) einen Hashwert (Token). Dieser Hashwert ist direkt einem bestimmten Knoten im Cluster zugeordnet, was eine gleichmäßige Datenverteilung garantiert.

Was ist in Cassandra der strukturelle und funktionale Unterschied zwischen einem "Partition Key" und einer "Clustering Column"?
?
Der **Partition Key** bestimmt die physische Verteilung: Alles, was denselben Partition Key hat, wird gemeinsam auf demselben Server-Knoten (in derselben Partition) gespeichert. Die **Clustering Column** legt lediglich die physische Sortierung (die Reihenfolge) der Zeilen _innerhalb_ dieser spezifischen Partition auf der Festplatte fest.

Warum ist es in Cassandra fatal und strengstens abgeraten, eine Abfrage mit der Option `ALLOW FILTERING` auf ein Nicht-Schlüssel-Feld (z.B. die IP-Adresse) durchzuführen?::Weil das System ohne die Angabe des Partition Keys nicht weiß, auf welchem Server die Daten liegen. `ALLOW FILTERING` zwingt die Datenbank dazu, sämtliche Partitionen auf allen Knoten im gesamten Cluster sequenziell zu durchsuchen (Full-Cluster-Scan), was die Performance in Produktionsumgebungen massiv einbrechen lässt.

Was versteht man unter dem Begriff "UPSERT" im Kontext moderner NoSQL-Datenbanken?::UPSERT (eine Mischung aus Update und Insert) bedeutet, dass jede Schreiboperation einfach gespeichert wird: Existiert der Key (die ID) bereits in der Datenbank, wird der Wert überschrieben (Update). Existiert der Key noch nicht, wird er automatisch neu angelegt (Insert). Dies optimiert den Schreibdurchsatz extrem.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Partitionierung]]
SORT file.mtime DESC
```