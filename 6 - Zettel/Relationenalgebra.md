#Note

2026-06-09

Tags: [[Relationenalgebra]], [[Relationenorientierte Operatoren]], [[Mengenorientierte Operatoren]], [[Kartesisches Produkt]], [[Join]], [[Logische Operatoren]], [[Relationenmodell]], [[Relationale Datenbank]], [[Datenbanksystem]]
#datenbanken 

---
Die **Relationenalgebra** ist das abstrakte, formale System zur Manipulation von Tabellen in relationalen Datenbanken. Sie arbeitet mit Operatoren, um Daten abzufragen, zu filtern und neu zu kombinieren, **ohne** die physischen Quelldaten zu verändern. Das Resultat jeder Operation ist konzeptionell immer wieder eine völlig neue Relation (Tabelle).

"Why all that Math?" - Die Brücke zur Data Science

Die Algebra dient als zwingender Übersetzungs-Layer. Wenn das Marketing fragt: _"Welche Kunden wohnen in Berlin oder sind älter als 30?"_, transformiert die Relationenalgebra dies in eine formale Logik: σStadt=’Berlin’∨Alter>30​(Kunden). Erst daraus wird der fertige SQL-Code (`SELECT ... WHERE ...`).

Die 3 Kategorien der Operatoren

Die Algebra teilt ihre Werkzeuge in drei funktionale Blöcke auf:

1. Relationenorientierte Operatoren (Strukturorientiert)

Sie arbeiten auf den Attributen (Spalten) und Tupeln (Zeilen) oder verknüpfen Tabellen in der Breite.

| Operator                        | Symbol    | SQL-Pendant        | Funktion / Beschreibung                                                                                                                                             |
| ------------------------------- | --------- | ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **[[Projektion]]**              | π (Pi)    | `SELECT`           | Spaltenauswahl. Reduziert die Tabelle vertikal auf bestimmte Attribute (eliminiert dabei formal Duplikate).                                                         |
| **[[Selektion]] (Restriktion)** | σ (Sigma) | `WHERE` / `HAVING` | Zeilenauswahl. Filtert Tupel horizontal, wenn sie eine logische Bedingung (WAHR) erfüllen.                                                                          |
| **[[Kartesisches Produkt]]**    | ×         | `FROM R1, R2`      | Bildet alle möglichen Kombinationen von Tupeln aus zwei Relationen (Ergibt n⋅m Zeilen).                                                                             |
| **[[Join]] (Verbund)**          | ⋈         | `JOIN ... ON`      | Verknüpft zwei Relationen basierend auf gemeinsamen Werten (meist Primary Key = Foreign Key). Ist logisch betrachtet ein Kreuzprodukt mit anschließender Selektion. |

2. Mengenorientierte Operatoren

Sie kombinieren ganze Ergebnisseiten miteinander. **Wichtige Voraussetzung:** Die beteiligten Relationen müssen _schema-kompatibel_ (vereinigungsverträglich) sein (gleiche Anzahl an Spalten, gleiche Datentypen).

|Operator|Symbol|SQL-Pendant|Funktion / Beschreibung|
|---|---|---|---|
|**Vereinigung**|∪|`UNION`|Alle Tupel aus R und S (ohne Duplikate).|
|**Schnittmenge**|∩|`INTERSECT`|Nur Tupel, die in **beiden** Relationen vorkommen.|
|**Differenz**|∖|`EXCEPT` / `MINUS`|Tupel aus R, die **nicht** in S vorkommen.|

3. Logische Operatoren (Bedingungsbasiert)

Sie liefern Wahrheitswerte (Boolesche Algebra) und werden meist **innerhalb** der Selektion (σ) eingesetzt, um komplexe Filter zu bauen.

|Operator|Symbol (Menge / Logik)|SQL|Funktion|
|---|---|---|---|
|**Negation (NOT)**|Ac / ¬|`NOT`|Kehrt die Bedingung um.|
|**Konjunktion (AND)**|∩ / ∧|`AND`|Alle Bedingungen müssen zutreffen.|
|**Disjunktion (OR)**|∪ / ∨|`OR`|Mindestens eine Bedingung muss zutreffen.|
|**Antivalenz (XOR)**|- / ⊕|`(A OR B) AND NOT (A AND B)`|Genau EINE Bedingung ist wahr, aber nicht beide.|

**Prioritätsregel der Logik:** Falls keine Klammern gesetzt sind, verarbeitet das System die Operatoren in dieser strengen Reihenfolge: **Klammer** → **NOT** → **AND** → **OR** → **XOR**.

--------------------------------------------------------------------------------

### Flashcards

Was ist das Ziel der Relationenalgebra im Kontext von Datenbanken?::Sie ist das formale, mathematische System zur Abfrage und Manipulation von Datenmengen, das als Übersetzer zwischen unstrukturierten Fachanforderungen und dem technischen SQL-Code dient.
<!--SR:!2026-06-10,0,230-->

Was ist der Unterschied zwischen der Projektion (π) und der Selektion (σ)?
?
Die **Projektion (**π**) / SELECT** wählt Spalten aus (vertikale Reduktion). Die **Selektion (**σ**) / WHERE** filtert Zeilen (Tupel) basierend auf einer logischen Bedingung (horizontale Reduktion).
<!--SR:!2026-06-10,0,230-->

Welche zwingende Voraussetzung gilt für die Anwendung von Mengenoperatoren (wie ∪ oder ∩) auf zwei Tabellen?::Die Tabellen müssen schema-kompatibel (vereinigungsverträglich) sein. Sie müssen die gleiche Anzahl an Attributen und identische/kompatible Datentypen an den jeweiligen Positionen aufweisen.

Wie ist der Join (Verbund ⋈) mathematisch in der Relationenalgebra definiert?::Ein Join ist konzeptionell die Ausführung eines Kartesischen Produkts (×) zweier Relationen, auf das unmittelbar eine Selektion (σ) angewendet wird, um nur die treffenden Zeilen zu behalten.

In welcher Reihenfolge (Priorität) werden logische Operatoren in einer Bedingung aufgelöst, wenn keine Klammern gesetzt sind?::Klammer → NOT (¬) → AND (∧) → OR (∨) → XOR (⊕).
<!--SR:!2026-06-13,3,250-->


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Relationenalgebra]]
SORT file.mtime DESC
```