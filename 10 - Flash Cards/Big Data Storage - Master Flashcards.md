#big_data

### UE01: Kursüberblick und Big-Data-Storage-Perspektive

Warum beginnt die Betrachtung von Big Data beim Storage (und nicht bei Algorithmen)?
?
Weil Storage der fundamentale Engpass ist. Die Speicherarchitektur legt fest, ob ein System bei Anfragen zügig reagieren kann, wie teuer es pro Datenmenge wird und ob es unter massiver Last stabil bleibt. Wer Storage ignoriert, trifft Entscheidungen im Blindflug.

Wie übersetzen sich die 3 V's von Big Data (Volume, Variety, Velocity) in konkrete Herausforderungen auf Speicherebene (Storage-Fragen)?
?
- **Volume**: Die Datenmenge überschreitet die Kapazität eines einzelnen Servers (erfordert horizontale Verteilung).
- **Variety**: Unterschiedliche Datenformen (z.B. Tabellen, Dokumente, Objekte, Ereignisströme) erfordern flexiblere Ablagestrukturen als starre Tabellenschemata.
- **Velocity**: Daten entstehen schneller, als klassische relationale Datenbanksysteme sie wegschreiben können (erfordert Ingestions-Geschwindigkeit).

Die Ebenen des Big-Data-Stacks (von unten nach oben) lauten: ==Storage==, ==Syntax==, ==Datenmodell==, ==Verarbeitung== und ==Serving==.

Wie ordnen sich typische Technologien den Ebenen des Big-Data-Stacks (Storage, Syntax, Datenmodell, Verarbeitung, Serving) zu?
?
- **Storage**: HDFS, Object Store
- **Syntax**: CSV, JSON, Parquet
- **Datenmodell**: Tabelle, Dokument, Graph
- **Verarbeitung**: Spark, MapReduce
- **Serving**: API, Dashboard

Worin unterscheiden sich OLTP und OLAP hinsichtlich ihrer Zielsetzung?
?
OLTP (Online Transaction Processing) ist auf schnelle, konsistente Einzeltransaktionen mit minimaler Latenz ausgelegt. OLAP (Online Analytical Processing) fokussiert auf komplexe Analysen, Aggregationen und priorisiert hohen Durchsatz über große Datenmengen.

Batch-Verarbeitung vs. Streaming
??
Bei der Batch-Verarbeitung werden Daten in großen Paketen zu festen Zeitpunkten verarbeitet (Fokus auf Durchsatz und sequenziellen Zugriff). Beim Streaming werden Daten fortlaufend und kontinuierlich verarbeitet (Fokus auf extrem niedrige Latenz und stabile Ingestion).

### UE02: Daten, Workloads und Zugriffsmuster

Warum reicht die "Datenform" (z.B. Tabelle, JSON, Objekt) allein nicht für eine Speicherentscheidung aus?
?
Die Datenform grenzt nur den Suchraum ein (Was liegt vor?), aber sie beantwortet nicht, wie die physische Organisation aussehen muss. Erst das Zugriffsmuster (Point Lookup, Range Scan etc.) entscheidet, welche Speicherlogik wirklich sinnvoll ist.

Welche physischen und wirtschaftlichen Konsequenzen drohen bei einer falschen Speicherwahl (ohne klares Zugriffsprofil)?
?
- Latenzspitzen bei Live-Abfragen.
- Teure Vollscans (Full Table Scans), die Ressourcen blockieren.
- Speicherkosten wachsen deutlich schneller als das eigentliche Datenvolumen.

Wie lautet die dreistufige Entscheidungslogik bei der Speicherwahl nach UE02?
?
1. **Welche Datenform liegt vor?** (z.B. Tabelle, Dokument, Objekt)
2. **Welches Zugriffsmuster dominiert?** (z.B. Point Lookup, Append, Range Scan, Batch Read)
3. **Welche Speicherlogik passt wirtschaftlich?** (z.B. DBMS, Scan-Store, Object/DFS)

Welche physischen Konsequenzen (Speicherlogik) ergeben sich zwingend aus einem Point Lookup?
?
Point Lookups erfordern eine Struktur, die das gezielte Nachschlagen minimiert. Die Konsequenz ist die Nutzung von Indexen oder schlüsselorientierter Ablage.

Ein ==Range Scan== verlangt als physische Konsequenz eine Ordnung, Sortierung oder Partitionierung, damit zusammenhängende Werte auch physisch benachbart effizient gelesen werden können.

Ein fortlaufendes Append-Zugriffsmuster (z.B. Event-Streams) bevorzugt eine ==sequentielle Ablage==, da dort das Neuschreiben von Daten den geringsten Overhead verursacht.

### UE03: Partitionierung und horizontale Skalierung

Nenne die drei primären Ziele der horizontalen Partitionierung.::1. Horizontale Skalierung, 2. Parallelität, 3. Begrenzung lokaler Kosten bei Abfragen.

Range-Sharding vs. Hash-Sharding
??
Beim Range-Sharding werden fachlich benachbarte Werte zusammen abgelegt, was ideal für Bereichsabfragen (Range Scans) ist, aber Hotspots provozieren kann. Beim Hash-Sharding werden Schlüssel durch eine Hashfunktion scheinbar gleichverteilt, was ideal für Point Lookups und gleichmäßige Lastverteilung ist, aber Bereichsabfragen zerstört.

Vergleiche Range-Sharding und Hash-Sharding bezüglich Zugriff, Lastbild und Rebalancing.
?
- **Range-Sharding**:
  - *Zugriff*: Sehr gut für Bereichsabfragen (Range Scans), da Wertebereiche zusammenbleiben.
  - *Lastbild*: Anfällig für Hotspots (z.B. bei zeitlichen Präfixen).
  - *Rebalancing*: Fachlich einfach nachvollziehbar, aber potenziell ungleichmäßig.
