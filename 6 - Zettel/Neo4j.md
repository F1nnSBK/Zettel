#Note

2026-06-12

Tags: [[Datenbanken]], [[NoSQL]], [[Neo4j]], [[Graphentheorie]], [[Cypher]]
#datenbanken

---
**Neo4j** wurde ab dem Jahr 2000 von Emil Eifrem entwickelt und löst ein massives Problem relationaler Systeme: Die Ineffizienz bei stark vernetzten Daten.

Das Problem: Die [[JOIN]]-Bomb

In SQL existieren Beziehungen nur logisch als Fremdschlüssel. Will man "Freunde von Freunden" abfragen, muss die R[[DBMS]] zur Laufzeit teure Suchvorgänge und Tabellen-JOINs durchführen. Je tiefer die Abfrage geht, desto exponentiell größer wird der Rechenaufwand – das System kollabiert (Join Bomb).

Die Lösung: Index-free Adjacency (Indexfreie Nachbarschaft)

Neo4j persistiert Beziehungen physisch als direkte Pointer am Datensatz. Das Suchen nach dem "nächsten Freund" ist kein Tabellen-Scan mehr, sondern nur noch ein direkter Sprung im Arbeitsspeicher (Traversierung in konstanter Zeit).

Das Datenmodell (Property Graph)

Daten werden als Eigenschaftsgraph gespeichert:

1. **Knoten (Nodes):** Repräsentieren die Entitäten (z. B. eine Person). Sie werden durch **Labels** semantisch gruppiert (z. B. `:Person`).
2. **Kanten (Relationships):** Gerichtete Verbindungen zwischen Knoten. Sie können ebenfalls Eigenschaften besitzen (z. B. `seit: 2021`).
3. **Eigenschaften (Properties):** Key-Value-Paare, die zusätzliche Daten direkt an Knoten _oder_ Kanten speichern.

Cypher: Die Sprache der Muster

Graphen fragt man nicht mit SQL ab, sondern mit der deklarativen Sprache **Cypher**. Cypher nutzt "Pattern Matching" (Mustererkennung) und eine intuitive ASCII-Art-Syntax, um Graphen visuell nachzuzeichnen:

- Knoten stehen in runden Klammern: `(p:Person)`
- Kanten sind Pfeile mit eckigen Klammern: `-[:ARBEITET_BEI]->`
- _Beispiel:_ `MATCH (p:Person {name: 'Alice'})-[:ARBEITET_BEI]->(c:Company) RETURN c.name`

Schema, Integrität und [[ACID]]

Neo4j hat ein "implizites Schema" – Labels und Properties können zur Laufzeit dynamisch hinzugefügt werden. Die Datenintegrität wird durch explizite **Constraints** (`UNIQUE`, `NOT NULL`) erzwungen, wobei `UNIQUE` als Best Practice für den fehlenden Primärschlüssel fungiert (die internen Neo4j-IDs sind instabil).

**Architektur-Besonderheit:** Im Gegensatz zu dokumenten- oder spaltenorientierten Systemen nutzt Neo4j **nicht** das BASE-Modell, sondern ist vollständig **ACID-konform**. Das garantiert sofortige Konsistenz und Transaktionssicherheit, erschwert aber die horizontale Skalierung (Scale-out) bei Schreibzugriffen enorm und ist für Massen-Aggregationen ungeeignet.

---

### Flashcards

Wann ist der Einsatz einer Graphdatenbank gegenüber anderen [[NoSQL]]-Typen vorzuziehen?
?
Eine Graphdatenbank ist immer dann optimal, wenn die komplexen Beziehungen (Vernetzung) zwischen den Datensätzen wichtiger oder auswertungsrelevanter sind als die isolierten Datensätze selbst (z. B. in Social Media, bei Routing-Aufgaben oder Empfehlungsalgorithmen).

Welches Performance-Problem relationaler Datenbanken bei tief vernetzten Daten lösen Graphdatenbanken durch „Indexfreie Adjazenz“?
?
Sie lösen das Problem der sogenannten "Join-Bomb". In SQL werden Beziehungen durch Fremdschlüssel erst zur Laufzeit über extrem rechenintensive JOINs berechnet, was bei tiefen Suchen exponentiell skaliert. "Indexfreie Adjazenz" bedeutet, dass Beziehungen physisch als Pointer gespeichert werden, wodurch das Navigieren (Traversieren) in konstanter Zeit erfolgt, da nichts mehr berechnet werden muss.

Inwiefern unterscheidet sich Neo4j bezüglich der ACID-Konformität von vielen anderen NoSQL-Systemen?
?
Während die meisten NoSQL-Systeme zugunsten der massiven Skalierbarkeit und Verfügbarkeit auf das BASE-Modell setzen, ist Neo4j vollständig ACID-konform und garantiert strikte, sofortige Transaktionssicherheit.

Erklären Sie das "Property-Graph-Modell" in Neo4j anhand seiner drei Hauptkomponenten.
?
1. **Knoten (Nodes):** Repräsentieren die eigentlichen Entitäten (z. B. Personen).
2. **Kanten (Relationships):** Sind gerichtete Verbindungen, die Knoten miteinander verknüpfen.
3. **Eigenschaften (Properties):** Sind Schlüssel-Wert-Paare, die zusätzliche Daten direkt in den Knoten _und_ auch in den Kanten speichern können.

Wie drückt die Abfragesprache "Cypher" in ihrer Syntax einen Knoten und eine Kante (Beziehung) optisch aus (ASCII-Art)?
?
Knoten werden in Cypher intuitiv durch runde Klammern dargestellt, z. B. `(p:Person)`. Kanten (Beziehungen) werden als Pfeile mit eckigen Klammern dargestellt, z. B. `-[:ARBEITET_BEI]->`.

Wie erzwingt Neo4j Datenintegrität und Primärschlüssel, wenn das System eigentlich schemaflexibel ist?
?
Durch explizite Constraints. Ein `UNIQUE`-Constraint (z.B. auf `p.id`) verhindert Dubletten und fungiert in der Praxis als Primärschlüssel, da die interne Neo4j-ID nicht stabil ist. Ein `NOT NULL`-Constraint erzwingt die Existenz von Pflichtfeldern.

Welche beiden fundamentalen Schwächen hat Neo4j im Vergleich zu anderen Datenbankarchitekturen?
?
1. Durch die harten ACID-Garantien ist das horizontale Skalieren (Scale-out) von Schreibzugriffen sehr stark erschwert.
2. Es ist architektonisch ungeeignet für Massen-Aggregationen und benötigt für die effiziente Graph-Verarbeitung unverhältnismäßig viel Arbeitsspeicher (RAM).


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Neo4j]]
SORT file.mtime DESC
```