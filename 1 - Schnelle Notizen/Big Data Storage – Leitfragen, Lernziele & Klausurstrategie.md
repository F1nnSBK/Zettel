#

# UE01: Kursüberblick und Big-Data-Storage-Perspektive

## Leitfrage
Warum ist Storage der Engpass und Strukturgeber für Big Data?

## Lernziele & Prüffragen

Prüffrage: Wie lässt sich Big Data aus der Storage-Perspektive definieren und was sind die wesentlichen Treiber für diese Betrachtung?
?
Lernziel: Big Data aus Storage-Sicht definieren und zentrale Treiber benennen.

Prüffrage: Welche Ebenen umfasst der Big-Data-Stack und inwiefern begrenzt die unterste Storage-Ebene die Möglichkeiten der darüberliegenden Ebenen?
?
Lernziel: Die Ebenen des Big-Data-Stacks einordnen.

Prüffrage: Worin unterscheiden sich OLTP und OLAP sowie Batch- und Streaming-Verarbeitung hinsichtlich ihrer Anforderungen an die Speicherlogik?
?
Lernziel: OLTP/OLAP sowie Batch/Streaming unterscheiden.

## Klausurstrategie
Klausurhinweise: In der Klausur werden typischerweise Begriffe und Zusammenhänge abgefragt. Antworten dürfen nicht nur Definitionen enthalten, sondern müssen die Logik der Entscheidung nachvollziehen. Wird nach einer Speicherwahl gefragt, muss die Antwort die Datenform und das Zugriffsmuster explizit benennen und daraus die Speicherlogik ableiten. Typische Operatoren sind „erklären“ (Begründungskette), „vergleichen“ (Trade-offs) und „einordnen“ (Position im Stack). Wer Belege und Beispiele anführt, erreicht sichere Punkte.

---

# UE02: Daten, Workloads und Zugriffsmuster

## Leitfrage
Wie führt der Weg von der Datenform über das Zugriffsmuster zur passenden Speicherlogik?

## Lernziele & Prüffragen

Prüffrage: Warum erfordern tabellarische, semi-strukturierte und unstrukturierte Datenformen grundlegend unterschiedliche physische Speicherarchitekturen?
?
Lernziel: Erklären, warum sich Datenformen in ihren Speicheranforderungen unterscheiden.

Prüffrage: Welche physischen Konsequenzen (z.B. Indexierung, Partitionierung) ergeben sich zwangsläufig aus Zugriffsmustern wie Point Lookup, Range Scan und Append?
?
Lernziel: Typische Zugriffsmuster begründen und mit physischen Konsequenzen verknüpfen.

Prüffrage: Wie leitet man systematisch aus den Daten und dem Zugriffsmuster eines E-Commerce-Systems die korrekte Speicherlogik ab, anstatt einfach eine Technologie zu benennen?
?
Lernziel: Für ein Szenario eine passende Speicherlogik herleiten.

## Klausurstrategie

Wie argumentiere ich in der Klausur?
?
Erklären: Eine Nennung reicht nicht aus; Ursache und Wirkung müssen entfaltet werden (Struktur: Begriff, typische Nutzung, physische Konsequenz).
Vergleichen: Mindestens zwei Alternativen müssen entlang eines gemeinsamen Kriteriums gegenübergestellt werden (z.B. Latenz vs. Durchsatz bei OLTP/OLAP).
Einordnen: Eine Herleitung ist gefragt. Die korrekte Antwortstruktur lautet: erst Datenform bestimmen -> dann dominantes Zugriffsmuster benennen -> physische Konsequenz nennen -> Speicherlogik ableiten. Nicht direkt mit einem Produktnamen einsteigen!

---

# UE03: Partitionierung und horizontale Skalierung

## Leitfrage
Wie verteilt man Daten so, dass Last und Wachstum beherrschbar bleiben?

## Lernziele & Prüffragen

Prüffrage: Was sind die drei primären Ziele der horizontalen Partitionierung von Datenbeständen?
?
Lernziel: Ziele der Partitionierung erklären.

Prüffrage: Inwiefern unterscheiden sich Hash-Sharding und Range-Sharding bezüglich ihrer Eignung für Point Lookups versus Range Scans?
?
Lernziel: Hash- und Range-Sharding vergleichen und passend einordnen.

Prüffrage: Wie entstehen Hotspots in einer Range-Partitionierung und mit welchen Gegenmaßnahmen (z.B. Rebalancing, Salting) lässt sich das Problem mindern?
?
Lernziel: Hotspots erkennen und einfache Gegenmaßnahmen begründen.

## Klausurstrategie

Wie argumentiere ich in der Klausur (Partitionierung)?
?
Beginne nicht pauschal mit "Hash ist besser". Die tragfähige Reihenfolge lautet: 1. Zugriffsmuster bestimmen, 2. Lastbild benennen, 3. Strategie begründen, 4. typisches Risiko (z.B. Hotspots) nennen.
Erklären: Nicht nur die Strategie definieren, sondern sagen, warum sie für ein Szenario passt (z.B. Range-Sharding für gute Bereichsabfragen).
Vergleichen: Strategien strikt entlang gemeinsamer Kriterien (wie Hotspot-Risiko oder Gleichverteilung) spiegeln.