- **Hash-Sharding**:
  - *Zugriff*: Sehr gut für einzelne Schlüssel (Point Lookups); zerstört jedoch Bereichsabfragen.
  - *Lastbild*: Gleichmäßigere Lastverteilung, technisch robuster gegen Hotspots.
  - *Rebalancing*: Technisch komplexer (erfordert Umverteilung), aber gleichmäßiger.

Was ist ein Hotspot in verteilten Datenbanken und wie entsteht er?
?
Ein Hotspot entsteht, wenn die Zugriffs- oder Schreiblast nicht proportional verteilt ist und ein einzelner Knoten extrem überlastet wird. Er entsteht oft beim Range-Sharding durch hochaktuelle Zeitfenster, trendende Regionen oder "heiße Schlüssel".

Gegenmaßnahmen bei Hotspots sind feineres Schneiden der Partitionen, Rebalancing oder die Modifikation des Schlüssels durch ==Salting== oder technische Präfixe.

Wie funktioniert Consistent Hashing und welches Problem löst es?
?
Consistent Hashing bildet Schlüssel und Server-Knoten auf einen logischen Ring ab. Es löst das teure Rebalancing-Problem bei Skalierung: Fällt ein Knoten aus oder kommt einer hinzu, müssen nicht alle Daten, sondern nur die direkten Nachbar-Segmente auf dem Ring neu verteilt werden.

Virtuelle Nodes (VNodes) im Consistent Hashing Ring sorgen dafür, dass ein einzelner physischer Knoten ==mehrfach== repräsentiert wird, was die Lastverteilung feiner und robuster macht.

### UE04: Replikation, Konsistenz und CAP

Nenne die drei Hauptziele von Replikation in verteilten Systemen.::1. Ausfallschutz (Verfügbarkeit), 2. Leseentlastung, 3. Regionale Nähe (Latenzreduktion).

Strong Consistency vs. Eventual Consistency
??
Bei Strong Consistency sehen alle nachfolgenden Lesezugriffe nach einem Write sofort den exakt selben neuen Stand (erfordert teure Koordination). Bei Eventual Consistency dürfen Replikate vorübergehend abweichen; sie gleichen sich nur "irgendwann" an (priorisiert hohe Verfügbarkeit und geringe Latenz).

Was bedeutet die clientseitige Garantie "Read-Your-Writes"?
?
Das System garantiert nicht die sofortige globale Sichtbarkeit für alle, aber der Nutzer selbst kann seine eigene, soeben vorgenommene Änderung garantiert sofort wieder lesen (z.B. Profil-Update).

Was besagt das CAP-Theorem (im Störungsfall)?
?
Es besagt, dass bei einer auftretenden Netzwerkpartition (P) ein verteiltes System nur zwischen Konsistenz (C) und Verfügbarkeit (A) priorisieren kann. P ist keine Wahl, sondern die Störungslage.

Entscheide für die folgenden drei Szenarien, ob im Falle einer Netzwerkpartition (Partition-Fall) eher Konsistenz (C) oder Verfügbarkeit (A) priorisiert werden sollte: 1) Zahlungsbuchung, 2) Produktkatalog, 3) Social Feed.
?
1. **Zahlungsbuchung**: Konsistenz (C). Falsche Doppelbuchungen oder inkonsistente Kontostände verursachen direkten wirtschaftlichen Schaden.
2. **Produktkatalog**: Verfügbarkeit (A). Vorübergehend veraltete Preise oder Produktbeschreibungen sind tolerierbar, solange der Shop erreichbar bleibt.
3. **Social Feed**: Verfügbarkeit (A). Ein leicht verzögerter Feed ist unproblematisch; der Dienst darf deshalb nicht für Nutzer ausfallen.

ACID vs. CAP
??
ACID definiert den Qualitätsrahmen und die Korrektheit für lokale Einzeltransaktionen. CAP beschreibt das Verhalten und die Priorisierung eines verteilten Systems bei einer Kommunikationsstörung (Netzwerkabbruch).

### UE05: Storage-Paradigmen im Überblick

Speicherparadigmen nach Adressierung::Block Storage: Offset/Blockadresse. File Storage: Pfad/Verzeichnis. Object Storage: Objekt-ID + Metadaten. Key-Value: Schlüssel.

Wie ordnen sich die Storage-Paradigmen auf dem Spektrum zwischen Infrastrukturbezug und Anwendungsbezug ein?
?
`[Infrastrukturbezug] Block Storage -> File Storage -> Object Storage -> Key-Value Stores -> Database-near Systems [Anwendungsbezug]`
Mit zunehmendem Anwendungsbezug wächst die Bedeutung der fachlichen Datenmodellierung und die Abfragesemantik, während auf der Infrastrukturseite rohe Datenblöcke und physische Schnittstellen dominieren.

Warum ist ein Object Store kein "modernes Dateisystem"?
?
Weil er keine tiefen Hierarchien oder Dateisystemoperationen besitzt. Er nutzt einen flachen Namensraum und ist auf einfache API-Operationen für große BLOBs mit Metadaten ausgelegt, getrennt von jeglicher Verzeichnis-Semantik.

Vergleiche File Storage, Object Storage und Datenbanken (DB) bezüglich ihrer Adressierung, Metadaten und primären Stärke.
?
- **Adressierung**:
  - *File*: Pfad/Verzeichnisbaum (POSIX-Standard).
  - *Object*: Eindeutige Objekt-ID in einem flachen Namensraum.
  - *DB*: Abfragen (Query / Modell) über Indizes.
- **Metadaten**:
  - *File*: Dateisystemattribute (Größe, Rechte, Zeitstempel).
  - *Object*: Beliebige benutzerdefinierte Metadaten am Objekt (Key-Value-Paare).
  - *DB*: Streng modelliertes und indiziertes Schema.
- **Primäre Stärke**:
  - *File*: Vertraute, hierarchische Dateisicht.
  - *Object*: Extreme horizontale Skalierung für große unstrukturierte Daten (BLOBs).
  - *DB*: Mächtige Abfragesemantik und relationale Integrität.

### UE08: Motivation und Konzept von NoSQL

