#Note

2026-06-09

Tags: [[SQL DDL]], [[Datenbanksystem]], [[Datenbankentwurf]], [[Relationale Datenbank]], [[Relationenmodell]], [[Abbildungsregeln]], [[Datenintegrität]], [[Attribut]], [[Entität]]
#datenbanken 

---
Die **Data Definition Language (DDL)** ist die Kategorie von SQL-Befehlen, mit der die Struktur einer relationalen Datenbank verwaltet wird. Während die DML (Data Manipulation Language) später die einzelnen Zeilen (Tupel) ändert, arbeitet die DDL ausschließlich auf der Meta-Ebene der Objekte (Schemas, Tabellen, Views).

#### Die 3 Hauptbefehle der DDL

Jedes Objekt in einer Datenbank wird über exakt drei Verben gesteuert:

1. **CREATE (Erschaffen):** Legt neue Datenbankobjekte an.
    - `CREATE SCHEMA my_schema;` (Erstellt einen isolierten Bereich)
    - `CREATE TABLE my_table (...);` (Erstellt die Tabelle mit all ihren Spalten)
2. **ALTER (Ändern):** Passt die Struktur eines existierenden Objekts an.
    - `ALTER TABLE my_table ADD COLUMN age INT;` (Fügt eine Spalte hinzu)
    - `ALTER TABLE my_table DROP COLUMN age;` (Löscht eine Spalte)
3. **DROP (Löschen):** Zerstört das Objekt (und den kompletten Inhalt!) endgültig.
    - `DROP TABLE my_table CASCADE;` (Zerstört die Tabelle und ignoriert/löscht dabei auch abhängige Fremdschlüsselverweise, wenn `CASCADE` verwendet wird).

Datentypen: Das Fundament der Spalten

Beim Erstellen einer Tabelle muss für jede Spalte zwingend die Domäne (der Datentyp) festgelegt werden. Hier passieren oft Designfehler:

- **Alphanumerisch (Text):**
    - `CHAR(n)` speichert Texte mit fester Länge. Ein 5-Buchstaben-Wort in einem `CHAR(20)`-Feld wird gnadenlos mit 15 Leerzeichen aufgefüllt, was Speicherplatz verschwendet.
    - `VARCHAR(n)` speichert Zeichenketten mit variabler Länge (bis zum Maximum `n`). Dies ist die effizientere und heute bevorzugte Wahl für Texte unterschiedlicher Länge wie Namen oder Adressen.
- **Numerisch:** `INT` (Ganzzahlen), `FLOAT` (Gleitkomma), `DECIMAL`/`NUMERIC` (Fixkomma für Geldwerte).
- **Spezielle:** `BOOLEAN` (True/False).

Code-Implementation: Eine Tabelle bauen (CREATE TABLE)

In diesem Befehl fließen die Struktur und die [[Datenintegrität]] (Constraints) zusammen.

```sql
-- DDL-Befehl zum Erstellen einer Tabelle
CREATE TABLE account(
    -- 1. Spaltenname | 2. Datentyp | 3. Constraints
    customer_id INTEGER NOT NULL,          -- Darf nicht leer sein
    account_holder VARCHAR(30) NOT NULL,   -- Variable Länge, max 30 Zeichen
    
    -- Definition der Primär- und Fremdschlüssel
    PRIMARY KEY (customer_id),
    FOREIGN KEY (customer_id) REFERENCES customer(customer_id) 
        ON DELETE CASCADE                  -- Referentielle Integrität (Löschweitergabe)
);
```

--------------------------------------------------------------------------------

### Flashcards

Was ist der funktionale Unterschied zwischen der DDL (Data Definition Language) und der DML (Data Manipulation Language)?::Die DDL wird verwendet, um die _Struktur_ der Datenbankobjekte (z.B. Tabellen, Schemas) zu definieren, zu ändern oder zu löschen. Die DML dient hingegen dazu, die konkreten Datensätze innerhalb dieser Tabellen zu verwalten (einfügen, ändern, löschen).

Welche drei zentralen SQL-Befehle bilden die DDL?::`CREATE` (Anlegen), `ALTER` (Struktur ändern), `DROP` (Endgültig löschen).
<!--SR:!2026-06-11,1,230-->

Was ist der technische Unterschied zwischen den SQL-Datentypen `CHAR(n)` und `VARCHAR(n)`?
?
`CHAR(n)` speichert eine feste Länge und füllt überschüssigen Platz mit Leerzeichen auf (Speicherverschwendung bei kurzen Wörtern). `VARCHAR(n)` speichert eine variable Länge bis zum definierten Maximum `n` und belegt nur den tatsächlich benötigten Speicherplatz.

Wie lautet der SQL DDL-Befehl, um aus der bestehenden Tabelle `employee` die Spalte `first_name` zu löschen?::`ALTER TABLE employee DROP COLUMN first_name;`.

Wann nutzt man `DROP TABLE` im Gegensatz zu `DELETE FROM`?::`DROP TABLE` (ein DDL-Befehl) zerstört das gesamte Datenbankobjekt inklusive aller Metadaten und der Struktur. `DELETE FROM` (ein DML-Befehl) leert nur die Datensätze, aber die leere Tabelle als Struktur bleibt erhalten.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[SQL DDL]]
SORT file.mtime DESC
```