---

# UE04: Replikation, Konsistenz und CAP

## Leitfrage
Wie balancieren verteilte Systeme Konsistenz und Verfügbarkeit?

## Lernziele & Prüffragen

Prüffrage: Warum bedeutet Replikation nicht einfach nur „Backup“, sondern verschiebt das System hin zu einem verteilten Abstimmungsproblem?
?
Lernziel: Ziele der Replikation erklären.

Prüffrage: Wie unterscheiden sich Strong und Eventual Consistency konkret in ihrem Sichtbarkeitsversprechen nach einem Schreibvorgang (Write)?
?
Lernziel: Strong und Eventual Consistency gegeneinander abgrenzen.

Prüffrage: Wie entscheidet sich ein Kassensystem vs. ein Social-Media-Feed bei einem Netzwerkausfall gemäß dem CAP-Theorem zwischen C (Consistency) und A (Availability)?
?
Lernziel: CAP auf einfache Szenarien anwenden.

## Klausurstrategie

Wie argumentiere ich in der Klausur (Replikation, Konsistenz, CAP)?
?
Erklären: Nicht nur definieren, was Eventual Consistency ist, sondern auch, warum Systeme sie wählen (z.B. geringere Latenz, höhere Verfügbarkeit im Störfall).
Einordnen: Transfer auf ein konkretes Szenario ist gefordert. Struktur: 1. Fachliche Kritikalität benennen -> 2. Akzeptables Sichtbarkeitsniveau ableiten -> 3. Priorisierung zwischen Konsistenz (C) und Verfügbarkeit (A) fällen. Wichtig: Trenne strikt zwischen ACID (lokale Transaktionsgarantien) und CAP (Verhalten eines verteilten Systems bei Kommunikationsstörung).

---

# UE05: Storage-Paradigmen im Überblick

## Leitfrage
Welche grundlegenden Speicherparadigmen gibt es und wofür eignen sie sich?

## Lernziele & Prüffragen

Prüffrage: Wie lässt sich der Unterschied zwischen File Storage, Object Storage und Block Storage anhand ihrer Adressierungslogik erklären?
?
Lernziel: Storage-Paradigmen benennen und unterscheiden.

Prüffrage: In welchen drei Hauptfragen (Adressierung, Struktur, typische Zugriffe) unterscheiden sich diese Storage-Paradigmen am stärksten?
?
Lernziel: File-, Object- und DB-nahe Systeme entlang gemeinsamer Kriterien vergleichen.

Prüffrage: Warum wäre es falsch, einen Object Store als universelles klassisches Dateisystem für komplexe Verzeichnisoperationen zu verwenden?
?
Lernziel: Typische Einsatzbereiche begründet zuordnen.

## Klausurstrategie

Wie argumentiere ich in der Klausur (Storage-Paradigmen)?
?
Erklären: Bei einem Object Store nicht bei "speichert Objekte" stehen bleiben, sondern die Adressierung über IDs, Metadatenorientierung und den Fit für große BLOBs mitdenken.
Einordnen: Niemals mit dem Produktnamen beginnen! Gute Antwortstruktur: 1. Szenario und Datenart beschreiben -> 2. Zugriff klären -> 3. Paradigma ableiten. Bsp.: "Da große Binärdaten mit einfacher ID dominieren, liegt Object Storage näher als ein klassisches Dateisystem."

---

# UE08: Motivation und Konzept von NoSQL

## Leitfrage
Warum entstanden NoSQL-Systeme und was versprechen sie?

## Lernziele & Prüffragen

Prüffrage: Welche konkreten Faktoren (globale Skalierung, Last, flexible Datenformen) haben klassische relationale Systeme unter Druck gesetzt und NoSQL begünstigt?
?
Lernziel: Zentrale Treiber für NoSQL erklären.

Prüffrage: Inwiefern stellt BASE keine "Regellosigkeit" dar, sondern eine bewusste Priorisierung gegenüber den strengen Garantien von ACID?
?
Lernziel: ACID und BASE als unterschiedliche Denkrahmen beschreiben.

Prüffrage: Welche vier Hauptfamilien von NoSQL-Systemen gibt es und welches Kernproblem der Skalierung löst jede Familie?
?
Lernziel: NoSQL-Familien im Überblick benennen.

## Klausurstrategie

Wie argumentiere ich in der Klausur (NoSQL Motivation)?
?
Antworten immer mit dem Problem beginnen, nicht mit dem Namen der Datenbank-Familie. Reihenfolge: 1. Welcher Druck besteht? (z.B. hohe Last, verteilte Joins) -> 2. Welche Reaktion ist typisch? (Denormalisierung, lockerere Sichtbarkeit) -> 3. Erst dann die Familie / den NoSQL Begriff einordnen.

