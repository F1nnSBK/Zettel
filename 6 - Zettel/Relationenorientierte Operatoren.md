#Note

2026-06-09

Tags: [[Datenbanken]], [[Grundlagen]], [[Relationenalgebra]], [[SQL]]
#datenbanken 

---
Die **relationenorientierten Operatoren** (oder strukturorientierten Operatoren) sind das Herzstück der Datenmanipulation in einer relationalen Datenbank. Sie arbeiten primär auf den Tupeln (Zeilen) und Attributen (Spalten) einer Relation und dienen dem Filtern, Umstrukturieren und Verbinden von Daten.

Jede Ausführung eines solchen Operators erzeugt immer eine neue Relation (Tabelle) als Ergebnis.

Die 5 wichtigsten relationenorientierten Operatoren

| Operator                      | Symbol    | SQL-Befehl         | Funktion & Eigenschaften                                                                                                                                                                                                | Business-Beispiel                                                                        |
| ----------------------------- | --------- | ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| **Projektion**                | π (Pi)    | `SELECT`           | Wählt bestimmte **Attribute (Spalten)** einer Relation aus. Mathematisch gesehen eliminiert die Projektion dabei zwingend alle doppelten Tupel.                                                                         | _"Welche Namen und Städte haben unsere Kunden?"_ →πName,Stadt​(Kunden)                   |
| **Selektion** (Restriktion)   | σ (Sigma) | `WHERE` / `HAVING` | Filtert **Tupel (Zeilen)**, die eine bestimmte Bedingung erfüllen. Nur wenn der logische Ausdruck WAHR ist, wird das Tupel ausgewählt.                                                                                  | _"Welche Kunden wohnen in Berlin?"_ →σStadt=′Berlin′​(Kunden)                            |
| **(Equi-)[[Join]]** (Verbund) | ⋈         | `JOIN ... ON`      | Kombiniert zwei Relationen zu einer neuen. Es werden Tupel verknüpft, bei denen das Join-Prädikat (meist Primary Key = Foreign Key) übereinstimmt. Logisch ist es ein Kartesisches Produkt gefolgt von einer Selektion. | _"Zeige alle Kunden mit ihren zugehörigen Bestellungen."_ →Kunden⋈K.ID=B.ID​Bestellungen |
| **[[Kartesisches Produkt]]**  | ×         | `FROM R1, R2`      | Bildet **alle möglichen Kombinationen** von Tupeln aus zwei Relationen. Hat Tabelle A n Tupel und Tabelle B m Tupel, entstehen n×m Tupel in der neuen Relation.                                                         | _"Prüfe alle denkbaren Kombinationen von Kunden und Artikeln."_ →Kunden×Artikel          |
| **Division**                  | ÷         | --                 | Komplexeres Konzept zur Beantwortung von "ALLE"-Fragen. SQL besitzt dafür **kein eigenes Schlüsselwort**. Es muss über `NOT EXISTS ... NOT EXISTS` oder Gruppierungen mit `COUNT`-Vergleichen gelöst werden.            | _"Finde Kunden, die ALLE angebotenen Produkte gekauft haben."_                           |

_(Hinweis zur Vollständigkeit: Es gibt zudem noch den_ **Umbenennungs-Operator** ρ _(Rho), der in SQL der Vergabe von Aliasen_ _AS_ _entspricht__.)_

Ausführungsreihenfolge

Im Gegensatz zu den strengen Prioritätsregeln bei den logischen Operatoren (AND, OR, NOT) gibt es bei den Relationenoperatoren keine explizite mathematische Reihenfolge. Sie werden in der Regel von **innen nach außen** (bei Verschachtelungen) oder von links nach rechts abgearbeitet. Klammern hebeln jede Standardreihenfolge aus.

--------------------------------------------------------------------------------

### Flashcards

Was ist der funktionale Unterschied zwischen Projektion (π) und Selektion (σ)?
?
Die **Projektion** wählt Spalten aus und reduziert die Tabelle _vertikal_ (inkl. Eliminierung von Duplikaten). Die **Selektion** (Restriktion) wählt Zeilen basierend auf Wahrheits-Bedingungen aus und filtert die Tabelle _horizontal_.

Welchen SQL-Klauseln entsprechen Projektion und Selektion üblicherweise?::Projektion entspricht `SELECT`. Selektion (Restriktion) entspricht `WHERE` (oder `HAVING`).

Was passiert, wenn man ein Kartesisches Produkt (×) auf eine Tabelle A mit 100 Zeilen und eine Tabelle B mit 50 Zeilen anwendet?::Es werden alle möglichen Kombinationen gebildet. Die neue Ergebnisrelation besitzt exakt 100×50=5.000 Zeilen (Tupel).

Wie ist ein Join (Verbund ⋈) mathematisch konzeptioniert?::Ein Join ist eigentlich die Ausführung eines Kartesischen Produkts zweier Relationen, auf dessen gigantische Ergebnismenge direkt danach eine Selektion (σ) angewandt wird, um nur die treffenden Paarungen (z.B. PK = FK) zu behalten.

Warum nimmt die Division (÷) in SQL eine Sonderstellung ein?
?
Weil sie als einziger relevanter relationaler Operator kein natives Schlüsselwort in SQL besitzt. Um komplexe Fragen wie _"Wer hat ALLE Artikel gekauft?"_ zu beantworten, muss man sich in SQL mit doppelten Negationen (`NOT EXISTS ... NOT EXISTS`) behelfen.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Relationenorientierte Operatoren]]
SORT file.mtime DESC
```