Was waren die drei zentralen Treiber für die Entstehung von NoSQL?::1. Skalierungsdruck durch Last/Menge, 2. Latenz und globale Verteilung, 3. Flexible Datenformen.

Was bedeutet das verteilte Denkmodell BASE?
?
Basically Available, Soft State, Eventually Consistent. Es priorisiert in verteilten Systemen Verfügbarkeit und toleriert vorübergehend abweichende, "weiche" Sichtstände mit der Garantie auf spätere Angleichung.

Vergleiche ACID und BASE bezüglich Fokus, Sichtbarkeit und typischem Einsatz (Fit).
?
- **ACID**:
  - *Fokus*: Transaktionskorrektheit und absolute lokale Datenintegrität.
  - *Sichtbarkeit*: Sofortige, global konsistente und eindeutige Sicht (Strong Consistency).
  - *Typischer Fit*: Kritische Geschäftsdaten, z.B. Zahlungsbuchungen.
- **BASE**:
  - *Fokus*: Globale Verfügbarkeit und verteilte Lasttoleranz.
  - *Sichtbarkeit*: Zeitversetzte Angleichung der Kopien (Eventual Consistency), stale reads möglich.
  - *Typischer Fit*: Webnahe Workloads mit massiver Last, z.B. Caches oder Social Feeds.

Warum greifen NoSQL-Systeme oft auf Denormalisierung zurück?
?
Weil verteilte Joins in hochskalierten Systemen extrem teuer sind. Informationen, die häufig gemeinsam gelesen werden, werden näher zusammengelegt (denormalisiert), um schnelle, folgezugriffsfreie Leseoperationen zu garantieren.

Welche Trade-offs ergeben sich bei der Denormalisierung im Vergleich zur Normalisierung?
?
- **Vorteil**: Vermeidung teurer verteilter Joins; Daten werden lesebereit und zusammenhängend abgelegt, was Leseoperationen beschleunigt.
- **Nachteil**: Erhöhte Redundanz und deutlich aufwendigere Aktualisierungen (Updates), da Datenänderungen an mehreren Stellen synchronisiert werden müssen.

Nenne die 4 Hauptfamilien von NoSQL-Systemen.::Key-Value, Document, Wide Column, Graph.

### UE09: Key-Value Stores

Auf welche API-Operationen ist ein Key-Value Store fachlich verengt?::put(k,v), get(k), delete(k).

Was sind die typischen Stärken und Grenzen eines Key-Value Stores?
?
Stärken: Extrem schnelle Direktzugriffe bei kurzem Pfad und hervorragende Verteilbarkeit (Skalierung) über den Schlüssel.
Grenzen: Das Modell versagt, wenn die Suchfrage den Key noch nicht kennt (Range Queries, komplexe Suchen, Relationen sind extrem aufwendig).

Wie werden Schlüssel (Keys) und Knoten (Nodes) beim Consistent Hashing einander zugeordnet?
?
Sowohl Serverknoten als auch Schlüssel werden gehashed und auf einem logischen Kreis (Ring) platziert. Ein Schlüssel gehört dem ersten Knoten, auf den man trifft, wenn man im Uhrzeigersinn (clockwise) wandert.

Wie unterscheidet sich Last-Write-Wins (LWW) von der Versionierung (z.B. mittels Vektoruhren) bei der Konfliktbehandlung in Key-Value Stores?
?
- **Last-Write-Wins (LWW)**: Der Konflikt wird automatisch anhand des jüngsten physischen Zeitstempels gelöst. Dies ist einfach und schnell, birgt jedoch das Risiko eines stillschweigenden Datenverlusts.
- **Versionierung / Vektoruhren**: Konflikte werden explizit im Datenmodell als Verzweigung (v2a, v2b) sichtbar gemacht. Das System überlässt das Zusammenführen (Merge) der Anwendung oder dem Nutzer, was Datenverlust verhindert.

Wofür sind Key-Value Stores der typische "Fit" (Use Cases)?::Session Stores, Caches (z.B. Warenkorb), Profilzustände und schnelle Konfigurationswerte.

### UE10: Document Stores

Was ist das zentrale Architekturprinzip hinter Document Stores?
?
Die fachliche Einheit wird zur Zugriffseinheit. Ein Dokument fasst Informationen (z.B. Bestelldaten) so zusammen, dass sie gemeinsam als eine Einheit gelesen und geschrieben werden können, was teure Joins erspart.

Einbettung vs. Referenzierung in Document Stores
??
Einbettung ist sinnvoll, wenn die Teile eng zusammengehören und im Zugriff fast immer gemeinsam gelesen werden (z.B. Bestellung und Positionen). Referenzierung ist sinnvoll, wenn die Teile groß sind, eigenständig wachsen oder von vielen Dokumenten geteilt werden (z.B. Kundenstammsatz).

Nach welchen drei Leitfragen entscheidet man im Dokumentmodell über die Strukturierung (Einbettung vs. Referenzierung)?
?
1. **Welche Teile werden fast immer gemeinsam gelesen und geschrieben?** (Spricht für Einbettung)
2. **Welche Teile wachsen stark an (unbounded) oder werden separat gepflegt?** (Spricht für Referenzierung)
3. **Wo helfen strukturierte Indizes, um Vollscans zu vermeiden?**

Warum benötigen Document Stores trotz ihres flexiblen Modells zwingend Indizes?
?
Weil flexible Strukturen bei Abfragen sonst zu massiven Vollscans führen. Die zentralen Query-Pfade müssen über Indizes vorbereitet werden, um Performance zu gewährleisten.

### UE11: Wide Column Stores

Wie organisiert ein Wide Column Store die Daten logisch?
?
Er organisiert die Daten nicht in homogenen Tabellen, sondern über einen dominanten ==Row Key== und logisch getrennte ==Column Families==.

Aus welchen Bausteinen besteht die logische Identifikationsstruktur einer Zelle (Cell) in einem Wide Column Store?
?
Eine Zelle wird durch ein mehrdimensionales Schlüssel-Tupel identifiziert:
`(Row Key, Column Family, Column Qualifier, Timestamp) -> Value`
Der Zeitstempel (Timestamp) ermöglicht die automatische Versionierung von Zellwerten.