---

# UE09: Key-Value Stores

## Leitfrage
Warum sind Key-Value Stores so skalierbar, und wo liegen ihre Grenzen?

## Lernziele & Prüffragen

Prüffrage: Warum ist die starke Einschränkung der API auf PUT, GET und DELETE bei Key-Value Stores fachlich ein immenser Skalierungsvorteil?
?
Lernziel: Die Key-Value API und ihre Grundidee erklären.

Prüffrage: Wie nutzt das Konzept des Consistent Hashing (Ringmodell) den Schlüssel für eine saubere Lastenverteilung und Rebalancing?
?
Lernziel: Partitionierung über Consistent Hashing beschreiben.

Prüffrage: Warum eignet sich ein Key-Value Store optimal für Session-Daten, versagt aber bei der Aufgabe, komplexe Filterungen über mehrere Attribute durchzuführen?
?
Lernziel: Typische Grenzen und Einsatzszenarien begründen.

## Klausurstrategie

Wie argumentiere ich in der Klausur (Key-Value Stores)?
?
Argumentation startet beim Zugriffsmuster: Wenn der Schlüssel bekannt ist und direkte Einzelzugriffe dominieren -> Key-Value Store. Dann Verteilungslogik ansprechen (Hashing, Ring), um Skalierung zu begründen. Zuletzt Grenzen benennen (z.B. fehlende Range Queries). Merksatz für "Einordnen": Key-Value Stores sind stark, wenn der Schlüssel bekannt ist; sie sind schwach, wenn die Frage (das Attribut) erst noch gefunden werden muss.

---

# UE10: Document Stores

## Leitfrage
Wann sind Dokumente das passende Datenmodell?

## Lernziele & Prüffragen

Prüffrage: Wie unterscheidet sich eine "fachliche Zugriffseinheit" im Document Store von einer normalisierten Struktur in einer relationalen Datenbank?
?
Lernziel: Das Dokumentprinzip erklären.

Prüffrage: Unter welchen konkreten Bedingungen (Änderungsrate, gemeinsames Lesen) sollten Daten in einem Dokument eingebettet und nicht nur referenziert werden?
?
Lernziel: Einbettung und Referenzen gegeneinander abwägen.

Prüffrage: Warum lösen Document Stores trotz ihrer Schema-Flexibilität nicht automatisch die Leistungsfrage und benötigen Indizes für Query-Pfade?
?
Lernziel: Indizes und Aggregationen als Leistungslogik einordnen.

## Klausurstrategie

Wie argumentiere ich in der Klausur (Document Stores)?
?
Beginne nie sofort mit "Einbettung" oder "Referenz". Struktur: 1. Fachliche Einheit beschreiben -> 2. Dominanten Zugriff klären (was wird gemeinsam gelesen / getrennt gepflegt?) -> 3. Modellierungsentscheidung treffen. Antworten sind besonders stark, wenn sie die Gegenposition mitdenken (warum wird ein Teil nicht eingebettet, um z.B. Redundanzen zu vermeiden). Merksatz für "Einordnen": Ein Document Store passt dort, wo fachliche Einheit und Zugriffseinheit eng zusammenfallen.

---

# UE11: Wide Column Stores

## Leitfrage
Wie funktionieren Column Families und wofür sind sie optimiert?

## Lernziele & Prüffragen

Prüffrage: Welche Rolle spielt der Row Key für den Zugriff und was ordnet eine Column Family in einem Wide Column Store?
?
Lernziel: Row Key, Column Family und Cell beschreiben.

Prüffrage: Warum sind Wide Rows und Sparse Columns optimal für Sensor- und Zeitreihendaten, die stark lückenhaft sein können?
?
Lernziel: Wide Rows und Sparse Columns als Zugriffsidee erklären.

Prüffrage: Inwiefern unterscheiden sich HBase (Master-fokussiert) und Cassandra (Peer-to-Peer) in ihrer Architekturidee, während sie dieselbe Column-Logik teilen?
?
Lernziel: HBase und Cassandra grob vergleichen.

## Klausurstrategie

Wie argumentiere ich in der Klausur (Wide Column Stores)?
?
Startpunkt ist nicht das Produkt, sondern das Zugriffsmuster. Reihenfolge: 1. Welches Zugriffsmuster dominiert? -> 2. Wie muss folglich der Row Key modelliert werden? -> 3. Erklären, welche Column Families gebildet werden. Merksatz für "Einordnen": Wide Column Stores passen dort, wo geordnete Schlüsselbereiche und vorbereitete Zugriffspfade (z.B. Zeitreihen) wertvoll sind.

---

# UE12: Konsistenzmodelle in NoSQL-Systemen

## Leitfrage
Wie lassen sich Konsistenz und Verfügbarkeit konkret austarieren?

## Lernziele & Prüffragen

Prüffrage: Wie grenzen sich Strong Consistency und Eventual Consistency von clientseitigen Garantien wie Read-Your-Writes ab?
?
Lernziel: Zentrale Konsistenzmodelle unterscheiden.

