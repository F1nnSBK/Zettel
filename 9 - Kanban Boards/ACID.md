#Note

2026-06-09

Tags: [[Datenbanksystem]], [[Relationale Datenbank]], [[Datenintegrität]], [[Big Data]]
#datenbanken 

---
Das **ACID-Prinzip** definiert die vier theoretischen Anforderungen, die ein relationales Datenbankmanagementsystem (RDBMS) an die Ausführung von Transaktionen stellt. Es ist das absolute Sicherheitsnetz für die Datenintegrität.

Die 4 Säulen von ACID

1. **Atomicity (Atomarität - "Ganz oder gar nicht")** Eine Transaktion ist unteilbar. Entweder werden _alle_ Operationen innerhalb der Transaktionsklammer erfolgreich auf der Datenbank umgesetzt (durch `COMMIT`), oder _keine einzige_ (durch `ROLLBACK` im Fehlerfall). Es darf niemals eine "halb fertige" Transaktion nach außen sichtbar werden.
2. **Consistency (Konsistenz - "Regeltreue")** Die Datenbank befindet sich vor dem Start einer Transaktion in einem validen Zustand und muss nach Abschluss der Transaktion wieder in einem gültigen, widerspruchsfreien Zustand sein. Das bedeutet, dass jede Änderung die definierten Integritätsregeln (z.B. Datentypen, Wertebereiche, referentielle Integrität durch gültige Fremdschlüssel) strikt erfüllen muss.
3. **Isolation (Isolation - "Abgeschirmt")** Da Nutzer und Systeme oft gleichzeitig (`concurrent`) auf Daten zugreifen, garantiert die Isolation, dass sich parallel laufende Transaktionen nicht gegenseitig beeinflussen. Zwischenergebnisse einer Transaktion sind für andere Nutzer absolut unsichtbar, bis ein `COMMIT` erfolgt. Wie stark diese Unsichtbarkeit in der Praxis ist, regeln die _Isolation Levels_.
4. **Durability (Dauerhaftigkeit - "Für die Ewigkeit")** Sobald eine Transaktion per `COMMIT` bestätigt wurde, sind die Änderungen permanent und sicher gespeichert. Ein anschließender Systemabsturz oder Stromausfall darf das Vorhandensein der Daten nicht mehr gefährden. Dies wird technisch meist durch das sofortige Schreiben in sogenannte Log-Dateien (Redo Logs) sichergestellt, noch bevor die Daten final in die Tabellen geschrieben werden.

Der architektonische Konflikt (ACID vs. BASE)

In zentralisierten relationalen Datenbanken (wie PostgreSQL oder Oracle) ist ACID der Standard. Sobald Datenbanken jedoch massiv über Server-Knoten auf der ganzen Welt verteilt werden (Distributed Systems), ist die strikte ACID-Konsistenz nur mit extrem hohem Koordinationsaufwand und Performance-Verlusten ("teure Locks") aufrechtzuerhalten.

Daher nutzen viele NoSQL-Datenbanken stattdessen das **BASE-Modell** (Basically Available, Soft state, Eventually consistent). Anstatt sofortige Konsistenz zu erzwingen, priorisiert BASE die ständige Verfügbarkeit des Systems und akzeptiert, dass Datenkopien auf verschiedenen Servern zeitweilig veraltet sein können, bis sie sich irgendwann angleichen ("Eventual Consistency").

--------------------------------------------------------------------------------

### Flashcards

Was ist eine Transaktion im Kontext eines Datenbanksystems, und welche vier fundamentalen ACID-Eigenschaften muss jedes Transaktionssystem garantieren?
?
Eine Transaktion ist eine logische Einheit von Datenbankanweisungen, die die Datenbank von einem konsistenten Zustand in einen neuen konsistenten Zustand überführt. Die ACID-Eigenschaften sind: **Atomicity:** Transaktion wird vollständig ausgeführt oder gar nicht. **Consistency:** Einhaltung aller definierten Regeln und Integritätsbedingungen vor und nach der Transaktion. **Isolation:** Gleichzeitige Transaktionen beeinflussen sich nicht; Zwischenergebnisse sind unsichtbar. **Durability:** Nach dem Commit sind die Änderungen dauerhaft gespeichert, auch bei Systemabstürzen.

Unterscheiden Sie die Bedeutung des Begriffs „Consistency“ (Konsistenz) innerhalb des ACID-Prinzips von der Verwendung im CAP-Theorem für verteilte Datenbanken.
?
**ACID-Konsistenz** bezieht sich auf die _Integrität_: Eine Transaktion überführt die DB von einem gültigen Zustand in den nächsten unter strikter Einhaltung aller definierten Geschäftsregeln (z.B. referentielle Integrität). **CAP-Konsistenz** bezieht sich auf die _Einheitlichkeit_ (Linearisierbarkeit): Jeder Lesevorgang (egal auf welchem Knoten der Welt) liefert zwingend den Wert des jüngsten Schreibvorgangs.

Vergleichen Sie das ACID-Prinzip mit dem BASE-Modell hinsichtlich der Konsistenzgarantien.
?
**ACID** garantiert sofortige, strikte Konsistenz direkt nach dem Abschluss (Commit) jeder einzelnen Transaktion. **BASE** akzeptiert einen vorübergehend inkonsistenten Zustand (den sogenannten „Soft State“), um eine höhere System-Verfügbarkeit und Skalierbarkeit zu erreichen. Die Konsistenz wird hier verzögert etabliert („Eventual Consistency“).
<!--SR:!2026-06-10,0,230-->

Wie wird selbst bei rasend schnellen In-Memory-Datenbanken (wie SAP HANA) die „Durability“ (Dauerhaftigkeit) garantiert, obwohl die Daten im flüchtigen Arbeitsspeicher liegen?
?
Durch ein Zusammenspiel von Savepoints und Redo Logs. Sämtliche committeten Transaktionsänderungen werden sofort synchron in ein Redo Log auf einen nichtflüchtigen Speicher (Festplatte) geschrieben. Zudem sichern zeitgesteuerte Savepoints den kompletten In-Memory-Zustand regelmäßig auf der Platte ab.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[ACID]]
SORT file.mtime DESC
```