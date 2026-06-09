#Note

2026-06-09

Tags: [[Datenbanken]], [[Grundlagen]], [[Relationenmodell]]
#datenbanken 

---
Die **Relationale Datenbank (RDBMS)** bildet seit den 1980er Jahren den Industriestandard für strukturierte Datenhaltung. Das zugrundeliegende theoretische Relationenmodell wurde 1970 von **Edgar F. Codd** ("A Relational Model of Data for Large Shared Data Banks") entwickelt und basiert rein auf der mathematischen Mengentheorie.

In diesem Modell werden sämtliche Informationen ausschließlich in Form von flachen Tabellen (den Relationen) abgebildet. Die zentrale Sprache zur Definition (DDL), Manipulation (DML) und Abfrage (DQL) dieser Tabellen ist **SQL**.

#### Formale Terminologie

Um die mathematische Basis (die [[Relationenalgebra]]) zu verstehen, müssen die informellen Alltagssprache-Begriffe zwingend in die formale relationale Sprache übersetzt werden:

|Formale relationale Bezeichnung|Informelle Bezeichnung (Alltag)|
|---|---|
|**Relation**|Tabelle (bestehend aus Kopf und Rumpf)|
|**Tupel**|Eine einzelne Zeile (Datensatz) innerhalb der Tabelle|
|**Attribut**|Eine Spalte (Feld) der Tabelle|
|**Kardinalität** (der Relation)|Anzahl der Zeilen (Tupel) in der Tabelle|
|**Grad**|Anzahl der Spalten (Attribute) der Tabelle|
|**Primärschlüssel**|Eindeutiger Identifikator eines Tupels|
|**Gebiet (Domäne)**|Die Definitionsmenge aller zulässigen Werte für ein Attribut|

#### Die 4 zwingenden Eigenschaften einer Relation

Damit eine Tabelle mathematisch als echte Relation gilt und durch die Relationenalgebra verarbeitet werden kann, muss sie zwingend vier Eigenschaften aufweisen:

1. **Es gibt keine doppelten Tupel:** Jede Zeile muss sich von allen anderen Zeilen unterscheiden. In der Praxis wird diese Eindeutigkeit durch den Einsatz eines zwingenden Primärschlüssels garantiert.
2. **Tupel sind nicht geordnet:** Die Zeilen unterliegen keiner inhärenten Reihenfolge (Set-Semantik).
3. **Attribute sind nicht geordnet:** Die Reihenfolge der Spalten verändert die Relation logisch nicht.
4. **Alle Attribute sind atomar:** Jede Zelle der Tabelle darf nur einen einzigen, nicht weiter unterteilbaren Wert (aus ihrer Definitionsmenge) enthalten (sog. 1. Normalform).

#### Abgrenzung zu [[NoSQL]]

Während relationale Systeme auf ein starres, vorab definiertes Schema (Schema on Write) und absolute Datenintegrität ([[ACID]]) setzen, verzichten moderne NoSQL-Datenbanken (z. B. Dokumentendatenbanken wie [[MongoDB]]) zugunsten von Skalierbarkeit und Agilität oft bewusst auf flache Tupel, strenge Normalisierung und komplexe JOINs.

--------------------------------------------------------------------------------

Flashcards

Wer hat das theoretische Fundament für das relationale Datenmodell entwickelt und wann?::Edgar Frank Codd im Jahr 1970.

Übersetze die drei wichtigsten Datenbank-Alltagsbegriffe (Tabelle, Zeile, Spalte) in die formale relationale Terminologie.::Tabelle = Relation, Zeile = Tupel, Spalte = Attribut.

Was bedeuten die Begriffe "Grad" und "Kardinalität" im Kontext einer relationalen Tabelle?
?
Der **Grad** beschreibt die Anzahl der Spalten (Attribute) der Tabelle. Die **Kardinalität** einer Relation beschreibt die Anzahl der Zeilen (Tupel) in der Tabelle.

Nenne die vier mathematischen Grundeigenschaften, die eine Tabelle erfüllen muss, um als korrekte Relation zu gelten.
?
1. Keine doppelten Tupel (Zeilen sind zwingend eindeutig).
2. Tupel (Zeilen) sind nicht geordnet.
3. Attribute (Spalten) sind nicht geordnet.
4. Alle Attribute sind atomar (enthalten keine zusammengesetzten Werte).

Wie werden Beziehungen zwischen Entitäten im relationalen Datenmodell physisch umgesetzt?::Es gibt keine direkten Zeiger/Pointer (wie in Graphdatenbanken). Beziehungen werden rein logisch über Wertegleichheit durch Primär- und Fremdschlüssel (Foreign Keys) simuliert, die bei Bedarf durch JOINs zusammengeführt werden.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Relationale Datenbank]]
SORT file.mtime DESC
```