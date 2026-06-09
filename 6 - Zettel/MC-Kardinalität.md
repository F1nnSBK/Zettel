#Note

2026-06-09

Tags: [[Datenbanken]], [[Datenbankentwurf]], [[Entity-Relationship-Modell]]
#datenbanken 

---
Die **MC-Kardinalität** (Modifizierte Chen-Notation) ist eine Erweiterung des klassischen Entity-Relationship-Modells. Während die klassische (1, m, n)-Notation primär die _Maximalbeziehung_ zwischen Entitäten beschreibt, präzisieren MC-Kardinalitäten dies, indem sie zwingend auch das _Minimum_ festlegen. Sie unterscheiden damit explizit zwischen **Muss-Beziehungen** und **Kann-Beziehungen**.

#### Präzisierung der Standardkardinalität "1"

Im klassischen Modell bedeutet "1" eigentlich "0 oder 1". Die MC-Notation spaltet dies auf in:

- **Typ "1" (Genau eine):** Es handelt sich um eine zwingende Zuordnung (Muss).
    - _Beispiel:_ Ein Mitarbeiter ist _genau einer_ Abteilung unterstellt.
- **Typ "c" (Can / Kann):** Es handelt sich um eine optionale Zuordnung ("keine oder eine").
    - _Beispiel:_ Ein Mitarbeiter kann eine Abteilung leiten, aber _nicht jeder_ Mitarbeiter tut dies.

#### Präzisierung der Standardkardinalität "n"

Im klassischen Modell bedeutet "n" oder "m" immer "0, 1 oder viele". Die MC-Notation spaltet dies auf in:

- **Typ "m" (Must / Muss):** Eine zwingende Zuordnung von "einer oder mehreren" Entitäten.
    - _Beispiel:_ Ein Projekt _muss_ von mindestens einem Mitarbeiter bearbeitet werden.
- **Typ "mc" (Mehrfach-konditionell):** Eine völlig offene Assoziation ("keine, eine oder mehrere").
    - _Beispiel:_ Mitarbeiter _können_ an mehreren Projekten mitwirken, sie müssen es aber nicht.

Code-Implementation (Physische Abbildung in SQL)

Die Unterscheidung zwischen "Muss" (1, m) und "Kann" (c, mc) hat drastische Auswirkungen auf das spätere relationale Datenbankschema. "Muss"-Beziehungen werden in SQL durch `NOT NULL` Constraints auf dem Fremdschlüssel erzwungen.

```sql
-- Beispiel: Typ "1" (Muss) vs. Typ "c" (Kann)
CREATE TABLE mitarbeiter (
    mitarbeiter_id INT PRIMARY KEY,
    
    -- Typ "1": Jeder MA MUSS einer Abteilung zugeordnet sein.
    -- Das NOT NULL Constraint erzwingt diese Minimal-Kardinalität.
    abteilung_id INT NOT NULL REFERENCES abteilung(id),
    
    -- Typ "c": Ein MA KANN einen Dienstwagen haben, MUSS aber nicht.
    -- Das Feld erlaubt NULL-Werte.
    dienstwagen_id INT REFERENCES dienstwagen(id)
);
```

--------------------------------------------------------------------------------

Flashcards

Welche fundamentale Schwäche der klassischen Chen-Notation löst die MC-Kardinalität?::Die klassische Notation definiert primär die Maximalbeziehung. Die MC-Kardinalität präzisiert dies, indem sie zusätzlich das Minimum (Muss- vs. Kann-Beziehung) explizit definiert.

In welche zwei Typen unterteilt die MC-Notation die klassische Standardkardinalität "1"?
?
In den Typ **"1"** (genau eine Entität / Muss-Beziehung) und den Typ **"c"** (Can / keine oder eine Entität / Kann-Beziehung).

In welche zwei Typen unterteilt die MC-Notation die klassische Standardkardinalität "n"?
?
In den Typ **"m"** (Must / eine oder mehrere Entitäten / Muss-Beziehung) und den Typ **"mc"** (Mehrfach-konditionelle Assoziation / keine, eine oder mehrere Entitäten / Kann-Beziehung).

Wie wird eine Muss-Beziehung (Typ "1" oder "m") bei der Überführung in ein relationales Datenbankschema physisch erzwungen?::Durch die Definition eines `NOT NULL` Constraints auf dem entsprechenden Fremdschlüssel, was die Eingabe eines fehlenden Wertes (`NULL`) auf Datenbankebene blockiert.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[MC-Kardinalität]]
SORT file.mtime DESC
```