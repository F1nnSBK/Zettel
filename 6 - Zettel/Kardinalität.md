#Note

2026-06-09

Tags: [[Kardinalität]], [[MC-Kardinalität]], [[Entity-Relationship-Modell]], [[Beziehungstyp]], [[Assoziation]], [[Abbildungsregeln]], [[Datenbankentwurf]]
#datenbanken

---
Die **Kardinalität** (auch Mächtigkeit genannt) spezifiziert im klassischen Entity-Relationship-Modell (ERM), wie viele Entities (Instanzen) eines Entitytyps mit wie vielen Entities eines anderen Entitytyps in Verbindung stehen.

Während die Assoziation die inhaltliche Natur der Beziehung benennt (z. B. "Kunde _erteilt_ Auftrag"), liefert die Kardinalität die quantitativen Spielregeln (z.B. "Ein Kunde kann _mehrere_ Aufträge erteilen, aber ein Auftrag gehört zu _genau einem_ Kunden").

#### Die (1, m, n)-Notation nach Chen

Das klassische ERM fokussiert sich primär auf die Angabe der **Maximalbeziehung**. Die Kanten des Rauten-Symbols (Beziehungstyp) werden dazu mit Variablen beschriftet:

- **1:** Steht für **0 oder 1**. Ein Entity kann mit maximal einem anderen Entity in Beziehung stehen (kann aber auch ohne Zuordnung bleiben).
- **n** bzw. **m:** Steht für **0, 1 oder viele**. Ein Entity kann mit beliebig vielen anderen Entities assoziiert sein.

#### Die 3 Standard-Kardinalitäten und ihre physische Umsetzung

Die Kardinalität bestimmt beim logischen Datenbankentwurf maßgeblich, wie die Beziehung in einer relationalen Datenbank abgebildet wird ([[Abbildungsregeln]]):

|Kardinalität|Beschreibung (Beispiel)|Physische SQL-Implementierung|
|---|---|---|
|**1 : 1**|_Ein Mann ist (max.) mit einer Frau verheiratet._|Der Primärschlüssel der einen Tabelle wandert als Fremdschlüssel (Foreign Key) in die andere Tabelle (oder beide werden zu einer Tabelle verschmolzen).|
|**1 : n**|_Eine Schulklasse hat viele Schüler (n)._ <br>_Ein Schüler gehört zu genau einer Klasse (1)._|Der Primärschlüssel der "1"-Seite (Klasse) wird als **Fremdschlüssel** in die Tabelle der "n"-Seite (Schüler) eingetragen.|
|**n : m**|_Ein Lieferant (n) liefert viele Artikel (m)._ <br>_Ein Artikel (m) wird von vielen Lieferanten (n) geliefert._|Zwingt zur Erstellung einer **neuen Assoziationstabelle**, welche die Primärschlüssel beider Entities als zusammengesetzten Schlüssel aufnimmt.|

#### Ternäre Kardinalitäten

Bei Beziehungen zwischen genau drei Entitytypen (z.B. _Pilot_, _Flugzeug_, _Flugroute_) wird die Kardinalität (z.B. **n:1:m**) ermittelt, indem man zwei Entities fixiert und fragt, wie viele Entities des dritten Typs damit in Beziehung stehen können. Dies wiederholt man für alle drei Richtungen.

--------------------------------------------------------------------------------

Flashcards

Was ist der formale Unterschied zwischen Assoziation und Kardinalität im ERM?
?
Die Assoziation beschreibt das Vorhandensein und die Art der Beziehung qualitativ (z.B. "Kunde erteilt Auftrag"). Die Kardinalität bestimmt die Beziehung quantitativ, also wie viele Ausprägungen maximal beteiligt sein dürfen (z.B. 1:n).
<!--SR:!2026-06-11,1,230-->

Was bedeuten die Variablen "1" sowie "n/m" in der klassischen Chen-Notation exakt?::"1" bedeutet 0 oder 1. "n" oder "m" bedeutet 0, 1 oder viele. Das klassische ERM beschreibt damit primär die Maximalbeziehung.

Wie wird eine 1:n Kardinalität im logischen Entwurf in eine relationale Datenbank abgebildet?::Der Primärschlüssel des Entitytyps auf der "1"-Seite wird als Fremdschlüssel (Foreign Key) in die Tabelle des Entitytyps auf der "n"-Seite übernommen.

Wie wird eine n:m Kardinalität im relationalen Modell physisch gelöst?::Eine n:m-Beziehung ist direkt nicht abbildbar. Es muss eine zusätzliche Assoziationstabelle (Verbindungstabelle) erstellt werden, die die Primärschlüssel beider beteiligter Tabellen als zusammengesetzten Fremdschlüssel aufnimmt.
<!--SR:!2026-06-10,0,230-->

Wie ermittelt man die Kardinalitäten bei einer komplexen ternären Beziehung (3 beteiligte Entitytypen)?::Man fixiert gedanklich ein konkretes Paar (zwei Entities) und fragt sich, mit wie vielen Entities des dritten Typs dieses Paar in Beziehung stehen kann. Das wiederholt man für alle drei Kombinationen.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Kardinalität]]
SORT file.mtime DESC
```