Prüffrage: Warum stellt die Formel R+W>N sicher, dass ein Lesezugriff (Read) immer mindestens auf ein aktuelles Replikat stößt?
?
Lernziel: Quorum-Regeln auf einfache Beispiele anwenden.

Prüffrage: Was bedeuten Mechanismen wie "Read Repair" oder "Last-Write-Wins" für die Konsistenz und den potenziellen Informationsverlust?
?
Lernziel: Konfliktlösung und Reparaturmechanismen erklären.

## Klausurstrategie

Wie argumentiere ich in der Klausur (Konsistenzmodelle)?
?
Beginne immer mit dem Fachszenario und dem Schaden eines veralteten oder widersprüchlichen Reads (z.B. Like auf Social Media vs. Platzreservierung im Flugzeug). Erst danach wird das passende Konsistenzmodell zugeordnet. Bei Quorum-Aufgaben N, R und W benennen, die Formel kurz interpretieren und Konfliktmechanismen ergänzen.

---

# UE13: NoSQL-Vergleich und Use Cases

## Leitfrage
Welcher NoSQL-Typ passt zu welchem Problem?

## Lernziele & Prüffragen

Prüffrage: Wie lassen sich Key-Value, Document, Wide Column und Graph anhand ihrer idealen Zugriffsmuster gegenüberstellen?
?
Lernziel: NoSQL-Typen vergleichend darstellen.

Prüffrage: Aus welchen vier Schritten besteht ein kompakter Entscheidungsgang, um für einen konkreten Anwendungsfall (z.B. E-Learning Plattform) den besten NoSQL-Typ abzuleiten?
?
Lernziel: Eine Use-Case-Entscheidung begründen.

Prüffrage: An welchen typischen Fachfragen stoßen die jeweiligen Modelle auf ihre architektonischen Grenzen?
?
Lernziel: Trade-offs knapp zusammenfassen.

## Klausurstrategie

Wie sieht ein kompakter Entscheidungsgang für Fallfragen aus?
?
1. Dominierende Fachfrage (Workload) benennen.
2. Einheit bestimmen, die gemeinsam gelesen/geschrieben/traversiert wird.
3. Den passenden Typ (Modellskizze) wählen, der diese Einheit natürlich trägt.
4. Grenze/Trade-off benennen (Was würde eine Fehlwahl kosten?).

---

# UE14: Motivation und Anforderungen an Distributed File Systems

## Leitfrage
Warum brauchen wir verteilte Dateisysteme?

## Lernziele & Prüffragen

Prüffrage: Welche vier Kernanforderungen (Skalierung, Durchsatz, Fehlertoleranz, Metadatenorganisation) motivieren den Einsatz eines DFS gegenüber einem lokalen Laufwerk?
?
Lernziel: Anforderungen an ein Distributed File System nennen.

Prüffrage: Wie unterscheidet HDFS architektonisch zwischen Daten und Metadaten über NameNode und DataNodes?
?
Lernziel: HDFS-Grundmodell mit Blocks, NameNode und DataNode erklären.

Prüffrage: Warum ist die Datenlokalität bei verteilten Analysen entscheidend für die Leistungsfähigkeit großer Dateisysteme?
?
Lernziel: Datenlokalität als Leistungsprinzip einordnen.

## Klausurstrategie

Wie argumentiere ich in der Klausur (Distributed File Systems)?
?
Beginne mit der Problemseite: Geringer Speicher, begrenzte Leserate pro Rechner, Ausfälle. Dann die Architekturantwort: Blöcke, NameNode, DataNodes, Replikation. Erst danach Details wie "Datenlokalität" benennen. Merksatz für "Einordnen": Ein DFS wird stark, wenn große Datenmengen robust und mit hohem Durchsatz über viele Knoten organisiert werden müssen. Es ist kein simples, riesiges NAS!

---

# UE15: HDFS Architektur im Detail

## Leitfrage
Wie arbeitet HDFS beim Lesen und Schreiben?

## Lernziele & Prüffragen

Prüffrage: Welche exakten Funktionen übernehmen Client, NameNode und DataNode im koordinierten Zusammenspiel des Clusters?
?
Lernziel: Rollen von Client, NameNode und DataNode erklären.

Prüffrage: In welchen konkreten Teilschritten laufen der Write Path und der Read Path in HDFS ab?
?
Lernziel: Read Path und Write Path in sinnvoller Reihenfolge darstellen.

Prüffrage: Inwiefern tragen Replikation und Rack Awareness bereits architektonisch zur Ausfallsicherheit des Clusters bei?
?
Lernziel: Replikation und Rack Awareness als Fehlertoleranzlogik einordnen.

## Klausurstrategie

