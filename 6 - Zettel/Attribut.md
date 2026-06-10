#Note

2026-06-09

Tags: [[Datenbanken]], [[Datenbankentwurf]], [[Entity-Relationship-Modell|ERM]]
#datenbanken 

---
Ein **Attribut** beschreibt die spezifischen Eigenschaften eines Entitytyps im Detail. Während die Entität das Objekt selbst darstellt (z. B. "Kunde"), liefert das Attribut die messbaren Fakten dazu (z. B. "Name", "Preis", "Geburtsdatum").

Jeder konkrete Datenwert ist die Ausprägung eines Attributs für ein spezifisches Tupel.

Arten von Attributen im konzeptionellen ERM (Chen-Notation)

Peter Chens Entity-Relationship-Modell unterscheidet verschiedene Typen von Attributen, um die Komplexität der Realität abzubilden:

| Attribut-Typ                   | Beschreibung                                                                                                                   | Darstellung im ERM                                                |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------- |
| **Einfaches Attribut**         | Eine atomare, nicht weiter unterteilbare Eigenschaft (z. B. _Preis_).                                                          | **Ellipse (Oval)**, die mit dem Entitytyp-Rechteck verbunden ist. |
| **Schlüsselattribut**          | Identifiziert eine [[Entität]] absolut eindeutig (z. B. _Kunden-Nr_). Teil des Identifikationsschlüssels.                      | Oval mit **unterstrichenem** Text.                                |
| **Zusammengesetztes Attribut** | Ein Attribut, das in logische Folgeattribute erweitert bzw. unterteilt werden kann (z. B. _Adresse_ → _PLZ_, _Ort_, _Straße_). | Oval, an dem hierarchisch weitere Ovale hängen.                   |
| **Mehrfachattribut**           | Kann für eine einzelne Entität gleichzeitig mehrere Werte speichern (z. B. _vorher besuchte Schulen_).                         | **Doppelte Ellipse**.                                             |

Attribute im relationalen Datenbankschema

Beim Übergang vom konzeptionellen ERM zum logischen Relationenmodell (Abbildungsregeln) greifen strenge mathematische Regeln:

1. **Spaltenbildung:** Jedes einfache Attribut des Entitytyps wird zu einer Spalte der Tabelle.
2. **Reihenfolge irrelevant:** Die Anordnung der Attributspalten in einer Relation verändert die Relation mathematisch nicht.
3. **Domänenbindung:** Alle Werte innerhalb eines Attributs müssen zwingend denselben Datentyp (die Domäne) besitzen. Das [[Datenbanksystem|DBMS]] verhindert aktiv Verstöße gegen diesen Wertebereich.
4. **Atomarität (1. [[Normalform]]):** Zusammengesetzte Attribute und Mehrfachattribute müssen aufgelöst werden, sodass an jedem Kreuzungspunkt von Zeile und Spalte nur ein atomarer Wert steht.

Code-Implementation (falls relevant)

```sql
-- Definition der Attribute (Columns) und ihrer Domänen (Datatypes) in SQL DDL
CREATE TABLE employee (
    -- Schlüsselattribut (Primary Key)
    employee_id INT PRIMARY KEY,
    
    -- Einfaches Attribut mit strenger Domänenregel (NOT NULL)
    last_name VARCHAR(50) NOT NULL,
    
    -- Aufgelöstes zusammengesetztes Attribut (Adresse -> city, zip_code)
    city VARCHAR(100),
    zip_code VARCHAR(5)
);
```

--------------------------------------------------------------------------------

### Flashcards

Was ist die funktionale Aufgabe eines Attributs im Datenbankentwurf?::Es beschreibt die detaillierten Eigenschaften eines Entitytyps (z. B. "Name", "Preis").

Wie wird ein einfaches Attribut im klassischen ER-Modell nach Chen grafisch dargestellt?::Als einfache Ellipse (Oval), die mit dem Rechteck des Entitytyps verbunden ist.

Was kennzeichnet ein "Schlüsselattribut" und wie wird es im ERM notiert?::Es ist Teil des Identifikationsschlüssels, der ein Entity eindeutig macht, und wird durch eine Unterstreichung des Namens im Oval gekennzeichnet.

Was ist der Unterschied zwischen einem zusammengesetzten Attribut und einem Mehrfachattribut?
?
Ein **zusammengesetztes Attribut** (z.B. Adresse) lässt sich logisch in kleinere Folgeattribute (PLZ, Ort) unterteilen. Ein **Mehrfachattribut** (z.B. vorher besuchte Schulen) speichert für ein einziges Entity mehrere Werte derselben Eigenschaft gleichzeitig.
<!--SR:!2026-06-10,0,230-->

Wie werden konzeptionelle Attribute in das logische Relationenmodell überführt?
?
Sie werden zu den Spalten der Relation (Tabelle). Jedem Attribut wird dabei ein strikter Datentyp (Domäne) zugewiesen, der die zulässigen Werte reglementiert, und die Anordnung der Spalten ist mathematisch irrelevant.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Attribut]]
SORT file.mtime DESC
```