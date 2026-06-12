#Note

2026-06-12

Tags: [[Datenbanken]], [[NoSQL]], [[Neo4j]], [[Graphentheorie]], [[Cypher]]
#datenbanken 

---
**Graphdatenbanken** (wie Neo4j, ab 2000 entwickelt) lösen ein massives Problem relationaler Systeme: Die Ineffizienz bei stark vernetzten Daten.

Das Problem: Die JOIN-Bomb

In SQL existieren Beziehungen nur logisch (als Fremdschlüssel). Will man "Freunde von Freunden" abfragen, muss die RDBMS zur Laufzeit teure Suchvorgänge und Tabellen-JOINs durchführen. Je tiefer die Abfrage geht, desto exponentiell größer wird der Rechenaufwand – das System kollabiert (Join Bomb).

Die Lösung: Index-free Adjacency (Indexfreie Nachbarschaft)

Neo4j persistiert Beziehungen physisch als direkte Pointer am Datensatz. Das Suchen nach dem "nächsten Freund" ist kein Tabellen-Scan mehr, sondern nur noch ein direkter Sprung im Arbeitsspeicher (Traversierung in konstanter Zeit).

Das Datenmodell (Property Graph)

Daten werden nicht in Zeilen und Spalten abgelegt, sondern als:

1. **Knoten (Nodes):** Repräsentieren die Entitäten (z. B. eine Person). Sie werden durch **Labels** semantisch gruppiert (z. B. `:Person`).
2. **Kanten (Relationships):** Gerichtete Verbindungen zwischen Knoten (z. B. `ARBEITET_BEI`).
3. **Eigenschaften (Properties):** Key-Value-Paare, die zusätzliche Daten direkt an Knoten _oder_ Kanten speichern (z. B. `seit: 2021` an einer Kante).

Cypher: Die Sprache der Muster

Graphen fragt man nicht mit SQL ab, sondern mit **Cypher**. Cypher nutzt "Pattern Matching" (Mustererkennung) und eine intuitive ASCII-Art-Syntax, um Graphen visuell nachzuzeichnen:

- Knoten stehen in runden Klammern: `(p:Person)`
- Kanten sind Pfeile mit eckigen Klammern: `-[:ARBEITET_BEI]->`
- _Beispiel:_ `MATCH (p:Person {name: 'Alice'})-[:ARBEITET_BEI]->(c:Company) RETURN c`

**Wichtig für Klausuren:** Im Gegensatz zu dokumenten- oder spaltenorientierten Systemen nutzt Neo4j **nicht** das BASE-Modell, sondern ist vollständig **ACID-konform**. Das garantiert sofortige Konsistenz, erschwert aber die horizontale Skalierung bei Schreibzugriffen enorm. Typische Einsatzgebiete sind Empfehlungsalgorithmen (Recommendation Engines), Fraud Detection und Wissensgraphen.

---

### Flashcards

Wann ist der Einsatz einer Graphdatenbank gegenüber anderen NoSQL-Typen vorzuziehen?
?
Eine Graphdatenbank ist immer dann optimal, wenn die komplexen Beziehungen (Vernetzung) zwischen den Datensätzen wichtiger oder auswertungsrelevanter sind als die isolierten Datensätze selbst (z. B. in sozialen Netzwerken, bei Routing-Aufgaben oder Empfehlungsalgorithmen).

Welches Performance-Problem relationaler Datenbanken bei tief vernetzten Daten lösen Graphdatenbanken durch „Indexfreie Adjazenz“?
?
Sie lösen das Problem der sogenannten "Join-Bomb". In SQL werden Beziehungen durch Fremdschlüssel erst zur Laufzeit über extrem rechenintensive JOINs berechnet, was bei tiefen Suchen exponentiell skaliert. "Indexfreie Adjazenz" bedeutet, dass Beziehungen physisch als Pointer gespeichert werden, wodurch das Navigieren (Traversieren) in konstanter Zeit erfolgt, da nichts mehr berechnet werden muss.

Inwiefern unterscheidet sich Neo4j bezüglich der ACID-Konformität von vielen anderen NoSQL-Systemen?
?
Während die meisten NoSQL-Systeme (wie Cassandra oder MongoDB) zugunsten der massiven Skalierbarkeit und Verfügbarkeit auf das BASE-Modell setzen (verzögerte Konsistenz / Eventual Consistency), ist Neo4j vollständig ACID-konform und garantiert strikte, sofortige Transaktionssicherheit.

Erklären Sie das "Property-Graph-Modell" anhand seiner drei Hauptkomponenten.
?
1. **Knoten (Nodes):** Repräsentieren die eigentlichen Entitäten (z. B. Personen oder Produkte).
2. **Kanten (Relationships):** Sind gerichtete Verbindungen, die Knoten miteinander verknüpfen.
3. **Eigenschaften (Properties):** Sind Schlüssel-Wert-Paare, die zusätzliche Daten direkt in den Knoten _und_ auch in den Kanten speichern können.

Wie drückt die Abfragesprache "Cypher" in ihrer Syntax einen Knoten und eine Kante (Beziehung) optisch aus (ASCII-Art)?
?
Knoten werden in Cypher intuitiv durch runde Klammern dargestellt, z. B. `(p:Person)`. Kanten (Beziehungen) werden als Pfeile mit eckigen Klammern dargestellt, z. B. `-[:ARBEITET_BEI]->`.

Welche beiden fundamentalen Schwächen hat Neo4j im Vergleich zu anderen NoSQL-Architekturen?
?
1. Durch die harten ACID-Garantien ist das horizontale Skalieren (Scale-out) von Schreibzugriffen sehr stark erschwert.
2. Es ist architektonisch ungeeignet für massenhafte Daten-Aggregationen und benötigt für die effiziente Graph-Verarbeitung unverhältnismäßig viel Arbeitsspeicher (RAM).


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Graphdatenbank]]
SORT file.mtime DESC
```