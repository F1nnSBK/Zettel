#Note

2026-06-09

Tags: [[Datenbanken]], [[Datenbankentwurf]], [[Entity-Relationship-Modell]]
#datenbanken

---
Ein **Beziehungstyp (Relationship-Typ)** fasst gleichartige Beziehungen zwischen Entities im Rahmen der Abstraktion zusammen. Während die _Relationship_ die konkrete logische Verknüpfung zwischen echten, spezifischen Entities ist (z. B. "Lieferant LSG liefert Artikel Cola"), ist der _Relationshiptyp_ die abstrakte Schablone dafür ("Lieferant liefert Artikel").

#### Darstellung und Eigenschaften im ERM

- **Notation:** Im Chen-ERM werden Beziehungstypen stets als **Raute (Diamant)** gezeichnet, die über Kanten mit den beteiligten Entitytypen verbunden ist.
- **Richtungsdualität:** Ein Beziehungstyp funktioniert logisch immer in beide Richtungen und muss bei der Modellierung in zwei gerichtete "Teilbeziehungen" zerlegt und hinterfragt werden (z. B. "Ein Lieferant liefert Artikel" ↔ "Ein Artikel wird von Lieferanten geliefert").
- **Beziehungsattribute:** Genau wie Entitytypen können auch Beziehungstypen eigene Attribute besitzen, die nur im Kontext der Verknüpfung Sinn ergeben (z. B. die _Liefermenge_ bei der Beziehung "liefert").

#### Spezielle Beziehungsformen

Neben der klassischen binären Beziehung (2 Entitytypen) gibt es komplexere Ausprägungen:

1. **Rekursive Beziehungen:** Eine Beziehung zwischen Entities, die _demselben_ Entitytyp angehören (z. B. Mitarbeiter "ist Vorgesetzter von" Mitarbeiter).
2. **Parallele Beziehungen:** Zwischen denselben zwei Entitytypen existieren gleichzeitig mehrere, völlig unterschiedliche Beziehungen (z. B. Mitarbeiter "leitet" Projekt vs. Mitarbeiter "arbeitet an" Projekt).
3. **Ternäre Beziehungen:** Ein Relationshiptyp, an dem exakt drei Entitytypen gleichzeitig beteiligt sind (z. B. Pilot, Flugzeug, Flugroute). Eine Aufspaltung in binäre Beziehungen würde hier zum Informationsverlust führen (sog. **Connection Trap**).

#### Paradigmenwechsel: Relational vs. Graph

Die physische Behandlung von Beziehungen ist der gravierendste Architekturunterschied zwischen klassischen SQL-Systemen und modernen Graphdatenbanken (wie Neo4j):

- **Relationales Modell:** Beziehungen werden durch starre Fremdschlüssel abgebildet und müssen zur Laufzeit aufwändig berechnet werden (JOINs).
- **Graphdatenbanken:** Beziehungen (Kanten) sind "**First-Class Citizens**". Sie werden physisch direkt als Pointer abgespeichert, was tiefe, netzwerkartige Abfragen (Traversierung) massiv beschleunigt.

Code-Implementation

Beim Übergang ins logische Relationenmodell (Abbildungsregeln) hängt das Schicksal der Beziehung von ihrer [[Kardinalität]] ab. Bei einer n:m-Beziehung wird der Beziehungstyp zwingend in eine eigene Verbindungstabelle umgewandelt.

```sql
-- Die Umsetzung eines n:m Beziehungstyps "liefert" in SQL
-- Die Beziehung wird zu einer physischen Tabelle, die die Primärschlüssel beider Entitytypen vereint
CREATE TABLE liefert (
    lief_nr INT,            -- Fremdschlüssel auf Entitytyp Lieferant
    artikel_nr INT,         -- Fremdschlüssel auf Entitytyp Artikel
    liefermenge INT,        -- Attribut des Beziehungstyps!
    
    -- Der zusammengesetzte Primärschlüssel der neuen Assoziationstabelle
    PRIMARY KEY (lief_nr, artikel_nr),
    FOREIGN KEY (lief_nr) REFERENCES lieferant(lief_nr),
    FOREIGN KEY (artikel_nr) REFERENCES artikel(artikel_nr)
);
```

--------------------------------------------------------------------------------

Flashcards

Wie wird ein Beziehungstyp im ER-Modell (Chen-Notation) grafisch dargestellt?::Als Raute (Diamant) zwischen den beteiligten Entitytypen.

Können Beziehungstypen eigene Attribute haben? Nenne ein Beispiel.
?
Ja, Beziehungen können Attribute besitzen, die nur im Kontext der Verknüpfung Sinn ergeben. Beispiel: Das Attribut "Liefermenge" oder "Bestelldatum" an der Beziehung "liefert" zwischen Lieferant und Artikel.

Was ist eine rekursive Beziehung?::Eine Beziehung zwischen Entities, die demselben Entitytyp angehören (z. B. ein Mitarbeiter ist der Vorgesetzte eines anderen Mitarbeiters).

Was versteht man unter der "Connection Trap" im Datenbankentwurf?
?
Der Semantik- und Informationsverlust, der entsteht, wenn man eine komplexe ternäre Beziehung (3 beteiligte Entitytypen, z. B. Pilot, Flugzeug, Route) fälschlicherweise in mehrere binäre Beziehungen zerlegt.

Wie unterscheidet sich die physische Speicherung von Beziehungen in Relationalen Datenbanken vs. Graphdatenbanken?
?
In relationalen DBs werden Beziehungen über starre Fremdschlüssel constraints modelliert und zur Laufzeit durch JOINs berechnet. In Graphdatenbanken (wie Neo4j) sind sie "First-Class Citizens" und werden als direkte, physische Pointer gespeichert.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Beziehungstyp]]
SORT file.mtime DESC
```