Wie argumentiere ich in der Klausur (HDFS Architektur)?
?
Bei Ablauf- oder Architekturfragen immer mit der Rollenlogik starten (Wer steuert, wer speichert, wer initiiert?). Strikt trennen in:
- Metadatenpfad (Client spricht mit NameNode)
- Datenpfad (Client transferiert an DataNodes in der Replikationskette)
Nicht einfach die Verben "schreibt" oder "liest" wiederholen, sondern aufzeigen, dass HDFS Orientierungswissen und Datenbewegung bewusst trennt.

---

# UE16: HDFS Eigenschaften, Fehlertoleranz und Grenzen

## Leitfrage
Wo ist HDFS stark und wo liegen die Grenzen?

## Lernziele & Prüffragen

Prüffrage: Welche Rolle spielen Heartbeats, Block Reports und Replikation für die operative Ausfallsicherheit des HDFS?
?
Lernziel: HDFS-Fehlertoleranzmechanismen erklären.

Prüffrage: Wieso ist die Fokussierung auf großen Durchsatz (statt Einzellatenz) der Schlüssel zum HDFS-Architekturdesign?
?
Lernziel: Datenlokalität und Durchsatzlogik einordnen.

Prüffrage: Aus welchen architektonischen Gründen wird HDFS bei Szenarien wie "Small Files" und "Random Writes" extrem ineffizient?
?
Lernziel: Typische Grenzen wie Small Files und Random Writes benennen.

## Klausurstrategie

Wie argumentiere ich in der Klausur (HDFS Grenzen)?
?
Start nicht mit Pro/Contra-Liste, sondern mit: 1. Problemklasse / Dateiform beschreiben (Scan oder Einzelzugriff? Durchsatz oder Latenz?) -> 2. Architekturpassung klären -> 3. Grenzen aufzeigen (z.B. Metadaten-Overhead bei Small Files). Merksatz für "Vergleichen": HDFS gegen die Problemwelt abgrenzen, nicht nur gegen ein anderes Produkt.

---

# UE17: Object Stores

## Leitfrage
Was macht Object Stores so skalierbar und preiswert?

## Lernziele & Prüffragen

Prüffrage: Inwiefern unterscheidet sich der flache Namespace eines Buckets grundlegend von der Hierarchie eines klassischen Dateisystems?
?
Lernziel: Bucket, Objekt und Metadaten erklären.

Prüffrage: Warum erzeugt die bewusste Reduktion auf diese schmale API einen massiven Plattform- und Skalierungsvorteil?
?
Lernziel: Grundlogik von PUT, GET, LIST und DELETE beschreiben.

Prüffrage: Wo liegt der präzise Unterschied zwischen der Datensicherheit (Durability) und der Erreichbarkeit (Verfügbarkeit) in einem Cloud-Speicher?
?
Lernziel: Durability und Verfügbarkeit sauber unterscheiden.

## Klausurstrategie

Wie argumentiere ich in der Klausur (Object Stores)?
?
Antworten beginnen mit dem Objektmodell, nicht mit Produktnamen (z.B. S3). Dann die API-Logik beschreiben (welche Operationen trägt das Modell?). Erst danach Skalierung oder Use Cases einordnen. Merksatz für "Einordnen": Object Stores sind einfache, stark skalierbare Plattformspeicher mit klarer API-Logik, entkoppelt von der Dateiillusion.

---

# UE18: DFS vs Object Store und moderne Architekturen

## Leitfrage
Wie entscheide ich zwischen DFS und Object Store in modernen Datenplattformen?

## Lernziele & Prüffragen

Prüffrage: Anhand welcher fünf Leitfragen (Modell, Zugriff, Leistungsziel, Plattformlogik, Kosten/Governance) vergleicht man DFS und Object Store am effektivsten?
?
Lernziel: DFS und Object Stores anhand klarer Kriterien vergleichen.

Prüffrage: Warum ist ein Data Lake primär ein "Speicherprinzip zur Entkopplung" und wie versucht das Lakehouse diese Konzepte weiter zu organisieren?
?
Lernziel: Data Lake und Lakehouse einordnen.

Prüffrage: Nach welchem 4-Schritte-Verfahren leitet man die Wahl zwischen DFS und Object Store für eine spezifische Plattform-Workload ab?
?
Lernziel: Eine Speicherentscheidung für einen Fall begründen.

## Klausurstrategie

Wie argumentiere ich in der Klausur (DFS vs Object Store)?
?
Vergleichen: Niemals isolierte Eigenschaften aufzählen. Arbeite an gemeinsamen Vergleichsachsen (Kriterien).
Einordnen/Begründen: Ein guter Klausursatz lautet z.B.: "Für diesen Use Case passt ein Object Store besser, weil die Speicherbasis von der späteren Verarbeitung entkoppelt werden soll und mehrere Engines über eine offene Plattform auf dieselben Rohdaten zugreifen."

---

# UE19: Hadoop-Oekosystem im Ueberblick

## Leitfrage
Wie greifen Storage und Processing im Hadoop-Oekosystem ineinander?

## Lernziele & Prüffragen