Wide Rows und Sparse Columns
??
Wide Rows: Zu einem Schlüssel können sehr viele zusammenhängende Werte gespeichert werden (ideal für Zeitreihen). Sparse Columns: Nicht jede Zeile muss alle Felder der Spaltenfamilie enthalten; leere Felder kosten keinen Platz und erzwingen keine uniforme Tabellenform.

Warum ist die Wahl des Row Keys bei Wide Column Stores die kritischste Designentscheidung?
?
Weil der Row Key direkt entscheidet, wie die Daten physisch verteilt werden und ob spätere Bereichsabfragen (Range Scans) effizient laufen. Ein falscher Row Key erzeugt Hotspots oder zwingt zu ineffizienten Vollscans.

Vergleich HBase vs. Cassandra::HBase ist eher mastergestützt und eng mit dem Hadoop/HDFS-Ökosystem verbunden. Cassandra ist dezentral, peer-to-peer orientiert und stark auf weltweite Verteilung und Replikation fokussiert.

### UE12: Konsistenzmodelle in NoSQL-Systemen

Wofür stehen die Parameter N, R und W in der Quorum-Logik?
?
N = Gesamtzahl der Replikate. W = Anzahl der Replikate, die einen Write bestätigen müssen. R = Anzahl der Replikate, die für einen Read befragt werden.

Beurteile folgende Quorum-Konfigurationen hinsichtlich der Gewährleistung von Strong Consistency (R + W > N): 1) N=3, R=2, W=2; 2) N=5, R=1, W=3; 3) N=5, R=2, W=2.
?
1. **N=3, R=2, W=2**: 2 + 2 > 3 (4 > 3) -> **Ja**. Der Lesevorgang überschneidet sich garantiert mit mindestens einem geschriebenen Replikat.
2. **N=5, R=1, W=3**: 1 + 3 > 5 (4 > 5) -> **Nein**. Es kann vorkommen, dass der Read ein Replikat erwischt, das den Schreibvorgang noch nicht erhalten hat (Stale Read).
3. **N=5, R=2, W=2**: 2 + 2 > 5 (4 > 5) -> **Nein**. Keine Überlappung zwischen Lese- und Schreibquoren garantiert.

Warum garantiert die Quorum-Regel R + W > N meist einen aktuellen Read?
?
Weil sie einen zwingenden Schnitt (Überlappung) zwischen der Gruppe der schreibenden und der Gruppe der lesenden Replikate erzwingt. Mindestens ein befragtes Replikat beim Read muss den letzten Write gesehen haben.

Was macht die Konfliktlösungsregel "Last-Write-Wins" und was ist ihr architektonischer Preis?
?
Sie löst Konflikte extrem schnell auf, indem immer der jüngste Zeitstempel gewinnt. Der Preis ist möglicher Informationsverlust, da vorherige, eventuell berechtigte parallele Updates stillschweigend überschrieben werden.

Warum ist Konsistenz (z.B. Eventual Consistency) letztlich eine fachliche und keine rein technische Entscheidung?
?
Weil die Akzeptanz veralteter Daten vom konkreten fachlichen Kontext abhängt. Bei Zählern, Social-Media-Feeds oder Likes ist eine verzögerte Aktualisierung unkritisch (EC). Bei Finanztransaktionen oder Sitzplatzbuchungen hingegen führt Inkonsistenz zu Doppelbuchungen und realem finanziellem Schaden, weshalb Strong Consistency zwingend erforderlich ist.

### UE13: NoSQL-Vergleich und Use Cases

Welche typischen Use Cases ordnet man den 4 NoSQL-Typen als Stärke zu?
?
Key-Value: Schnelle Session-Stores und Caches. Document: Produktkataloge, CMS, verschachtelte Objekte. Wide Column: Zeitreihen, IoT-Sensordaten, Log-Events. Graph: Soziale Netzwerke, Empfehlungssysteme (Routing), Betrugserkennung.

Fasse die Stärken und typischen Schwächen der 4 NoSQL-Familien in je einem Satz zusammen.
?
- **Key-Value**:
  - *Stärke*: Extrem schnelle Lese- und Schreibzugriffe über einen eindeutigen Schlüssel.
  - *Schwäche*: Ungeeignet für Bereichsabfragen, komplexe Datenstrukturen oder Verknüpfungen.
- **Document**:
  - *Stärke*: Speichert fachlich zusammenhängende, variable Einheiten direkt ab, was Joins einspart.
  - *Schwäche*: Ungeeignet für hochgradig vernetzte Datenbeziehungen (Querbeziehungen) oder transaktionale Konsistenz über viele Dokumente.
- **Wide Column**:
  - *Stärke*: Exzellent für massiven Schreibdurchsatz und zeitlich geordnete Bereichsscans (z.B. Zeitreihen).
  - *Schwäche*: Ungeeignet für Ad-hoc-Analysen über Spalten, die nicht Teil des Row Keys sind.
- **Graph**:
  - *Stärke*: Optimal für das Traversieren komplexer Beziehungen und Pfade zwischen Objekten.
  - *Schwäche*: Ungeeignet für einfache Key-Value-Massenzugriffe oder flache, unstrukturierte Großdaten.

An welchen Grenzen kippen die einzelnen NoSQL-Modelle in Mehrarbeit um?
?
Key-Value: Sobald über andere Kriterien als den Key gefiltert werden muss. Document: Sobald komplexe, netzartige Querbeziehungen dominieren. Wide Column: Sobald Ad-hoc Queries jenseits des Row-Keys nötig sind. Graph: Wenn kaum Beziehungen traversiert werden und reine Objektzugriffe dominieren.

Wie baut man einen kompakten Entscheidungsgang für NoSQL-Fallfragen auf?
?
1. Dominierende Fachfrage/Workload benennen. 2. Festlegen, welche Einheit gemeinsam gelesen/geschrieben wird. 3. Den passenden NoSQL-Typ ableiten, der diese Einheit natürlich trägt. 4. Die Alternative abgrenzen oder Grenzen benennen.

