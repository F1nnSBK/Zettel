#Note

2026-06-09

Tags: [[Mathematik]], [[Mengenlehre]], [[Menge]], [[Datenbanken]], [[Grundlagen]], [[Relationenalgebra]], [[SQL]]
#datenbanken 

---
Die **mengenorientierten Operatoren** der Relationenalgebra verknüpfen ganze Tabellenmengen miteinander. Während ein Join (relationenorientiert) Tabellen _horizontal_ um neue Spalten erweitert, verbinden Mengenoperatoren die Teilergebnisse _vertikal_ (sie hängen Zeilen aneinander oder ziehen sie voneinander ab).

#### Die eiserne Regel: Schema-Kompatibilität

Damit zwei Relationen (oder SQL-Ergebnismengen) über Mengenoperatoren kombiniert werden können, müssen sie zwingend **schema-kompatibel (vereinigungsverträglich)** sein. Das bedeutet in der Praxis:

1. Beide SELECT-Abfragen müssen exakt **gleich viele Spalten** zurückgeben.
2. Die Spalten auf den jeweils gleichen Positionen müssen **kompatible Datentypen** besitzen (sie müssen nicht identisch heißen, aber vom selben Typ sein).

**Wichtig für SQL:** Die endgültigen Spaltennamen der Ergebnisrelation werden _immer_ von der allerersten SELECT-Abfrage diktiert.

Die 3 Kernoperatoren (und ihre SQL-Pendants)

| Operator                        | Symbol | SQL         | Funktion & Bedeutung                                                                             |
| ------------------------------- | ------ | ----------- | ------------------------------------------------------------------------------------------------ |
| **Vereinigung** (Union)         | ∪      | `UNION`     | Alle Tupel aus R und S. Beantwortet "**Oder**"-Fragen ("Kunden in Berlin _oder_ mit Lieferung"). |
| **Durchschnitt** (Intersection) | ∩      | `INTERSECT` | Nur Tupel, die in **beiden** Relationen gleichzeitig vorkommen. Beantwortet "**Und**"-Fragen.    |
| **Differenz** (Except / Minus)  | ∖      | `EXCEPT`    | Tupel aus R, die **nicht** in S vorkommen. Beantwortet "**Aber nicht**"-Fragen.                  |

_(Hinweis zur Symmetrischen Differenz / XOR: Ein exklusives "Entweder-Oder" erfordert in der Mengenlehre die Kombination:_ (A∖B)∪(B∖A)_.)_

#### Besonderheiten in der SQL-Umsetzung

Die Relationenalgebra basiert auf reinen Mengen (Sets), in denen keine Duplikate existieren dürfen. SQL arbeitet hingegen standardmäßig mit "Bags" (Multimengen), weshalb ein normales `SELECT` Duplikate zulässt.

Bei der Verwendung von Mengenoperatoren in SQL gilt jedoch:

- **Duplikat-Eliminierung:** `UNION`, `INTERSECT` und `EXCEPT` entfernen automatisch alle Duplikate, um mathematisch korrekt zu bleiben.
- **Performance-Bypass:** Da das Entfernen von Duplikaten sehr rechenintensiv ist, kann in SQL der Zusatz `ALL` (z.B. `UNION ALL`) angehängt werden, wodurch Duplikate explizit beibehalten werden.
- **Sortierung:** Ein `ORDER BY` zur Sortierung der Endergebnismenge darf in der gesamten Query nur **ein einziges Mal ganz am Ende** stehen.

--------------------------------------------------------------------------------

### Flashcards

Was ist der fundamentale Unterschied zwischen Joins und Mengenoperatoren bei der Tabellenverknüpfung?::Joins verknüpfen Tabellen **horizontal** (Spalten werden nebeneinandergelegt). Mengenoperatoren verknüpfen Tabellen **vertikal** (Zeilen der einen Abfrage werden unter oder gegen die Zeilen der anderen gestellt).

Was bedeutet es, wenn zwei Tabellen "schema-kompatibel" (vereinigungsverträglich) sein müssen?
?
Es ist die Grundvoraussetzung für Mengenoperatoren. Es bedeutet, dass beide Tabellen (bzw. SELECTs) **exakt gleich viele Spalten** haben müssen und die Spalten an den jeweiligen Positionen **kompatible Datentypen** aufweisen müssen.

Welche drei mengenorientierten Operatoren gibt es und wie lauten ihre SQL-Pendants?::1. Vereinigung (∪ / UNION), 2. Durchschnitt/Schnittmenge (∩ / INTERSECT), 3. Differenz (∖ / EXCEPT oder MINUS).

Was ist der funktionale Unterschied zwischen `UNION` und `UNION ALL` in SQL?::`UNION` verhält sich wie die mathematische Relationenalgebra und **eliminiert automatisch alle Duplikate**. `UNION ALL` überspringt diesen rechenintensiven Schritt und behält alle doppelten Datensätze bei.

Wo darf die Sortierung (`ORDER BY`) in einer Abfrage mit Mengenoperatoren (z.B. UNION) stehen?::Nur ein einziges Mal, und zwar ganz am Ende der gesamten kombinierten SQL-Anweisung.

Wie lässt sich der `EXCEPT`-Operator (Differenz) durch einen relationenorientierten Operator in SQL umschreiben?::Durch einen `LEFT JOIN`, bei dem man anschließend in der WHERE-Klausel nach `IS NULL` im Fremdschlüssel filtert (um nur die Datensätze zu behalten, die keinen Treffer in der rechten Tabelle haben).


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Mengenorientierte Operatoren]]
SORT file.mtime DESC
```