Prüffrage: Welche exakten Aufgabenbereiche (Speicher, Ressourcen, Batch-Logik, Metadaten) decken diese vier Hadoop-Kernkomponenten ab?
?
Lernziel: HDFS, YARN, MapReduce und Metastore benennen.

Prüffrage: In welcher Abfolge (Speichern -> Job anstoßen -> YARN plant -> Engine verarbeitet) durchläuft ein Datenfluss das Ökosystem?
?
Lernziel: Den Weg von Daten und Jobs durch das Ökosystem erklären.

Prüffrage: Warum benötigt man einen Metastore, um einen logischen Tabellenblick auf ansonsten strukturlose Dateien im HDFS zu erhalten?
?
Lernziel: Die Rolle von Metadaten und Tabellenabstraktion einordnen.

## Klausurstrategie

Wie argumentiere ich in der Klausur (Hadoop-Ökosystem)?
?
Bei Fragen immer mit der konkreten Ebene beginnen: Geht es um Speicher, Ressourcen, Verarbeitung oder Metadaten?. Dann Komponente zuordnen und das Zusammenspiel formulieren. Einordnen: Hadoop ist kein "einzelnes Tool", sondern ein Schichtenmodell. Keine Buzzwords werfen, ohne die Rolle im System zu verdeutlichen.

---

# UE21: MapReduce als Batch-Paradigma

## Leitfrage
Wie funktioniert MapReduce als geordnete Batch-Verarbeitung und warum war dieses Modell so prägend?

## Lernziele & Prüffragen

Prüffrage: Welche zwingende Reihenfolge aus lokaler Vorverarbeitung (Map), Neuordnung übers Netz (Shuffle) und Verdichtung (Reduce) charakterisiert das Paradigma?
?
Lernziel: Den Ablauf aus Map, Shuffle und Reduce erklären.

Prüffrage: Inwiefern hilft die datennahe Verarbeitung in der Map-Phase dabei, Netzengpässe beim Umgang mit Big Data zu verhindern?
?
Lernziel: Datennahe Verarbeitung als Leistungsargument einordnen.

Prüffrage: Warum scheitert MapReduce an Systemen mit extrem niedriger Latenzanforderung, während es für gigantische Tages-Batch-Läufe brilliert?
?
Lernziel: Geeignete und ungeeignete Batch-Probleme unterscheiden.

## Klausurstrategie

Wie argumentiere ich in der Klausur (MapReduce)?
?
Antwort über den Ablauf aufbauen (Map, Shuffle, Reduce erklären). Dann begründen, warum der vorliegende Fall exakt als Batch-Problem gelesen werden muss (z.B. klar abgegrenzte Menge, keine Echtzeit nötig). Im dritten Schritt die Stärken und Grenzen einordnen.

---

# UE24: Vergleich und Entscheidung

## Leitfrage
Wie lassen sich HDFS, Object Store, MapReduce, Spark und HBase für unterschiedliche Aufgaben begründet einordnen?

## Lernziele & Prüffragen

Prüffrage: Wie nutzt man die Metriken Zugriffsmuster, Latenz, Datenform und Flexibilität, um eine fundierte Architekturentscheidung zu treffen?
?
Lernziel: Systeme entlang von Zugriffsmuster, Latenz, Datenform und Flexibilität vergleichen.

Prüffrage: Warum muss eine Architekturentscheidung primär über die dominante Aufgabe (Batch vs. Analyse vs. Einzelzugriff) argumentiert werden?
?
Lernziel: Eine Systemwahl mit Bezug auf die Aufgabe begründen.

Prüffrage: Warum sind Entscheidungen, die HBase zur freien Batch-Großanalyse oder HDFS für millisekundenschnelle Updates einplanen, fundamentale Fehlkonfigurationen?
?
Lernziel: Typische Fehlzuordnungen erkennen.

## Klausurstrategie

Wie argumentiere ich in der Klausur (Vergleich und Entscheidung)?
?
Nicht mit dem Produktnamen beginnen! Reihenfolge: 1. Aufgabe charakterisieren (Batch oder flexibel? Analyse oder schneller Einzelzugriff? Speicherbasis oder Zugriffsstruktur?) -> 2. Passendes System nennen -> 3. Die Kriterien in die Entscheidung einbetten. Eine Entscheidung ist falsch, wenn das System die dominante Aufgabe nicht trägt.

---

# UE26: Klausurtraining

## Leitfrage
Wie lassen sich klausurtypische Aufgaben so strukturieren, dass aus Wissen eine saubere Antwort wird?

## Lernziele & Prüffragen

Prüffrage: Was verlangt der Operator "Vergleichen" zwingend, was ein einfaches Aufzählen von Merkmalen nicht erfüllt?
?
Lernziel: Aufgaben nach den Operatoren Einordnen, Vergleichen und Begründen lesen.

Prüffrage: Wie baut sich das 4-Schritte-Gerüst auf, um das Rohwissen in eine voll bepunktete Klausurantwort zu überführen?
?
Lernziel: Antworten in nachvollziehbare Schritte gliedern.