### UE14: Motivation und Anforderungen an Distributed File Systems

Nenne die 4 Kernanforderungen an ein Distributed File System (DFS).::1. Horizontale Skalierung, 2. Hoher Durchsatz für paralleles Lesen/Schreiben, 3. Fehlertoleranz durch Replikation, 4. Verteilte Metadatenorganisation.

Warum verwendet HDFS standardmäßig sehr große Blockgrößen (z.B. 128 MB oder 256 MB)?
?
- **Minimierung der Metadaten**: Jedes Block-Metadatenelement belegt Speicher im RAM des NameNodes. Größere Blöcke bedeuten weniger Blöcke insgesamt und somit weniger RAM-Bedarf auf dem NameNode.
- **Sequenzieller Durchsatz**: Die Latenz für den Festplatten-Seek wird amortisiert; HDFS kann große sequentielle Transfers durchführen, was ideal für Batch-Verarbeitung ist.
- **Reduzierung des Netzwerk-Overheads beim Client-Zugriff**: Der Client muss seltener beim NameNode nach neuen Blockplatzierungen fragen.

Was ist der Unterschied zwischen Kapazität und Durchsatz in der DFS-Motivation?
?
Studierende denken oft nur an Speicherkapazität (Platz). Ein DFS ist aber primär dafür da, gigantischen Durchsatz zu erzeugen, damit extrem große Datenmengen schnell parallel gelesen und verarbeitet werden können.

Was versteht man unter Datenlokalität und warum ist sie ein Leistungsprinzip?
?
Rechenlogik wird möglichst zu den Datenknoten gebracht, statt die Daten zum Rechenknoten zu schicken. Wenn der Rechenknoten den Block bereits lokal hält, spart das immens Netzwerkbandbreite und Latenz.

Was unterscheidet ein Distributed File System (DFS) wie HDFS konzeptionell von einem Network Attached Storage (NAS)?
?
- **NAS**: Ein zentraler Speicherort, der Dateien über ein Netzwerk bereitstellt (Single Point of Failure, skalierungsbeschränkt).
- **DFS**: Verteilt Blöcke einer Datei redundant über viele physische Knoten, organisiert die Ausfallsicherheit über Replikate und ermöglicht paralleles Lesen/Schreiben sowie computenahe Verarbeitung (Datenlokalität).

### UE15: HDFS Architektur im Detail

Beschreibe die 3 Hauptrollen in HDFS (Client, NameNode, DataNode).
?
- Client: Startet Lese- oder Schreibvorgänge, ist die anfragende Seite.
- NameNode: Verwaltet Metadaten und Platzierungsentscheidungen, speichert selbst aber KEINE Blockdaten.
- DataNode: Speichert die tatsächlichen Blöcke und transportiert die physischen Datenströme.

Was ist der fundamentale Unterschied zwischen Metadatenpfad und Datenpfad in HDFS?
?
Der Metadatenpfad verläuft über den NameNode und liefert nur Orientierungs- oder Platzierungswissen. Der Datenpfad meint die physischen Byte-Ströme und läuft direkt zwischen Client und den DataNodes.

Skizziere den HDFS Write Path in der korrekten Reihenfolge.
?
1. Client meldet beim NameNode eine neue Datei/Block an (Metadatenpfad).
2. NameNode plant Platzierung und nennt Ziel-DataNodes (Metadatenpfad).
3. Client sendet Datenstrom zum ersten DataNode (Datenpfad).
4. Block wird in einer Replikationskette an weitere DataNodes gereicht (Datenpfad).
5. Kette bestätigt Vollständigkeit, Schreibvorgang abgeschlossen (Datenpfad).

Wie funktioniert der Datenübertragungsfluss (Pipeline Write) während des HDFS Write Path zwischen Client und den DataNodes?
?
Der Client streamt die Daten eines Blocks in Form kleiner Pakete (z.B. 64 KB) an den ersten DataNode der vom NameNode vorgegebenen Replikationskette. Dieser erste DataNode schreibt das Paket lokal und leitet es sofort an den zweiten DataNode weiter (Pipelining), welcher es wiederum an den dritten sendet. Erst wenn die Bestätigung (ACK) rückwärts durch die Pipeline gelaufen ist, gilt das Paket als erfolgreich geschrieben.

Wie funktioniert der HDFS Read Path?
?
Der Client holt sich zuerst die Block-Orte beim NameNode (Metadaten). Anschließend liest er die Blockdaten direkt vom entsprechenden DataNode (Datenpfad).

### UE16: HDFS Eigenschaften, Fehlertoleranz und Grenzen

Nenne drei zentrale Fehlertoleranz-Mechanismen in HDFS und ihren Zweck.
?
1. Heartbeats: Erkennen von DataNode-Ausfällen.
2. Block Reports: Halten das Metadatenbild des NameNodes über die real liegenden Blöcke aktuell.
3. Replikation: Sichert die Verfügbarkeit und erlaubt den Neuaufbau fehlender Blöcke.

Welche drei Mechanismen verwendet HDFS zur Erkennung und Behandlung von Knoten- und Datenfehlern im laufenden Betrieb?
?
- **Heartbeats**: DataNodes senden periodisch Signale an den NameNode. Bleiben diese aus, markiert der NameNode den Knoten als tot.
- **Block Reports**: DataNodes senden regelmäßige Berichte über alle physisch bei ihnen liegenden Blöcke, damit der NameNode die Blockzuordnung verifizieren kann.
- **Prüfsummen (Checksums)**: Clients berechnen beim Schreiben Prüfsummen und verifizieren diese beim Lesen, um stille Datenkorruption (Bit Rot) auf DataNodes zu erkennen.

Rack Awareness::Der NameNode plant Replikate bewusst über verschiedene Racks hinweg, damit der Stromausfall eines gesamten Racks nicht zum kompletten Datenverlust führt.

