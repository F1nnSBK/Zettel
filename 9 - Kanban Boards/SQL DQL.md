#Note

2026-06-09

Tags: [[Relationale Datenbank]], [[Datenbanksystem]], [[Relationenorientierte Operatoren]], [[Join]], [[Kartesisches Produkt]], [[Daten]], [[SQL DDL]], [[SQL DML]]
#datenbanken 

---
Die **Data Query Language (DQL)** besteht primär aus einem einzigen, extrem mächtigen Befehl: `SELECT`. Sie ist deklarativ (deskriptiv), das heißt, sie beschreibt das gesuchte Ergebnis, ohne den genauen Suchalgorithmus vorzugeben.

Eine SQL-Abfrage wirkt immer mengenorientiert und liefert als Ergebnis **immer** wieder eine Tabelle (Result Set) zurück.

Anatomie des SELECT-Befehls

Nur zwei Klauseln sind in einer Abfrage zwingend erforderlich: `SELECT` (die Spaltenauswahl) und `FROM` (die Tabellenauswahl). Alle anderen Klauseln sind optional.

Die formale Struktur sieht wie folgt aus:

```sql
SELECT [DISTINCT] Spaltenliste        -- 3. Projektion (Welche Spalten?)
FROM Tabelle                          -- 1. Quelle (Woher?)
[WHERE Bedingung]                     -- 2. Selektion (Welche Zeilen?)
[GROUP BY Spaltenliste]               -- 4. Gruppierung
[HAVING Bedingung]                    -- 5. Filterung der Gruppen
[ORDER BY Spaltenliste] [ASC|DESC]    -- 6. Sortierung
[LIMIT Anzahl] [OFFSET Startpunkt];   -- 7. Paginierung
```

_(Hinweis: Die Zahlen in den Kommentaren geben die ungefähre logische Abarbeitungsreihenfolge durch die Datenbank an, die stark von der Schreibweise abweicht!)_.

Wichtige Konzepte und Besonderheiten

1. **Menge vs. Multimenge (Bag):** Eine normale Abfrage liefert eine _Multimenge_ zurück, in der Zeilen doppelt vorkommen können (aus Performancegründen). Erst das explizite Hinzufügen des Schlüsselworts `DISTINCT` zwingt das System, Duplikate zu entfernen und eine mathematisch korrekte _Menge_ zu liefern.
2. **Umgang mit NULL-Werten:** `NULL` steht für einen unbekannten Wert. Daher schlagen Vergleiche wie `WHERE alter = NULL` immer fehl. Es muss zwingend die Syntax `IS NULL` oder `IS NOT NULL` verwendet werden. Zudem werden NULL-Werte bei der Berechnung von Aggregatfunktionen (wie `SUM` oder `AVG`) vom System ignoriert.
3. **Mustererkennung (Wildcards):** Für Textdurchsuchungen (`LIKE`) gibt es zwei Wildcards. Das Prozentzeichen `%` steht für eine _beliebige_ Anzahl von Zeichen (oder gar keines), während der Unterstrich `_` für _exakt ein_ beliebiges Zeichen steht.

--------------------------------------------------------------------------------

Flashcards (Offizielle Wiederholungsfragen)

Welchen Zweck erfüllen die Klauseln LIMIT und OFFSET? Für welche typische Funktionalität in Webanwendungen bilden sie die Grundlage?
?
`LIMIT` begrenzt die Anzahl der zurückgegebenen Zeilen. `OFFSET` überspringt eine bestimmte Anzahl von Zeilen am Anfang. Zusammen bilden sie die Grundlage für die Paginierung (Seitenblätterfunktion) in Webanwendungen.
<!--SR:!2026-06-11,1,230-->

Erklären Sie den fundamentalen Unterschied zwischen der WHERE-Klausel und der HAVING-Klausel in Bezug darauf, wann und worauf sie die Filterung anwenden.
?
Die `WHERE`-Klausel filtert die "Datengrundlage" (einzelne Zeilen) **vor** der Gruppierung. Die `HAVING`-Klausel filtert das aggregierte Ergebnis (Datensatzgruppen) erst **nach** der Gruppierung durch `GROUP BY`.
<!--SR:!2026-06-10,0,230-->

Was passiert, wenn man in der SELECT-Liste eine Spalte angeben möchte, die nicht in der GROUP BY-Klausel aufgeführt ist und auch keine Aggregatfunktion darauf angewendet wird? ?
Das ist nicht erlaubt und wirft einen Fehler. In der SELECT-Liste dürfen bei Verwendung von `GROUP BY` **nur** die Attribute stehen, nach denen auch gruppiert wird, oder eben berechnete Aggregatfunktionen (wie SUM, COUNT).

Warum kann man nicht `WHERE spaltenname = NULL` schreiben, um nach leeren Werten zu filtern, und welche Syntax wird stattdessen verwendet?
?
`NULL` repräsentiert einen _unbekannten_ Wert und kann daher mathematisch nicht mit einem Gleichheitszeichen (=) verglichen werden. Stattdessen muss zwingend die Syntax `IS NULL` oder `IS NOT NULL` verwendet werden.

Was ist der Unterschied zwischen den beiden Wildcards `%` und `_` bei der Verwendung des `LIKE`-Operators in einer WHERE-Klausel?
?
Das Prozentzeichen (`%`) steht für eine beliebige Anzahl von beliebigen Zeichen (oder kein Zeichen). Der Unterstrich (`_`) steht für **genau ein** einziges beliebiges Zeichen.

In welcher Reihenfolge werden eine Hauptabfrage und eine einfache, nicht-korrelierte Unterabfrage typischerweise von der Datenbank ausgeführt?
?
Verschachtelte Abfragen werden (sofern sie nicht-korreliert sind) immer von unten nach oben bzw. von innen nach außen abgearbeitet. Die Datenbank führt zuerst die innere Unterabfrage aus und verwendet deren Ergebnis dann für die äußere Hauptabfrage.

Was unterscheidet eine korrelierte (abhängige) Unterabfrage von einer einfachen Unterabfrage in Bezug auf ihre Ausführung?
?
Eine korrelierte Unterabfrage hängt für ihre Werte von der äußeren Hauptabfrage ab. Sie kann nicht isoliert ausgeführt werden. Stattdessen wird sie (ähnlich einer geschachtelten Schleife) für **jede einzelne Zeile** der äußeren Abfrage immer wieder neu ausgeführt.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[SQL DQL]]
SORT file.mtime DESC
```