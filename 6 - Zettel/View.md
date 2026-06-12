#Note

2026-06-09

Tags: [[Relationale Datenbank]], [[Datenbanksystem]], [[SQL DDL]], [[SQL DQL]], [[Datenintegrität]], [[Abbildungsregeln]]
#datenbanken 

---
Eine **VIEW (Sicht oder Pseudotabelle)** ist ein benanntes, dauerhaft gespeichertes Datenbankobjekt, das nach außen (gegenüber Programmen und Usern) exakt wie eine echte Tabelle auftritt. Sie speichert jedoch keine eigenen Datensätze, sondern präsentiert lediglich die dynamische Ergebnismenge einer festgelegten SELECT-Abfrage.

Die 3 Hauptzwecke von VIEWs

1. **Datenunabhängigkeit (Abstraktion):** Wenn Programme nur über VIEWs auf Daten zugreifen, bleibt die Schnittstelle stabil. Die physische Tabelle hinter der Sicht kann beliebig umgebaut werden (z. B. Hinzufügen neuer Spalten), ohne dass der Applikationscode abbricht.
2. **Kapselung von Geschäftsregeln:** Komplexe Berechnungen (z. B. `SUM(unit_price * quantity) AS Gesamtumsatz`) oder tiefe JOIN-Ketten werden einmalig in der View definiert und können dann von Endanwendern ganz simpel mit `SELECT * FROM gesamtumsatz_view` konsumiert werden.
3. **Sicherheit und Rechteverwaltung:** Man entzieht einem Nutzer die Leserechte auf die komplette Tabelle `mitarbeiter` und gibt ihm stattdessen nur Leserechte auf eine View, die kritische Spalten (wie Gehälter) durch Projektion oder sensible Zeilen (wie Fremdabteilungen) durch Selektion ausblendet.

Syntax und Erstellung

Eine View wird als DDL-Befehl erstellt und existiert fortan im Datenbankschema:

```sql
-- Erzeugen einer View mit Umbenennung der Spalten
CREATE VIEW Mitarbeiter_namen (Nummer, VNAME, NNAME) AS 
SELECT id, vornamen, nachname 
FROM mitarbeiter;

-- Löschen einer View
DROP VIEW Mitarbeiter_namen;
```

Begriffliche Abgrenzung: VIEW vs. Inline View

- **Persistente VIEW:** Mit `CREATE VIEW` dauerhaft im Schema gespeichert. Wiederverwendbare Abstraktionsschicht.
- **Inline View:** Eine temporäre, nur einmalig verwendete SELECT-Anweisung, die direkt im `FROM`-Abschnitt einer Hauptabfrage in Klammern geschrieben (und mit einem Alias versehen) wird.

Datenmanipulation (DML) über eine VIEW

Obwohl Views primär zum Lesen da sind, _können_ durch sie hindurch auch Datensätze in der echten Tabelle eingefügt, aktualisiert oder gelöscht werden (`UPDATE/INSERT/DELETE`). Das DBMS erlaubt dies aber **nur**, wenn sich die Änderung eindeutig auf einen physischen Datensatz zurückrechnen lässt. Folgende Bedingungen müssen _zwingend_ für eine änderbare (updatable) View erfüllt sein:

1. Die `FROM`-Klausel enthält **nur genau eine Relation** (keine JOINs).
2. Es gibt **keine** **GROUP BY**-Klausel.
3. Die `SELECT`-Klausel enthält **keine** **DISTINCT**-Angabe.
4. Es werden **keine Berechnungen, Konstanten oder Aggregationen** (SUM, COUNT) ausgegeben.
5. Operatoren wie `UNION`, `INTERSECT` oder `EXCEPT` kommen nicht vor.

---

### Flashcards

Was versteht man unter dem Datenbankkonzept einer VIEW und wie verhält sie sich gegenüber anfragenden Programmen?::Eine VIEW ist eine "Pseudotabelle" (gespeicherte SELECT-Abfrage), die nur dynamisch die Ergebnismenge repräsentiert. Nach außen hin präsentiert sie sich gegenüber Programmen oder Nutzern jedoch exakt wie eine echte, physische Tabelle.

Welchen spezifischen Vorteil der "Datenunabhängigkeit" bieten VIEWs, wenn sich die zugrundeliegende Tabellenstruktur (z. B. durch neue Attribute) ändert?::Sie bilden eine stabile Abstraktionsschicht. Die anfragenden Programme müssen nicht angepasst werden, da die VIEW die Änderungen der physischen Struktur maskiert und nach außen hin das gewohnte Interface beibehält.

Worin besteht der genaue architektonische Unterschied zwischen einer persistenten VIEW und einer Inline View?::Eine **persistente VIEW** ist ein benanntes Datenbankobjekt, das mit `CREATE VIEW` dauerhaft im Schema gespeichert und wiederverwendet wird. Eine **Inline View** ist eine temporäre SELECT-Anweisung, die direkt im `FROM`-Abschnitt einer Hauptabfrage definiert wird und nach deren Ausführung verfällt.
<!--SR:!2026-06-10,0,230-->

Nenne drei zwingende Bedingungen, die erfüllt sein müssen, damit über eine VIEW Daten in der Basistabelle eingefügt oder geändert werden dürfen (Updatable View).
?
1. Die FROM-Klausel darf nur genau eine Relation (Tabelle) enthalten (keine JOINs).
2. Es darf keine `GROUP BY`-Klausel existieren.
3. Die Abfrage darf kein `DISTINCT`, keine Aggregationen und keine berechneten Felder enthalten.
<!--SR:!2026-06-10,0,230-->

Warum sind VIEWs ein extrem mächtiges Sicherheitsinstrument in relationalen Datenbanken?::Man kann Benutzern den direkten Zugriff auf eine Basistabelle komplett verweigern und ihnen stattdessen nur Zugriff auf eine VIEW gewähren, die sensible Spalten (wie das Gehalt) oder fremde Datensätze (wie Mitarbeiter aus anderen Abteilungen) herausfiltert.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[View]]
SORT file.mtime DESC
```