Warum sind "Small Files" in HDFS ein massives Architekturproblem?
?
Da HDFS auf große Blöcke und sequenziellen Durchsatz ausgelegt ist, erzeugen Millionen kleinster Dateien einen gigantischen Metadatenaufwand im RAM des NameNodes, ohne dass die Vorteile der Blockverarbeitung (Durchsatz) je ausgespielt werden können.

Für welche Zugriffe ist HDFS ungeeignet?
?
Für Random Writes (häufige unvorhersehbare kleine Aktualisierungen) und für Szenarien, die auf extrem niedrige Einzellatenzen angewiesen sind. HDFS ist für Batch-Durchsatz gebaut, nicht für interaktive Punktzugriffe.

### UE17: Object Stores

Nenne die drei Grundbausteine eines Object Stores.::Bucket (logischer Namensraum), Objekt (Inhalt + Schlüssel) und Metadaten (beschreibende Informationen).

Wie adressiert ein Object Store Daten im Gegensatz zu einem Dateisystem?
?
Er nutzt einen flachen Namespace mit eindeutigen Objekt-IDs (Schlüsseln) über API/HTTP, anstatt eines tief verschachtelten, hierarchischen Verzeichnisbaums.

Aus welchen architektonischen Gründen lässt sich Object Storage im Vergleich zu klassischen Dateisystemen (POSIX) nahezu unbegrenzt horizontal skalieren?
?
- **Flacher Namensraum**: Es gibt keine Verzeichnishierarchien. Der Namensraum ist eine flache Schlüssel-Wert-Struktur, wodurch teure Verzeichnissperren (Locking) entfallen.
- **Einfaches API-Modell**: Die zustandslosen HTTP-Operationen (GET, PUT, DELETE, LIST) erlauben eine einfache Verteilung der Anfragen über Load Balancer und Gateways.
- **Lose Kopplung**: Objekte sind unabhängige Einheiten. Änderungen an einem Objekt erfordern keine globalen Metadaten-Updates über andere Dateien hinweg.

Welche 4 Kern-API-Operationen prägen die Logik des Object Stores?::PUT (Schreiben), GET (Lesen), LIST (Suchen nach Prefixen), DELETE (Löschen).

Unterschied zwischen Durability und Verfügbarkeit in der Cloud.
??
Durability (Dauerhaftigkeit) misst, wie unwahrscheinlich es ist, dass die Daten physisch verloren gehen (z.B. 99.999999999%). Verfügbarkeit (Availability) misst, wie oft der Dienst für Anfragen erreichbar und nutzbar ist (z.B. 99.9%).

### UE18: DFS vs Object Store und moderne Architekturen

Wie vergleicht man DFS und Object Store hinsichtlich des Architekturziels?
?
DFS (wie HDFS) ist stark für computenahe, batch-orientierte Verarbeitung mit Datei-/Blocklogik. Object Stores sind stark als offene, entkoppelte Plattform- und Rohdatenbasis (Data Lake) mit flacher API- und Skalierungslogik.

Vergleiche ein Distributed File System (wie HDFS) und Object Storage bezüglich der Kopplung von Storage und Compute sowie der Eignung für Multi-Engine-Architekturen.
?
- **HDFS (DFS)**:
  - *Kopplung*: Eng an Compute gekoppelt (Datenlokalität), typischerweise im selben physikalischen Cluster betrieben.
  - *Eignung*: Ideal für eine einzelne, dedizierte Verarbeitungsengine (z.B. ein MapReduce/Spark-Cluster), die massiven Batch-Durchsatz benötigt.
- **Object Storage**:
  - *Kopplung*: Konsequent von Compute entkoppelt. Speicher und Rechenleistung skaliert und bezahlt man separat.
  - *Eignung*: Dient als zentrale, offene Plattformbasis (Data Lake), auf die viele verschiedene, unabhängige Teams und Engines (z.B. Spark, Trino, Flink) gleichzeitig zugreifen können.

Was ist der Data Lake als Speicherprinzip?
?
Er ist kein einzelnes Produkt, sondern ein Architekturprinzip. Rohdaten werden zentral, offen und günstig abgelegt (meist in Object Stores), sodass Speicher und Compute entkoppelt sind und verschiedene Teams/Engines darauf zugreifen können.

Lakehouse::Die Verbindung aus der günstigen, offenen Speicherbasis eines Data Lakes mit den Strukturen, Transaktionsregeln und der Governance eines Data Warehouses.

### UE19: Hadoop-Ökosystem im Überblick

Welche 4 Kernbausteine bilden das klassische Hadoop-Ökosystem und was tun sie?
?
- HDFS: Verteilte Speicherbasis.
- YARN: Ressourcensteuerung und Laufzeitkoordination (Plant Container).
- MapReduce: Verarbeitungslogik für Batch-Jobs.
- Metastore: Hält Strukturwissen und ermöglicht logische Tabellenblicke auf strukturlose Dateien.

In welcher Abfolge durchläuft ein Job das Hadoop-Ökosystem?
?
Daten liegen in HDFS $\rightarrow$ Job wird angestoßen $\rightarrow$ YARN organisiert die Laufzeitressourcen $\rightarrow$ MapReduce-Logik verarbeitet die Daten $\rightarrow$ Output landet wieder in HDFS.

### UE21: MapReduce als Batch-Paradigma

Skizziere den Ablauf von MapReduce (die 3 Phasen).
?
1. Map: Eingabedaten werden lokal gelesen und in logische Teilresultate (Key-Value-Paare) überführt.
2. Shuffle: Daten mit gleichen Schlüsseln werden über das Netzwerk neu gruppiert und geordnet (teuer!).
3. Reduce: Die zusammengehörigen Werte werden verdichtet und zum Endergebnis aggregiert.

Warum ist die Shuffle-Phase in der verteilten Verarbeitung der zentrale Engpass?
?
Weil hier die Datenlokalität aufgegeben werden muss. Alle Werte desselben Schlüssels müssen über das Netzwerk bewegt und umsortiert werden, was massive Netzwerklasten erzeugt.