Prüffrage: Wie formuliert man einen schwachen Satz wie "Spark ist besser" in ein tragfähiges Architekturargument um?
?
Lernziel: Schwache von tragfähigen Antworten unterscheiden.

## Klausurstrategie ("Vom Rohwissen zur ausformulierten Antwort")

Das Gerüst für jede Klausurantwort:
?
1. Aufgabe verstehen: Startet beim Problem, nicht bei Schlagwörtern.
2. Kriterium nennen: Fachlichen Maßstab aufbauen (z.B. Flexibilität, Zugriffseinheit).
3. Einordnung: System in das Kursmodell setzen.
4. Begründung formulieren: Entscheidung explizit mit Aufgabe + Kriterium verknüpfen.

---

# Übungsklausur: Big Data Storage

Frage 1: Zugriffsmuster zuordnen (4 Punkte)
Szenario: Ordnen Sie die folgenden vier Szenarien jeweils einem Zugriffsmuster zu (Point Lookup, Range Scan, Append, Object Read) und begründen Sie jede Zuordnung in einem Satz. a) Live-Preisabfrage in einem Onlineshop b) Tagesreport über alle Verkäufe eines Monats c) Eingehende Sensorwerte einer Produktionsanlage d) Abruf eines archivierten Vertragsscans
?
Musterlösung:
a) Live-Preisabfrage: Point Lookup. Begründung: Es handelt sich um einen Key-basierten Einzelzugriff mit der Erwartung an eine sofortige Antwort.
b) Tagesreport: Range Scan / Batch Read. Begründung: Ein großer Zeitraum wird hierbei sequentiell gelesen und aggregiert.
c) Sensorwerte: Append (mit späteren Range Scans). Begründung: Es ist ein kontinuierlicher Eventstrom, der fortlaufend angehängt und erst später zeitlich ausgewertet wird.
d) Vertragsscan: Object Read. Begründung: Es ist ein großes, unveränderliches Objekt, das selten und immer als Ganzes gelesen wird.

Frage 2: NoSQL-Typ begründet wählen (5 Punkte)
Szenario: Ein Streaming-Dienst speichert pro Nutzer ein umfangreiches Profil mit variablen Präferenzen, Watchlists und Einstellungen. Eine Profilseite wird als Ganzes geladen. a) Wählen Sie einen passenden NoSQL-Typ aus: Key-Value, Document, Wide Column. b) Begründen Sie Ihre Wahl entlang Stärke, Grenze und Preis der Fehlwahl. c) Nennen Sie einen alternativen Typ und erläutern Sie, warum er hier ungünstiger wäre.
?
Musterlösung:
a) Gewählter Typ: Document.
b) Begründung:
- Stärke: Das Profil wird als fachliche Einheit (zusammenhängend) gelesen und geschrieben — genau das ist die Stärke von Document-Stores.
- Grenze: Querbeziehungen zwischen Profilen (z.B. „Freunde mit ähnlichen Vorlieben“) werden im Document-Modell sehr aufwendig.
- Preis der Fehlwahl: Würde man z.B. Key-Value wählen, ginge die Feldzugriffsstruktur verloren und Teilabfragen im Profil würden unnötig schwer.
c) Alternative: Key-Value. Warum ungünstig? Er bietet zwar schnellen Zugriff über die Nutzer-ID, aber die innere Struktur des Profils bliebe völlig außerhalb des Modells — selektive Updates einzelner Felder ohne Anwendungssemantik wären somit nicht möglich.

Frage 3: Storage-Paradigma einordnen (3 Punkte)
Szenario: Ein Unternehmen möchte Backups von Server-Snapshots ablegen: sehr große, unveränderliche Dateien, seltener Zugriff, hohe Anforderung an Durability. a) Wählen Sie ein passendes Storage-Paradigma (Block, File, Object, Key-Value, DB). b) Begründen Sie mit zwei Eigenschaften (z. B. Adressierung, Struktur, Zugriffsmuster, Durability). c) Schließen Sie ein Paradigma explizit aus und begründen Sie kurz.
?
Musterlösung:
a) Paradigma: Object Storage.
b) Eigenschaften:
- Adressierung: Object Storage nutzt einen flachen Namespace mit ID-basiertem Zugriff über API/HTTP — ideal für sehr viele und große Objekte.
- Zugriffsmuster + Durability: Unveränderliche, selten gelesene Objekte, die eine hohe Durability benötigen, sind exakt das Einsatzfeld von Object Stores.
c) Ausschluss: Block Storage. Begründung: Block Storage ist auf Random-Writes und niedrige Latenz für aktive Volumes ausgelegt; für selten gelesene, riesige und unveränderliche Großdateien wäre dies völlig überdimensioniert und zu teuer.

