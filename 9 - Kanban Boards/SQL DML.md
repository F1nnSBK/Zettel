#Note

2026-06-09

Tags: [[Relationale Datenbank]], [[Datenbanksystem]], [[Relationenorientierte Operatoren]], [[Join]], [[Datenintegrität]], [[Daten]], [[SQL DDL]]
#datenbanken

---
Die **Data Manipulation Language (DML)** ist die Kategorie von SQL-Befehlen, die dafür zuständig ist, die in den Tabellen gespeicherten Daten zu manipulieren. Während wir mit DDL-Befehlen (`CREATE`, `ALTER`, `DROP`) die "Behälter" gebaut haben, füllen wir diese Behälter nun mit echten Datensätzen.

1. Daten einfügen: INSERT

Mit dem `INSERT`-Befehl werden völlig neue Zeilen (Tupel) in eine Tabelle geschrieben.

**A) Einzelne oder mehrere Zeilen direkt einfügen:** Man gibt explizit an, in welche Spalten geschrieben wird, gefolgt von den konkreten Werten (VALUES).

```
INSERT INTO mitarbeiter (emp_id, emp_email, first_name, last_name)
VALUES (2, 'worker2@comp.de', 'Hugo', 'Boss'),
       (3, 'worker3@comp.de', 'Fred', 'Feuerstein');
```

**B) Daten aus einer anderen Tabelle kopieren (Bulk Insert):** Man kann eine Unterabfrage (`SELECT`) nutzen, um Datenmengen direkt von einer Tabelle in eine andere zu schaufeln. Das funktioniert blind mit `SELECT *` nur dann, wenn Spaltenanzahl und Datentypen beider Tabellen exakt identisch sind.

```
INSERT INTO mitarbeitertemp (emp_id, emp_email, first_name, last_name)
SELECT emp_id, emp_email, first_name, last_name
FROM mitarbeiter;
```

2. Daten ändern: UPDATE

Der `UPDATE`-Befehl modifiziert bereits existierende Datensätze in einer Tabelle.

**Gefahr:** Die `WHERE`-Klausel ist hier das wichtigste Element. Sie filtert exakt die Datensätze, die geändert werden sollen. Man kann bestehende Inhalte auch direkt für Berechnungen oder String-Verkettungen (`||`) heranziehen.

```
-- Erhöht die Gehälter aller Mitarbeiter in Abteilung 5 um 10%
UPDATE mitarbeiter
SET gehalt = gehalt * 1.10
WHERE abteilung_id = 5;

-- Ändert zwei Felder gleichzeitig bei einem spezifischen Mitarbeiter
UPDATE employee
SET last_name = 'Mustermann', first_name = 'Maxi'
WHERE email = 'worker@comp.de' AND last_name = 'Muster';
```

3. Daten löschen: DELETE

Der `DELETE`-Befehl löscht ganze Zeilen (Datensätze) aus der Tabelle.

**Gefahr:** Genau wie beim `UPDATE` entscheidet die `WHERE`-Klausel über Leben und Tod der Daten.

```
DELETE FROM employee
WHERE email = 'worker@comp.de';
```

_Hinweis zur Integrität:_ Wenn auf den zu löschenden Datensatz noch Fremdschlüssel aus einer anderen Tabelle zeigen, greifen nun die [[Datenintegrität]]s-Regeln (wie `ON DELETE CASCADE` oder `RESTRICT`), die das Löschen entweder kaskadierend weitergeben oder strikt blockieren.

--------------------------------------------------------------------------------

### Flashcards

Frage 2: Erklären Sie den Hauptzweck der DDL (Data Definition Language) im Gegensatz zur DML (Data Manipulation Language). Wofür wird jede dieser beiden Sprachkategorien verwendet?
?
Die **DDL** wird verwendet, um die _Struktur_ der Datenbank zu definieren und zu verwalten (Objekte wie Tabellen oder Schemas erstellen, ändern, löschen). Die **DML** wird hingegen genutzt, um die in den Tabellen gespeicherten _Daten_ zu manipulieren (Datensätze einfügen, ändern oder löschen).
<!--SR:!2026-06-11,1,230-->

Frage 10: Was bewirkt die `WHERE`-Klausel in einem `UPDATE`-Befehl? Was würde passieren, wenn Sie diese Klausel in einem `UPDATE`-Befehl weglassen würden?
?
Die `WHERE`-Klausel filtert exakt die Datensätze, die geändert werden sollen. Lässt man die `WHERE`-Klausel weg, wird die `UPDATE`-Anweisung gnadenlos auf **alle Zeilen der gesamten Tabelle** angewendet, was meist zu katastrophalem Datenverlust führt.
<!--SR:!2026-06-11,1,230-->

Wie lautet der SQL-Syntax, um das Ergebnis einer SELECT-Abfrage direkt als neue Datensätze in eine andere Tabelle einzufügen?::`INSERT INTO zieltabelle (spalte1, spalte2) SELECT spalte1, spalte2 FROM quelltabelle;`.

Was ist der fundamentale Unterschied zwischen `DELETE FROM tabelle;` und `DROP TABLE tabelle;`?::`DELETE FROM` ist ein DML-Befehl und löscht "nur" alle Datensätze (die leere Tabellenstruktur bleibt erhalten). `DROP TABLE` ist ein DDL-Befehl und zerstört das gesamte Datenbankobjekt inklusive der Struktur.
<!--SR:!2026-06-11,1,230-->


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[SQL DML]]
SORT file.mtime DESC
```