Wofür ist MapReduce ideal geeignet und wofür nicht?
?
Ideal für extrem große, klar umrissene Batch-Jobs (z.B. tägliche Log-Auswertungen), die keine Eile haben. Ungeeignet für interaktive Suchen, extrem niedrige Latenzanforderungen oder stark iterative Algorithmen (z.B. Machine Learning).

### UE24: Vergleich und Entscheidung

Welche 4 Kriterien dienen in UE24 als Grundlage für Speicher-/Plattformvergleiche?::1. Zugriffsmuster, 2. Latenz, 3. Datenform, 4. Flexibilität.

Warum darf man Spark nicht einfach als "besseres MapReduce" bezeichnen?
?
Der Unterschied liegt in der Flexibilität des Verarbeitungsmodells. MapReduce zwingt jede Aufgabe in die starre 2-Phasen-Pipeline. Spark kann komplexere Arbeitspläne (DAGs) mit vielen Operatoren und In-Memory-Verarbeitung aufbauen und ist flexibler für iteratives Rechnen.

Einordnung: HBase vs. Spark vs. HDFS
??
- HDFS: Speicherbasis für große Batch-Mengen.
- Spark: Verarbeitungs-Engine für flexible Analysen.
- HBase: Zugriffsorientierte Datenbank für punktgenaues Nachschlagen in großen, strukturierten Beständen.

### UE26: Klausurtraining & Beispielfragen

Nach welchem 4-Schritte-Gerüst baut man eine perfekte Klausurantwort in Big Data Storage auf?::1. Aufgabe charakterisieren, 2. Fachliches Kriterium nennen, 3. System einordnen, 4. Entscheidung explizit begründen.

Welcher Operator zwingt dazu, ein gemeinsames Merkmal für mindestens zwei Gegenstände zu finden?::Der Operator "vergleichen" (es reicht keine reine Aufzählung separater Listen).

Ordne folgendem Szenario das korrekte Zugriffsmuster zu: "Live-Preisabfrage in einem Onlineshop".
?
==Point Lookup==. Begründung: Key-basierter Einzelzugriff mit Erwartung an sofortige Antwort.

Ordne folgendem Szenario das korrekte Zugriffsmuster zu: "Tagesreport über alle Verkäufe eines Monats".
?
==Range Scan / Batch Read==. Begründung: Ein großer Zeitraum wird sequentiell gelesen und aggregiert.

Ordne folgendem Szenario das korrekte Zugriffsmuster zu: "Eingehende Sensorwerte einer Produktionsanlage".
?
==Append== (mit späteren Range Scans). Begründung: Kontinuierlicher Eventstrom, der fortlaufend angehängt wird.

Ordne folgendem Szenario das korrekte Zugriffsmuster zu: "Abruf eines archivierten Vertragsscans".
?
==Object Read==. Begründung: Großes, unveränderliches Objekt, das selten und als Ganzes gelesen wird.

Welcher NoSQL-Typ passt zu einem Nutzerprofil (Präferenzen, Watchlist), das immer als Ganzes geladen wird?
?
Typ: Document Store.
Stärke: Profil wird als fachliche Einheit gelesen.
Grenze: Querbeziehungen (Freunde finden) sind teuer.
Preis der Fehlwahl: Bei Key-Value ginge die innere Zugriffsstruktur verloren.

Welches Storage-Paradigma passt zu Backups von Server-Snapshots (riesig, unveränderlich, hoher Durability-Bedarf)?
?
Object Storage. Die Adressierung über flachen Namespace/ID ist ideal für große Objekte, das Zugriffsmuster zielt genau auf hohe Durability bei seltenem Lesen ab. (Block Storage wäre hier teuer und überdimensioniert).

Beurteile die Aussage: "HDFS ist veraltet, seit es Object Stores gibt."
?
Die Aussage ist falsch. Beide verfolgen unterschiedliche Ziele: HDFS ist eng mit Compute gekoppelt und auf Batch-Verarbeitung ausgelegt. Object Stores sind entkoppelte, weltweite Speicherbasen für unterschiedliche Plattform-Engines.

Warum braucht eine Lernplattform oft eine Mischarchitektur (z.B. Document Store für Kurse und Wide Column für Aktivitätslogs)?
?
Weil unterschiedliche Bedarfe herrschen: Ein Kurs ist eine fachlich zusammenhängende Einheit (Document). Die Log-Aufrufe sind jedoch riesige Ereignisströme, die geordnet nach Zeit/Nutzer gescannt werden müssen (Wide Column). Ein einzelnes System würde bei einem der beiden Bedarfe massiv Leistung einbüßen.


---
# Ergänzungen

### Grundlagen & Datenmodelle

