#Note

2026-06-12

Tags: [[Datenbanken]], [[Verteilte Systeme]], [[Replikation]], [[Hochverfügbarkeit]], [[Architektur]]
#datenbanken 

---
**Replikation** bezeichnet die redundante Speicherung von Daten auf mehreren Servern. Sie ist die wichtigste Architektur-Maßnahme in verteilten Systemen, um zwei fundamentale Ziele zu erreichen:

1. **Ausfallsicherheit (Hochverfügbarkeit):** Wenn ein Server brennt, übernehmen die Kopien auf den anderen Servern nahtlos.
2. **Leseperformance:** Leseanfragen (`SELECT`) können auf alle verfügbaren Replikate verteilt (Load Balancing) werden.

**Das architektonische Problem:** Replikation erhöht die Verfügbarkeit extrem, aber die Konsistenz wird massiv komplizierter. Wenn man Daten ändert, müssen alle Replikate im Netzwerk benachrichtigt werden. Klassische relationale Systeme (RDBMS) nutzen hierfür oft das komplexe und langsame Zwei-Phasen-Commit-Protokoll (2PC), um ACID-Sicherheit zu garantieren.

Die 3 Architekturen der Replikation

**1. Master-Slave-Replikation**

- **Konzept:** Es gibt eine strenge Hierarchie. Ein Server ist der "Chef" (Master), die anderen die Kopien (Slaves).
- **Datenfluss:** **Schreibzugriffe** (Änderungen) dürfen **nur** über den Master-Node erfolgen. Der Master pusht die Updates dann an die Slaves. **Lesezugriffe** können jedoch über alle Nodes erfolgen.
- **Ausfall:** Fällt der Master aus, wird durch einen Wahl-Algorithmus (Failover) automatisch ein Slave zum neuen Master befördert.

**2. Master-Master-Replikation**

- **Konzept:** Es gibt keine Hierarchie.
- **Datenfluss:** Alle Nodes im Cluster haben volle **Lese- und Schreibzugriffe**.
- **Ausfall/Risiko:** Fällt ein Knoten aus, übernehmen die anderen sofort. Allerdings ist die Konfliktauflösung (wenn zwei Knoten gleichzeitig denselben Datensatz ändern) extrem komplex.

**3. Masterless / Peer-to-Peer (Beispiel: Cassandra)**

- **Konzept:** Perfektioniert in Wide-Column-Stores wie Cassandra. Alle Replikate sind absolut gleichwertig (kein Master-Slave). Es gibt keinen "Single Point of Failure".
- **Datenfluss:** Ein _Keyspace_ definiert den **Replication Factor (RF)** (z. B. RF=3 bedeutet, es gibt 3 Kopien jeder Zeile im Cluster). Die Konsistenz pro Lese-/Schreibvorgang kann dann vom Entwickler dynamisch über den _Consistency Level (CL)_ eingestellt werden (z. B. müssen bei `QUORUM` die Mehrheit der Replikate den Schreibvorgang bestätigen).

---

Flashcards

Was versteht man in verteilten Datenbanksystemen unter „Replikation“ und welche zwei Hauptziele werden damit verfolgt?::Replikation ist die redundante Speicherung von Daten auf mehreren Servern. Sie dient in erster Linie der Erhöhung der Ausfallsicherheit (Hochverfügbarkeit) und der Verbesserung der Leseperformance (durch Lastenverteilung auf verschiedene Replikate).

Welcher fundamentale Trade-Off (Kompromiss) entsteht beim Einsatz von Datenreplikation in verteilten Systemen?::Replikation erhöht zwar die Verfügbarkeit des Systems, macht aber die Gewährleistung der Konsistenz deutlich komplizierter. Es sind aufwendige Koordinationsmechanismen (wie das Zwei-Phasen-Commit-Protokoll in RDBMS) nötig, um alle Replikate synchron zu halten.

Erklären Sie die Funktionsweise und den Datenfluss der Master-Slave-Replikation.
?
Bei der Master-Slave-Replikation gibt es eine strenge Hierarchie. Schreibzugriffe (Änderungen) dürfen ausnahmslos nur auf dem Master-Node ausgeführt werden. Lesezugriffe können hingegen auf alle Nodes (Master und Slaves) verteilt werden. Fällt der Master aus, wird ein Slave zum neuen Master befördert.

Worin besteht der architektonische Hauptunterschied zwischen einer Master-Master-Replikation und einer Master-Slave-Replikation?::Bei der Master-Master-Replikation gibt es keine Hierarchie; alle Server-Knoten im Netzwerk haben sowohl volle Lese- als auch volle Schreibzugriffe auf die Datenbank. Bei der Master-Slave-Architektur darf nur ein einziger Knoten schreibend verändert werden.

Wie wird die Replikation in modernen Wide-Column-Datenbanken wie Apache Cassandra konfiguriert und wie unterscheidet sie sich vom Master-Slave-Ansatz?
?
Cassandra nutzt eine "Masterless"-Architektur (Peer-to-Peer). Alle Replikate sind völlig gleichwertig; es gibt keinen Master und damit keinen "Single Point of Failure". Die Anzahl der Kopien wird auf Keyspace-Ebene über den sogenannten **Replikationsfaktor (RF)** festgelegt (z.B. RF=3 bedeutet drei Kopien pro Zeile im Cluster).


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Replikation]]
SORT file.mtime DESC
```