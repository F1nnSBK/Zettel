#Note

2026-06-09

Tags: [[Datenbanken]], [[Datenbankentwurf]], [[Modellierung]]
#datenbanken 

---
Eine **Entität (Entity)** ist ein eindeutig identifizierbares, abgrenzbares und zu beschreibendes Objekt der Realwelt (Miniwelt), über das in einer Datenbank Informationen gesammelt werden sollen. Dies können sowohl physisch reale Objekte (z. B. ein bestimmtes Auto, eine konkrete Person) als auch abstrakte Konzepte (z. B. ein Auftrag, ein Event) sein.

#### Abgrenzung: Entity vs. Entitytyp

In der Datenbankmodellierung ist die strikte konzeptionelle Trennung zwischen der konkreten Einzelinstanz und ihrer abstrakten Schablone essenziell:

|Begriff|Definition|Beispiel aus Skript|Relationales Äquivalent|
|---|---|---|---|
|**Entity (Entität)**|Eine konkrete, einzelne Ausprägung (Instanz) eines Objekts der Miniwelt.|"LSG Sky Chefs", "Cola Dose 0,33l", "Max Mustermann"|Ein **Tupel** (eine einzelne Zeile / ein Datensatz) in einer Tabelle.|
|**Entitytyp**|Die abstrakte Zusammenfassung (Klasse) gleichartiger Entities in strukturierter Form.|"Lieferant", "Artikel", "Kunde"|Eine **Relation** (die Struktur/Tabelle selbst).|

#### Grafische Darstellung im ERM

Im klassischen Entity-Relationship-Modell nach Peter Chen werden **Entitytypen** stets als **Rechtecke** dargestellt. Die konkreten Ausprägungen (die tatsächlichen Entities) selbst werden im konzeptionellen ER-Diagramm normalerweise nicht gezeichnet, da das Modell primär dazu dient, die Struktur (das Schema) und die [[Assoziation|Beziehungen]] der Datenbasis zu definieren, nicht jedoch deren spezifischen Tupel-Inhalt.

#### Transformation ins Relationenmodell

Nach den gängigen Abbildungsregeln des logischen Datenbankentwurfs bildet jeder Entitytyp das Fundament für die spätere physische Datenbankarchitektur:

1. **Tabelle:** Jeder Entitytyp wird in eine eigene Tabelle (Relation) überführt.
2. **Spalten:** Die Eigenschaften (Attribute) des Entitytyps werden zu den Spalten der Tabelle.
3. **Datensätze:** Jede physisch gespeicherte Entität bildet exakt einen eindeutigen Datensatz (Zeile) in dieser Tabelle ab.

Code-Implementation

```sql
-- DDL-Repräsentation: Erstellung der Tabellenstruktur für den Entitytyp "Lieferant"
CREATE TABLE lieferant (
    lief_nr INT PRIMARY KEY,       -- Identifiziert jede Entität (Instanz) absolut eindeutig
    name VARCHAR(100) NOT NULL,    -- Attribut des Entitytyps
    anschrift VARCHAR(200)         -- Attribut des Entitytyps
);

-- DML-Repräsentation: Einfügen einer konkreten Entität (Entity)
INSERT INTO lieferant (lief_nr, name, anschrift) 
VALUES (1, 'LSG Sky Chefs', 'MUC'); -- Dies ist das physische Entity (das Tupel), repräsentiert durch konkrete Attributwerte.
```

--------------------------------------------------------------------------------

### Flashcards

Was ist der funktionale Unterschied zwischen einer Entität (Entity) und einem Entitytyp?::Eine Entität ist das konkrete, abgrenzbare Einzelobjekt (z. B. "LSG Sky Chefs"). Ein Entitytyp ist die abstrakte Zusammenfassung gleichartiger Entitäten (z. B. "Lieferant").

Wie wird ein Entitytyp im Entity-Relationship-Modell (Chen-Notation) grafisch dargestellt?::Als Rechteck.

Worin resultiert ein Entitytyp nach der logischen Überführung (Abbildungsregeln) in ein relationales Datenbankmodell?::Ein Entitytyp wird exakt zu einer eigenen Relation (Tabelle).

Worin resultiert eine konkrete Entität (Entity) in einem relationalen Datenbankmodell?::Sie repräsentiert genau ein Tupel (einen Datensatz bzw. eine Zeile) innerhalb einer Tabelle.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Entität]]
SORT file.mtime DESC
```