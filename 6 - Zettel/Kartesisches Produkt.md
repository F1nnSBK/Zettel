#Note

2026-06-09

Tags: [[Kartesisches Produkt]], [[Mengenorientierte Operatoren]], [[Relationenalgebra]], [[Join]], [[Relationenorientierte Operatoren]], [[Menge]]
#datenbanken 

---
Das **Kartesische Produkt** (oder Kreuzprodukt, Symbol: ×) ist ein fundamentaler Operator der Relationenalgebra. Es verknüpft zwei Relationen miteinander, indem es **jeden** Datensatz (Tupel) der ersten Tabelle mit **jedem** Datensatz der zweiten Tabelle kombiniert.

#### Die mathematische Dimension (n×m)

Das Kreuzprodukt ist eine rein mechanische Multiplikation von Mengen, die keinerlei inhaltliche Beziehungen oder Wertegleichheiten prüft:

- **Tupel (Zeilen):** Hat Relation A n Tupel und Relation B m Tupel, so besitzt das Kartesische Produkt exakt n⋅m Tupel.
- **Attribute (Spalten):** In der Ergebnisrelation werden sämtliche Spalten von A und B nebeneinandergestellt (addiert).

_Beispiel:_ Wenn wir eine Tabelle `Kunden` (5 Zeilen) und eine Tabelle `Artikel` (10 Zeilen) über ein Kreuzprodukt verknüpfen, erhalten wir eine gigantische Tabelle mit 5×10=50 Zeilen. Jeder Kunde ist dann (theoretisch) jedem Artikel einmal zugeordnet. In der Praxis ist das isoliert angewendet **selten sinnvoll**.

#### Die Brücke zu SQL und Joins

In SQL wird das Kartesische Produkt ausgelöst, wenn man in der `FROM`-Klausel einfach mehrere Tabellen mit einem Komma trennt, ohne eine Verknüpfungsbedingung anzugeben.

```sql
-- Erzeugt ein gigantisches Kartesisches Produkt (Alle mit Allen)
SELECT * FROM account, customer;
```

**Der Weg zum Join:** Ein sinnvolles Ergebnis entsteht erst, wenn wir diesen gigantischen Kombinationsraum durch eine logische **[[Selektion]]** (eine `WHERE`-Klausel) wieder drastisch einschränken. Suchen wir aus dem Kartesischen Produkt nur die Zeilen heraus, bei denen der Fremdschlüssel dem Primärschlüssel entspricht, haben wir mathematisch einen **Equi-Join** (bzw. Inner Join) simuliert.

```sql
-- Ein Kartesisches Produkt, das durch Selektion (WHERE) zum Join wird
SELECT * 
FROM account, customer 
WHERE account.customer_id = customer.customer_id;
```

_Hinweis:_ SQL fordert hierbei die eindeutige Benennung der Attribute durch Voranstellen des Tabellennamens (`tabelle.attribut`), damit klar ist, welche Spalte aus welcher Ursprungstabelle gemeint ist.

--------------------------------------------------------------------------------

### Flashcards

Was macht der Operator "Kartesisches Produkt" (×) in der [[Relationenalgebra]]?::Er kombiniert jeden Datensatz (Tupel) der ersten Tabelle bedingungslos mit jedem Datensatz der zweiten Tabelle.

Wie berechnet sich die Anzahl der Zeilen (Tupel) im Ergebnis eines Kartesischen Produkts?::Wenn Tabelle A n Tupel hat und Tabelle B m Tupel, hat das Ergebnis exakt n⋅m Tupel.

Wie wird ein Kartesisches Produkt im klassischen SQL-Syntax (ohne JOIN-Schlüsselwort) erzeugt?::Indem man in der `FROM`-Klausel einfach beide Tabellennamen mit einem Komma getrennt auflistet (z. B. `SELECT * FROM account, customer;`).
<!--SR:!2026-06-10,0,230-->

Warum ist das Kartesische Produkt das mathematische Fundament für Datenbank-Joins?
?
Weil ein Join logisch gesehen nichts anderes ist als die Ausführung eines extrem großen Kartesischen Produkts, auf das unmittelbar danach eine Selektion (WHERE-Bedingung) angewandt wird, um nur die passenden Primär-/Fremdschlüssel-Paare übrig zu lassen.
<!--SR:!2026-06-11,1,230-->

Was muss in SQL zwingend beachtet werden, wenn Attribute aus zwei Tabellen im Kreuzprodukt gleich heißen (z.B. customer_id)?::Den Attributen muss der jeweilige Tabellenname durch einen Punkt getrennt vorangestellt werden (z. B. `customer.customer_id`), um Mehrdeutigkeiten aufzulösen.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Kartesisches Produkt]]
SORT file.mtime DESC
```