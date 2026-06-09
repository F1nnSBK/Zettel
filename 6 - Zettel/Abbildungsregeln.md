#Note

2026-06-09

Tags: [[Abbildungsregeln]], [[Entity-Relationship-Modell]], [[Relationenmodell]], [[Datenbankentwurf]], [[Relationale Datenbank]], [[Kardinalität]], [[MC-Kardinalität]], [[Entität]], [[Attribut]], [[Beziehungstyp]], [[Assoziation]], [[Generalisierung]]
#datenbanken

---
Die **Abbildungsregeln** (Transformationsregeln) definieren den formalen Übergang vom konzeptionellen Datenmodell (dem ERM-Diagramm) in das logische Relationenmodell. Sie geben präzise vor, wie aus Rechtecken (Entities), Ellipsen (Attributen) und Rauten (Beziehungen) relationale Tabellen, Spalten und Schlüssel entstehen.

Hier sind die vier essenziellen Grundregeln mit konkreten Beispielen:

Regel 1: Entitytypen zu Tabellen

Jeder Entitytyp im ERM wird als eine eigenständige Tabelle (Relation) umgesetzt.

- Die einfachen **Attribute** des Entitytyps werden zu den Spalten der Tabelle.
- Das **Schlüsselattribut** des Entitytyps wird zum **Primärschlüssel (Primary Key, PK)** der Tabelle und (formal) unterstrichen.

**Beispiel aus dem Skript:**

- **ERM:** Entitytyp `Lieferant` mit Schlüssel `LNr` und Attributen `Name`, `Adresse`.
- **Relation:** `Lieferant(LNr, Name, Adresse)`.
- **ERM:** Entitytyp `Artikel` mit Schlüssel `ANr` und Attributen `Bezeichnung`, `Preis`.
- **Relation:** `Artikel(ANr, Bezeichnung, Preis)`.

--------------------------------------------------------------------------------

Regel 2: 1:1 Kardinalität

Wenn zwischen zwei Entitäten eine 1:1-Beziehung besteht, gibt es zwei Lösungswege:

1. Der Primärschlüssel der _einen_ Tabelle wird als **Fremdschlüssel (Foreign Key, FK)** in die _andere_ Tabelle aufgenommen.
2. _Oder:_ Integration aller Attribute beider Entitäten in eine einzige, große Tabelle (Verschmelzung), sofern es funktional sinnvoll ist.

**Beispiel:** Ein `Mitarbeiter` (1) hat genau einen `Dienstwagen` (1).

- **Relationen:** `Mitarbeiter(MitarbeiterNr, Name)` `Dienstwagen(Kennzeichen, Modell, MitarbeiterNr [FK])`

--------------------------------------------------------------------------------

Regel 3: 1:n Kardinalität

Dies ist der häufigste Fall in Datenbanken (sog. Master-Detail-Beziehung).

- Der **Primärschlüssel der "1"-Entität** wandert zwingend als **Fremdschlüssel** in die Tabelle der **"n"-Entität**.

**Beispiel aus dem Skript:** Ein `Lieferant` (1) liefert mehrere `Artikel` (n). Ein Artikel wird aber nur von genau einem Lieferanten geliefert.

- **Relation 1-Seite:** `Lieferant(LNr, Name, Adresse)`
- **Relation n-Seite:** `Artikel(ANr, Bezeichnung, Preis, LNr [FK])` _(Der Artikel "merkt" sich, von wem er kommt)._

--------------------------------------------------------------------------------

Regel 4: n:m Kardinalität

Das relationale Modell kann n:m-Beziehungen _nicht_ direkt über einfache Fremdschlüssel abbilden.

- Eine n:m-Beziehung wird zwingend in eine **neue, zusätzliche Tabelle** (eine sogenannte Assoziations- oder Beziehungstabelle) umgewandelt.
- Diese neue Tabelle enthält als **zusammengesetzten Primärschlüssel** die beiden Primärschlüssel der beteiligten Entitätstypen.
- Wenn der Beziehungstyp im ERM eigene Attribute besaß (z.B. ein Datum oder eine Menge), werden diese als einfache Spalten in diese neue Tabelle übernommen.

**Beispiel aus dem Skript:** Ein `Lieferant` (n) liefert viele `Artikel` (m) und ein Artikel wird von vielen Lieferanten geliefert. An der Raute "liefert" hängt das Attribut `Liefermenge`.

- **Relation A:** `Lieferant(LNr, Name, Adresse)`
- **Relation B:** `Artikel(ANr, Bezeichnung, Preis)`
- **Neue Beziehungstabelle:** `liefert(LNr [PK/FK], ANr [PK/FK], Liefermenge)`

--------------------------------------------------------------------------------

### Flashcards

Wie werden Entitytypen und ihre Eigenschaften im Relationenmodell abgebildet?::Jeder Entitytyp wird zu einer Tabelle. Die Attribute werden zu Spalten, und das identifizierende Attribut wird zum Primärschlüssel (PK).

Wie lautet die Abbildungsregel für eine 1:1-Beziehung?::Der Primärschlüssel der einen Tabelle wird als Fremdschlüssel in die andere Tabelle aufgenommen, oder beide Entitäten werden vollständig in einer einzigen Tabelle verschmolzen.

Wie lautet die zwingende Abbildungsregel für eine 1:n-Beziehung?
?
Der Primärschlüssel der Entität auf der "1"-Seite wird als Fremdschlüssel in die Tabelle der Entität auf der "n"-Seite übernommen. (Die "n"-Seite speichert den Verweis auf ihren "Master").

Wie wird eine n:m-Beziehung im relationalen Datenbankdesign physisch gelöst?
?
Sie muss zwingend in eine neue, zusätzliche Assoziationstabelle (Beziehungstabelle) umgewandelt werden. Diese enthält die Primärschlüssel der beiden beteiligten Tabellen als zusammengesetzten Primärschlüssel.

Was passiert mit Attributen, die im ERM direkt an einem n:m-Beziehungstyp hängen (z.B. "Liefermenge")?::Sie werden zu regulären Spalten in der neu generierten Assoziationstabelle.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Abbildungsregeln]]
SORT file.mtime DESC
```