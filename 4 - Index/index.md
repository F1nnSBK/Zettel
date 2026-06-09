#Note

2026-06-09

Tags: [[Datenbanksystem]], [[Relationale Datenbank]], [[SQL DDL]], [[Datenbankentwurf]], [[Attribut]], [[Performance]]
#datenbanken 

---
Ein **INDEX** ist eine physische Datenstruktur, die die Geschwindigkeit von Datenabfragen (Lese-Performance) drastisch optimiert. Ohne Index muss die Datenbank bei einer Suche (z. B. `WHERE last_name = 'Müller'`) jede einzelne Zeile überprüfen. Mit einem Index springt sie direkt an die richtige Stelle.

Indizierung ist eines der wichtigsten Themen für ein performanceorientiertes Datenbankdesign und oft der entscheidende Faktor für die Akzeptanz eines Systems durch die Endanwender.

Der Preis der Geschwindigkeit (Der Trade-off)

Indizes sind nicht kostenlos. Während sie die Lese-Geschwindigkeit extrem erhöhen, **verschlechtern sie zwingend die Schreib-Performance**. Jedes Mal, wenn ein Datensatz eingefügt (`INSERT`), geändert (`UPDATE`) oder gelöscht (`DELETE`) wird, muss das DBMS zusätzlich zur Tabelle auch die Index-Struktur neu berechnen und aktualisieren (Overhead).

Syntax und Arten von Indizes

**1. Der Standard-Index** Beschleunigt das Suchen, erlaubt aber weiterhin doppelte Werte in der Spalte.

```sql
-- Erzeugt einen Index für schnelle Ländersuchen
CREATE INDEX idx_country ON invoice(billing_country); [2]

-- Index wieder löschen
DROP INDEX idx_country; [4, 5]
```

**2. Der Unique-Index (Eindeutiger Index)** Er beschleunigt nicht nur die Suche, sondern erzwingt auch auf Datenbankebene, dass kein Wert in dieser Spalte doppelt vorkommen darf. Da ein `PRIMARY KEY` in SQL ohnehin immer indiziert ist, verhält sich ein `UNIQUE INDEX` funktional exakt wie ein Primärschlüssel.

```sql
-- Erzeugt einen eindeutigen Index (wirft Fehler, wenn ein Nachname schon existiert!)
CREATE UNIQUE INDEX i_last_name ON customer(last_name); [4, 5]
```

Wie findet man heraus, wo ein Index fehlt?

Um zu überprüfen, ob die Datenbank bei einer Abfrage einen vorhandenen Index nutzt oder mühsam die ganze Tabelle scannt, stellt man dem SELECT-Befehl das Wort **EXPLAIN** voran. Dieser Befehl führt die Abfrage nicht aus, sondern gibt den internen Ausführungsplan des Optimizers aus, was erste Hinweise für sinnvolle Indizes liefert.

--------------------------------------------------------------------------------

### Flashcards

Warum sollte man nicht einfach wahllos für jede Spalte einer Tabelle einen INDEX erstellen?::Weil Indizes zwar die Lese-Performance (SELECT) verbessern, aber gleichzeitig die Schreib-Performance verschlechtern. Bei jedem INSERT, UPDATE oder DELETE entsteht ein zusätzlicher Overhead, da der Index stets mitgepflegt werden muss.

Wie kann man mit einem Index auf einer Spalte ein Verhalten erzwingen, das exakt dem eines PRIMARY KEY entspricht?::Durch das Erstellen eines `UNIQUE INDEX` (`CREATE UNIQUE INDEX ...`). Da dieser Index nicht nur die Suche beschleunigt, sondern auch zwingend Eindeutigkeit fordert, verhält er sich wie ein Primärschlüssel.

Welcher SQL-Befehl hilft bei der Analyse, um herauszufinden, ob eine Abfrage effizient läuft oder ob das Anlegen eines neuen Index sinnvoll wäre?::Der Befehl `EXPLAIN` (gefolgt von der eigentlichen Abfrage). Er gibt den Ausführungsplan der Datenbank aus.

Was passiert, wenn man versucht, einen `UNIQUE INDEX` auf eine Spalte wie `last_name` (Nachname) zu legen, in der es bereits "Müller" und "Schmidt" mehrfach gibt?::Der Befehl wirft einen Fehler und schlägt fehl. Ein Unique-Index kann nur erstellt werden, wenn alle bisherigen Werte in der Spalte absolut eindeutig sind.

Wird für den Primärschlüssel (`PRIMARY KEY`) einer Tabelle automatisch ein Index angelegt, oder muss dieser vom Entwickler manuell erstellt werden?::Ein `PRIMARY KEY` ist immer automatisch indiziert.




---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Index]]
SORT file.mtime DESC
```