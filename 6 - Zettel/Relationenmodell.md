#Note

2026-06-09

Tags: [[Datenbanken]], [[Grundlagen]], [[Relationenmodell]]
#datenbanken 

---
Das **Relationenmodell** ist das theoretische Fundament für strukturierte relationale Datenbanken. Es wurde im Jahr 1970 von **Edgar Frank Codd** in seiner bahnbrechenden Arbeit "A Relational Model of Data for Large Shared Data Banks" vorgestellt. Es löste historische hierarchische und netzwerkartige Datenbankkonzepte ab und bildet seit den 1980er Jahren den industriellen De-facto-Standard.

Das Modell basiert strikt auf der mathematischen Mengentheorie. Sämtliche Daten und auch die Beziehungen zwischen den Daten werden einheitlich und ausschließlich in Form von Tabellen ausgedrückt.

#### Mathematische Definition

Im logischen Datenbankentwurf wird die Realwelt in formale Datenstrukturen übersetzt:

- **Relation:** Eine Relation R ist formal eine Teilmenge aus dem kartesischen Produkt von vorgegebenen Wertebereichen (Domänen) aus allen i Attributen (i=1,…,n): R⊆D1​×⋯×Dn​ mit n Spalten.
- **Tupel:** Ein einzelnes Tupel r (eine Zeile) ist eine konkrete Ausprägung aus diesen Domänen: r=(d1​,…,dn​).
- **Menge:** Die Relation R selbst ist die exakte Tupelmenge: R={r1​,…,rm​} mit m Zeilen.

#### Die formale Terminologie

Um die mathematischen Operationen der Datenbank zu verstehen, müssen die alltagssprachlichen Tabellen-Begriffe zwingend in das Relationenmodell übersetzt werden:

|Formale relationale Bezeichnung|Informelle Bezeichnung (Alltag)|
|---|---|
|**Relation**|Tabelle (bestehend aus Kopf und Rumpf)|
|**Tupel**|Eine einzelne Zeile (Reihe / Datensatz) einer Tabelle|
|**Attribut**|Eine Spalte (Feld) einer Tabelle|
|**Kardinalität** _(einer Relation)_|Die Anzahl der Zeilen (Tupel) einer Tabelle|
|**Grad**|Die Anzahl der Spalten (Attribute) einer Tabelle|
|**Gebiet (Domäne)**|Die Menge aller möglichen Werte / der Datentyp (z. B. Integer)|

#### Die 4 zwingenden Eigenschaften einer Relation

Damit eine Tabelle mathematisch als echte Relation gilt und das Datenbankmanagementsystem (DBMS) fehlerfrei darauf operieren kann, muss sie zwingend vier Eigenschaften aufweisen:

1. **Keine doppelten Tupel:** Es gibt keine zwei Tupel, die völlig identisch sind; sie sind paarweise verschieden. Dies wird durch den zwingenden Primärschlüssel garantiert, der jedes Tupel eindeutig identifiziert.
2. **Ungeordnete Tupel:** Die Reihenfolge der Zeilen ist mathematisch völlig irrelevant; sie unterliegen innerhalb der Relation keiner inhärenten Ordnung.
3. **Ungeordnete Attribute:** Die Reihenfolge der Spalten ist ebenso irrelevant; das Tauschen von Spaltenanordnungen verändert die Relation nicht.
4. **Atomare Attribute:** Jeder Datenwert (der Kreuzungspunkt von Spalte und Zeile) darf nur einen einzigen, nicht weiter unterteilbaren Wert (atomare Eigenschaft) aus der zugrundeliegenden Domäne enthalten. Dies ist gleichzeitig die Bedingung für die 1. Normalform.

--------------------------------------------------------------------------------

### Flashcards

Wie lautet die strenge mathematische Definition einer Relation?::Eine Relation ist eine Teilmenge aus dem kartesischen Produkt von definierten Wertebereichen (Domänen): R⊆D1​×⋯×Dn​.
<!--SR:!2026-06-10,0,230-->

Was beschreiben der "Grad" und die "Kardinalität" in Bezug auf eine relationale Tabelle?
?
Der **Grad** ist die Anzahl der Spalten (Attribute) der Relation. Die **Kardinalität** (in diesem spezifischen Kontext) ist die Anzahl der Zeilen (Tupel) in der Relation.

Welche 4 mathematischen Grundeigenschaften MUSS eine Tabelle zwingend erfüllen, um formal als korrekte Relation zu gelten?
?
1. Es existieren keine doppelten Tupel (jede Zeile ist durch den Primärschlüssel eindeutig).
2. Die Tupel sind ungeordnet.
3. Die Attribute sind ungeordnet.
4. Alle Attribute sind zwingend atomar (beinhalten keine zusammengesetzten Wertegruppen).


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Relationenmodell]]
SORT file.mtime DESC
```