Frage 4: HDFS vs. Object Store (4 Punkte)
Szenario: HDFS und Object Store sind beide Speicherlogiken. a) Vergleichen Sie beide Systeme in einer Tabelle entlang der Kriterien Zugriffsmuster und Flexibilität. b) Beurteilen Sie die Aussage: „HDFS ist veraltet, seit es Object Stores gibt.“ in 1–2 Sätzen.
?
Musterlösung:
a) Vergleich:
- Zugriffsmuster: HDFS zielt auf sequentielle Batch-Verarbeitung großer Blöcke ab und ist eng mit Compute gekoppelt. Object Store bietet direkten Objektzugriff über API/HTTP für viele unabhängige Reads/Writes.
- Flexibilität: HDFS ist extrem eng an das Hadoop-Ökosystem gebunden (Speicher und Compute zusammen). Object Store ist von Compute entkoppelt, wodurch mehrere verschiedene Engines denselben Datenraum nutzen können.
b) Beurteilung der Aussage: Die Aussage ist falsch. Beide gehören zwar in den Speicherraum, verfolgen aber grundlegend unterschiedliche Kopplungs- und Nutzungsideen. HDFS ist auf enge Compute-Kopplung und Batch-Analysen ausgelegt, während der Object Store auf entkoppelte, weltweite Plattformzugriffe abzielt.

Frage 5: Mischarchitektur in einer Lernplattform (4 Punkte)
Szenario: Eine Lernplattform hat zwei Bedarfe an denselben Daten:
- Bedarf 1 (Kursbeschreibungen): Kurse mit Modulen, Terminen und Materialien werden als Ganzes geladen, bearbeitet und versioniert.
- Bedarf 2 (Aktivitätsereignisse): Seitenaufrufe und Bearbeitungszeiten entstehen in großer Zahl und werden nach Nutzer, Kurs oder Zeitfenster sequentiell ausgewertet.
a) Schlagen Sie für jeden Bedarf einen passenden NoSQL-Typ vor (Key-Value, Document, Wide Column) und begründen Sie kurz. b) Erklären Sie in einem Satz, warum ein einzelner Typ beide Bedarfe nicht gleich gut abdeckt.
?
Musterlösung:
a) Typen:
- Bedarf 1 (Kursbeschreibungen): Document. Ein Kurs wird als zusammenhängende fachliche Einheit gelesen, bearbeitet und versioniert — das ist die natürliche Stärke des Document-Modells.
- Bedarf 2 (Aktivitätsereignisse): Wide Column. Großmengige, geordnete Ereignisse mit einem Row-Key nach Nutzer/Kurs/Zeit können hier über Bereichszugriffe enorm effizient ausgewertet werden.
b) Begründung zur Mischarchitektur: Die beiden Bedarfe haben fundamentale, unterschiedliche Zugriffswelten — fachliche Einheit lesen vs. geordnete Bereiche scannen. Ein einzelner Typ würde bei dem Versuch, beide Anforderungen zu erfüllen, in einem der beiden Aspekte zwangsläufig Leistung einbüßen.

Frage 6: HDFS-Architektur: Write Path und Rollen (5 Punkte)
Szenario: Ein Team beginnt mit HDFS und äußert: „Der NameNode ist dann unser Speichercluster.“ a) Beschreiben Sie die drei Hauptrollen in HDFS (Client, NameNode, DataNode) in je einem Satz. b) Skizzieren oder beschreiben Sie den Write Path in einer sinnvollen Schrittfolge (mindestens 4 Schritte) und kennzeichnen Sie, was Metadatenpfad und was Datenpfad ist. c) Beurteilen Sie die eingangs zitierte Aussage in 1–2 Sätzen.
?
Musterlösung:
a) Hauptrollen:
- Client: Startet Lese- oder Schreiboperationen; er ist kein interner Clusterknoten, sondern die anfragende Seite.
- NameNode: Verwaltet die Metadaten (Datei-, Block- und Platzierungsinformationen) und trifft Platzierungsentscheidungen, speichert selbst aber keine Blockdaten.
- DataNode: Speichert die eigentlichen Blöcke auf der Festplatte und transportiert die Datenströme zwischen Client und Replikationskette.
b) Write Path:
1. Client meldet beim NameNode eine neue Datei bzw. einen neuen Block an (Metadatenpfad).
2. NameNode trifft Platzierungsentscheidung (Replikationsfaktor, Rack Awareness) und nennt dem Client die Zielkette an DataNodes (Metadatenpfad).
3. Datenstrom startet direkt vom Client zum ersten DataNode der Kette (Datenpfad).
4. Der Block wird entlang der Replikationskette an weitere DataNodes weitergereicht (Datenpfad).
5. DataNodes bestätigen den Block; erst nach vollständiger Bestätigung der gesamten Kette gilt der Schreibvorgang als abgeschlossen (Datenpfad).
c) Beurteilung der Aussage: Die Aussage ist unpräzise. Der NameNode ordnet lediglich die Datenwelt (Metadaten und Platzierungswissen), gespeichert werden die tatsächlichen Blöcke jedoch auf den DataNodes. Metadatenebene und Datenebene müssen architektonisch immer getrennt gedacht werden.