Wodurch wird Big Data klassischerweise charakterisiert (Die 5 V's)?
?
Durch Volume (Datenmenge), Variety (Datenvielfalt), Velocity (Geschwindigkeit), Veracity (Wahrhaftigkeit/Datenqualität) und Value (unternehmerischer Wert).

Welche physischen Speicherfolgen ergeben sich aus den drei zentralen Datenformen (tabellarisch, semi-strukturiert, unstrukturiert)?
?
- Tabellarisch: Festes Schema und Indizes für schnelle, gezielte Einzelzugriffe.
- Semi-strukturiert: Flexible Struktur und selektive Indizes, da nicht zwingend jedes Feld in jedem Datensatz auftaucht.
- Unstrukturiert: Speicherung als reine Objektablage (grosse Dateien), wobei die fachliche Suchlogik in separate Metadaten ausgelagert wird.

Synchrone vs. Asynchrone Replikation
??
- Synchrone Replikation: Der Schreibvorgang gilt erst als erfolgreich, wenn Replikate bestätigt haben. Das erzeugt eine höhere Latenz, bietet aber sofortige Sicherheit und starke Konsistenz.
- Asynchrone Replikation: Der Schreibvorgang wird dem Nutzer sofort bestätigt, die Replikate ziehen erst im Hintergrund nach. Das ist deutlich schneller, führt aber zu einer vorübergehend uneinheitlichen Sicht und birgt ein Verlustrisiko bei einem Crash.

Wo liegen die spezifischen architektonischen Grenzen von Block Storage und File Storage?
?
- Block Storage: Arbeitet extrem nah am Betriebssystem und besitzt daher keinerlei Dateiansicht und keine fachliche Struktur.
- File Storage: Bietet eine vertraute Ordnerstruktur (ideal für Teamdaten), jedoch bremsen globale Verzeichnisbäume und das Verwalten des Namensraums die Skalierung bei extrem großen Datenmengen massiv aus.


### NoSQL Deep-Dive (LSM-Trees & Konsistenz)

Wie funktioniert der Schreibprozess über LSM-Trees (Log-Structured Merge Trees) bei Wide Column Stores, um extrem hohe Schreib-Performance zu erzielen?
?
Schreibvorgänge (Writes) werden zunächst extrem schnell im RAM (Arbeitsspeicher) in einer sogenannten ==MemTable== erfasst. Wenn dieser Speicher voll ist, werden die Daten "append-only" und sequentiell als unveränderliche ==SSTable== auf die Festplatte geschrieben.

Welcher Hintergrundprozess ist bei der Nutzung von LSM-Trees zwingend notwendig, um die Lese-Performance (Read-Performance) langfristig zu erhalten?
?
Die ==Compaction== (Kompaktierung). Da Daten nur sequentiell angehängt werden, führt dieser Hintergrundprozess die vielen kleinen SSTables auf der Festplatte regelmäßig zusammen, sortiert sie und bereinigt physisch gelöschte oder überschriebene Daten.

Welche Methode zur Konfliktlösung (neben der "Last-Write-Wins"-Regel) macht bei parallelen Schreibvorgängen in Key-Value Stores Konflikte explizit sichtbar?::Die Versionierung (beispielsweise durch Vektoruhren).

Welches Konsistenzmodell verhindert, dass ein Nutzer bei aufeinanderfolgenden Lesezugriffen in eine ältere Sicht zurückfällt (Rücksprünge)?::Monotonic Reads.

Wie unterscheiden sich Read Repair und Write Repair bei der aktiven Konfliktbehandlung im Eventual Consistency Modell?
?
- Read Repair: Abweichungen zwischen Replikaten werden direkt während eines Lesezugriffs (Read) erkannt und sofort ausgeglichen.
- Write Repair: Das System hilft aktiv dabei, Replikate nach einem Schreibvorgang (Write) zeitversetzt zu aktualisieren und anzugleichen.


### DFS, Object Stores & Hadoop-Ökosystem

Welcher spezifische Fehlertoleranz-Mechanismus (neben Heartbeats, Block Reports und Replikation) dient in HDFS der aktiven Erkennung von physisch defekten Daten auf der Festplatte?::Block Checks.

Warum sind LIST-Operationen bei Object Stores aus Leistungssicht oft problematisch?
?
Das Auflisten von Objekten (LIST) über extrem große, flache Namensräume (Buckets) hinweg ist oft eine aufwendige Systemleistung und deutlich teurer sowie langsamer als der gezielte Einzelabruf eines Objekts per ID (GET).

Worin besteht im Hadoop-Ökosystem der architektonische Unterschied zwischen der reinen "Datei-Sicht" und der "Tabellen-Sicht"?
?
In der Datei-Sicht liegen die reinen, strukturlosen Rohdaten (z.B. als CSV oder Parquet) direkt im HDFS. Erst die Tabellen-Sicht, welche durch den ==Metastore== erzeugt wird, legt eine nutzbare Logik und ein Schema über exakt diese rohen Dateien und erlaubt strukturierte Abfragen.

Welche Nachteile ergeben sich bei Document Stores durch die oft gewählte Einbettung (Denormalisierung) im Hinblick auf Datenpflege?
?
Mehrfachupdates und Transaktionen werden schwierig. Da redundante Daten (z. B. eine Adresse) oft in vielen Dokumenten eingebettet sind, erfordert eine Aktualisierung das fehlerfreie Ändern vieler Dokumente, was klassische Transaktionsgarantien erschwert.

Konsistenzmodelle sind oft Fachentscheidungen. Nenne typische Beispiele für Daten, bei denen Eventual Consistency akzeptabel ist, und solche, wo Strong Consistency kritisch ist.
?
- Akzeptabel (Eventual Consistency): Likes, Zähler, Social Media Feeds (vorübergehende Abweichungen richten keinen wirtschaftlichen Schaden an).
- Kritisch (Strong Consistency): Zahlungen, Sitzplatzreservierungen (Gefahr von Doppelbuchungen oder finanziellem Verlust).

Warum sind folgende drei Systemzuordnungen klassische Anti-Patterns? 1. Spark als Speicher nutzen. 2. HDFS für schnellen Zeilenzugriff nutzen. 3. HBase für freie Großanalysen nutzen.
?
1. Spark ist eine reine Processing-Engine (Verarbeitung) im Speicher (In-Memory) und keine persistente Speicherbasis (Storage).
2. HDFS ist für gewaltigen Batch-Durchsatz und große Blöcke gebaut, nicht für punktgenaue Point-Lookups mit niedriger Latenz.
3. HBase ist zugriffsorientiert (Point Lookups über Row Key). Für spontane, freie Analysen (Vollscans) über unvorbereitete Pfade ist es die falsche Wahl.

Ordne den ersten vier Ebenen des Big-Data-Stacks (Storage, Syntax, Datenmodell, Verarbeitung) die jeweiligen Architekturfragen (Ort, Format, Struktur, Nutzung) sowie typische Technologien zu.
?
- Storage (Ort): Wo liegen die Rohdaten? (z.B. HDFS, Object Store)
- Syntax (Format): Wie sind sie codiert? (z.B. CSV, Parquet)
- Datenmodell (Struktur): Wie ist die fachliche Sicht? (z.B. Tabelle, Dokument, Graph)
- Verarbeitung (Nutzung): Womit wird gerechnet? (z.B. Spark, MapReduce)