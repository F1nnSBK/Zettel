#Note

2026-06-12

Tags: [[Datenbanken]], [[NoSQL]], [[Big Data]], [[Architektur]], [[BASE]]
#datenbanken 

---
**NoSQL-Datenbanken** entstanden als direkte Antwort auf die Limitierungen von relationalen Datenbanken (RDBMS) im Angesicht des Web 2.0 (ab den 2000er Jahren) und Big Data. Klassische Datenbanken ließen sich nur sehr teuer "vertikal" (durch stärkere Hardware) skalieren und scheiterten an unstrukturierten Daten (Variety).

Der Paradigmenwechsel

NoSQL-Systeme zeichnen sich durch folgende Eigenschaften aus:

1. **Nicht-relationales Datenmodell:** Daten werden nicht in starren Tabellen mit Zeilen und Spalten gespeichert.
2. **Schema-Flexibilität (Schema-on-Read):** Es gibt kein fixes Datenbankschema. Strukturen müssen nicht vorab per DDL definiert werden, was agile Entwicklung und schnelle Iterationen erlaubt.
3. **Massive Skalierbarkeit & Web-Scale:** Unterstützen lineare, horizontale Skalierung (Verteilung auf viele günstige Standard-Server). Sie bedienen Millionen Nutzer gleichzeitig ohne Performance-Verlust.
4. **Hochverfügbarkeit durch Replikation:** Das System darf niemals stillstehen. Daten werden über mehrere Knoten repliziert.
5. **BASE statt ACID:** Um Ausfalltoleranz (CAP-Theorem) zu garantieren, setzen die Systeme meist auf das BASE-Modell (Basically Available, Soft-state, Eventual consistency).

Die 4 Hauptkategorien von NoSQL-Systemen

Da es nicht mehr "die eine" Tabellenstruktur gibt, spaltet sich NoSQL in vier hochspezialisierte Gattungen auf:

- **[[Key-Value Store]]s (z. B. Redis, DynamoDB):** Das einfachste Modell. Ein Wert wird über einen eindeutigen Schlüssel adressiert. Extrem schnell, perfekt für Session-Management und Caching.
- **Dokumentenorientierte Datenbanken (z. B. MongoDB):** Speichern strukturierte JSON/BSON-Dokumente. Hohe Flexibilität durch baumartig verschachtelte Daten. Ideal für CMS und Produktkataloge.
- **[[Wide-Column Store]] (z. B. Cassandra):** Arbeiten mit Spaltenfamilien statt Tabellenzeilen. Optimiert für extrem hohen Schreibdurchsatz, Logging und IoT-Daten.
- **[[Graphdatenbanken]] (z. B. Neo4j):** Fokussieren sich voll auf Beziehungen (Knoten und Kanten). Perfekt für soziale Netzwerke, Wissensgraphen und Empfehlungsalgorithmen.

**Nomenklatur:** Der Begriff "NoSQL" (entstanden 1998) ist heute irreführend, da viele dieser Systeme (wie Cassandra mit CQL) längst SQL-ähnliche Abfragesprachen nutzen. Daher ist der Begriff **"nicht-relationale Datenbanken"** fachlich wesentlich präziser.

---

### Flashcards

Begriffsdefinition (Prüfungsfrage 1): Warum ist die Bezeichnung „nicht-relational“ fachlich oft treffender als der etablierte Begriff „NoSQL“?
?
Weil viele moderne NoSQL-Systeme mittlerweile SQL-ähnliche Schnittstellen (z.B. CQL bei Cassandra) besitzen, ist das Fehlen von SQL nicht mehr das Hauptmerkmal. Das radikal abweichende (nicht-relationale) Datenmodell hingegen schon.

Schema-Flexibilität: Was bedeutet „Schemafreiheit“ in der Praxis für die Applikationsentwicklung?
?
Es bedeutet, dass die Datenstruktur nicht strikt vor der Dateneingabe (via DDL) definiert werden muss. Jedes Dokument oder jeder Datensatz innerhalb einer Sammlung kann völlig individuelle Attribute besitzen. Dies ermöglicht eine sehr agile und iterative Softwareentwicklung.

BASE vs. ACID: NoSQL-Systeme streben oft eine hohe Verfügbarkeit an. Auf welches Modell (Akronym) wird dabei im Gegensatz zu ACID häufig verwiesen?::Auf das **BASE**-Modell (Basically Available, Soft state, Eventual consistency).

Welches Skalierungs-Paradigma wird von NoSQL-Datenbanken standardmäßig genutzt, um dem "Volume" von Big Data gerecht zu werden?::Die **horizontale Skalierung** (Verteilung der Daten über viele Standard-Server / Sharding), anstelle der vertikalen Skalierung (Aufrüsten eines einzelnen Servers) von relationalen Datenbanken.

Nennen Sie die vier Hauptkategorien von NoSQL-Datenbanksystemen.::1. Key-Value Stores, 2. Dokumentenorientierte Datenbanken, 3. Wide-Column Stores, 4. Graphdatenbanken.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[NoSQL]]
SORT file.mtime DESC
```