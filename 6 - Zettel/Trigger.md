#Note

2026-06-12

Tags: [[Datenbanken]], [[SQL]], [[Programmierung]], [[Trigger]]
#datenbanken

---
Ein **TRIGGER** ist eine serverseitige Prozedur, die automatisch aufgerufen wird, wenn ein festgelegtes Ereignis (INSERT, UPDATE, DELETE) auf einer Tabelle stattfindet. Sie besitzen keine Übergabeparameter und können direkt auf die betroffenen Zeilen zugreifen.

Die Architektur in PostgreSQL (2-Teiler)

Im Gegensatz zu anderen Datenbanksystemen darf ein Trigger in PostgreSQL keinen direkten Programmcode enthalten. Er muss immer strikt in zwei Datenbankobjekte aufgeteilt werden:

**1. Die Trigger-Funktion (Die Logik)** Muss als Funktion mit der Sprache `PL/pgSQL` und dem zwingenden Rückgabetyp `RETURNS TRIGGER` erstellt werden. Die Parameterliste ist immer leer `()`.

- _Magische Variablen:_ Die Funktion erhält ihre Daten implizit. Bei einem UPDATE hat man beispielsweise über `OLD.*` Zugriff auf die Zeile _vor_ der Änderung und über `NEW.*` Zugriff auf die Zeile _nach_ der Änderung.

**2. Der Trigger (Das Ereignis)** Verbindet die Tabelle mit der Trigger-Funktion. Hier konfiguriert man das Timing und die Granularität:

- **Zeitpunkt:** `BEFORE` (vor der Datenbankänderung, kann noch blockieren/verändern) oder `AFTER` (nach der Datenbankänderung).
- **Ereignis:** `INSERT`, `UPDATE`, `DELETE`.
- **Granularität:** `FOR EACH ROW` (feuert z.B. 100-mal, wenn 100 Zeilen geändert werden) oder `FOR EACH STATEMENT` (feuert genau 1-mal für den gesamten SQL-Befehl).

**Code-Beispiel: Validierung (aus den Übungsaufgaben)** Wir verhindern, dass beim Update das neue Einstellungsdatum vor dem alten liegt.

```sql
-- Schritt 1: Die Funktion (Logik)
CREATE OR REPLACE FUNCTION check_hire_date() RETURNS TRIGGER 
LANGUAGE plpgsql AS $$ 
BEGIN     
    -- Prüfen über die magischen NEW und OLD Variablen
    IF NEW.hire_date < OLD.hire_date THEN         
        RAISE EXCEPTION 'Das Einstellungsdatum kann nicht zurückdatiert werden.';     
    END IF;     
    -- Zwingend erforderlich bei BEFORE-Triggern: Die Zeile durchreichen
    RETURN NEW; 
END; $$;  

-- Schritt 2: Den Trigger binden
CREATE TRIGGER check_date_forward 
BEFORE UPDATE OF hire_date ON employee 
FOR EACH ROW 
EXECUTE FUNCTION check_hire_date();
```

_(Quelle: Übungsblatt 5)_

Wichtige Einschränkungen

- **Kein SELECT:** Trigger-Funktionen dürfen keine Kommandos wie ein normales `SELECT` ausführen, die ein sichtbares Abfrageergebnis zum Client zurückliefern.
- **Keine Transaktionen:** Befehle wie `COMMIT` oder `ROLLBACK` sind streng verboten, da der Trigger ein untrennbarer Teil der aufrufenden DML-Operation ist.
- **Keine Mutationen auf die eigene Tabelle:** Man darf in der Funktion keine expliziten SQL-DML Befehle (wie `UPDATE eigene_tabelle`) abfeuern, da dies Endlosschleifen auslösen würde. (Ausnahme: Zuweisungen wie `NEW.feld = 'Wert'` in BEFORE-Triggern sind erlaubt).

---

### Flashcards

Was versteht man unter einem „Hook“ im Zusammenhang mit Datenbank-Triggern?::Ein Trigger dient als „Haken“, um eigenen Code automatisch in die normale Abarbeitung von Ereignissen (INSERT, UPDATE, DELETE) durch das DBMS einzufügen.

Warum benötigt man in PostgreSQL zusätzlich zum `CREATE TRIGGER`-Befehl eine separate „Trigger Function“?::Der `CREATE TRIGGER`-Befehl dient in PostgreSQL nur dazu, das Ereignis an eine Tabelle zu binden. Die eigentliche Logik darf nicht im Trigger stehen, sondern muss in einer Funktion mit dem Rückgabetyp `RETURNS TRIGGER` gekapselt sein.

Erklären Sie den funktionalen Unterschied zwischen einem BEFORE- und einem AFTER-Trigger.::BEFORE-Trigger laufen vor der Operation ab und können diese noch modifizieren (z.B. Daten verändern) oder stoppen (z.B. durch eine Exception). AFTER-Trigger laufen erst nach der erfolgreichen Durchführung der Operation ab.

Was repräsentieren die Variablen `OLD` und `NEW` innerhalb einer Trigger-Funktion bei einer UPDATE-Operation?::`OLD` enthält den Zustand des Datensatzes vor der Änderung, `NEW` enthält den Zustand nach der Änderung.

Warum dürfen in Trigger-Funktionen keine Transaktionsbefehle wie COMMIT oder ROLLBACK ausgeführt werden?::Da Trigger als "Hook" Teil der aufrufenden DML-Operation sind, dürfen sie die Transaktionskontrolle nicht eigenständig beeinflussen. Sie laufen zwingend in derselben Transaktion ab wie der Befehl, der sie ausgelöst hat.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Trigger]]
SORT file.mtime DESC
```