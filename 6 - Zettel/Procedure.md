#Note

2026-06-09

Tags: [[Datenbanksystem]], [[Relationale Datenbank]], [[SQL DDL]], [[Datenintegrität]], [[Daten]]
#datenbanken 

---
Eine **PROCEDURE** (oft Stored Procedure genannt) ist ein in der Datenbank gespeichertes Programm, das komplexe Geschäftsprozesse ausführt. In PostgreSQL existieren sie als eigenständiges Konstrukt erst seit Version 11.

Die 3 fundamentalen Unterschiede zur FUNCTION

Obwohl Funktionen und Prozeduren fast die gleiche Syntax (`LANGUAGE plpgsql`) nutzen, unterscheiden sie sich architektonisch massiv:

1. **Aufruf:** Prozeduren können **nicht** in SQL-Befehlen (wie `SELECT`) verwendet werden. Sie werden isoliert über den Befehl `CALL` gestartet.
2. **Transaktionskontrolle:** Prozeduren dürfen eigene Transaktionsbefehle wie `COMMIT` oder `ROLLBACK` enthalten. Das ist essenziell für langlaufende Prozesse (z.B. ein Monatsabschluss, der nach jedem 1000. Datensatz den Zwischenstand sichern muss).
3. **Kein Rückgabewert per RETURN:** Das Schlüsselwort `RETURN` dient in einer Prozedur ausschließlich dazu, die Ausführung _sofort zu beenden_. Es liefert niemals einen Wert zurück.

Parameter-Arten (Der Weg rein und raus)

Da es kein echtes `RETURN` gibt, fließen Daten über den Parameter-Kopf der Prozedur:

- **IN:** Reiner Eingabewert (Standard).
- **OUT:** Dient als Container für die Rückgabe von Werten an den Aufrufer.
- **INOUT:** Wird mit einem Wert reingegeben, in der Prozedur verändert und als neues Ergebnis wieder herausgegeben.

--------------------------------------------------------------------------------

Beispiele für Procedures

**Beispiel 1: Eine einfache Prozedur (Nur IN-Parameter)** _Szenario:_ Wir wollen den zugeordneten Support-Mitarbeiter eines Kunden ändern.

```sql
CREATE OR REPLACE PROCEDURE change_support_staff(
    p_customer_id INT,            -- Implizit ein IN Parameter
    p_new_support_id INT          -- Implizit ein IN Parameter
) 
LANGUAGE plpgsql 
AS $$ 
BEGIN
    UPDATE Customer 
    SET Support_Rep_Id = p_new_support_id 
    WHERE Customer_Id = p_customer_id;
END 
$$;

-- Aufruf der Prozedur:
CALL change_support_staff(1, 5);
```

**Beispiel 2: Prozedur mit Transaktion (COMMIT) und Rückgabewerten (OUT)** _Szenario:_ Wir fügen ein neues Genre hinzu, sichern das Ergebnis sofort unwiderruflich in der Datenbank (`COMMIT`) und geben eine Erfolgsmeldung sowie die neue Gesamtanzahl der Genres zurück.

```sql
CREATE OR REPLACE PROCEDURE add_genre(
    IN new_genre text,         
    IN new_genre_id int,       
    OUT result_message text,   -- 1. Rückgabewert
    OUT new_count int          -- 2. Rückgabewert
) 
LANGUAGE plpgsql 
AS $$
BEGIN
    -- 1. Daten einfügen
    INSERT INTO genre (name, genre_id) VALUES (new_genre, new_genre_id);
    
    -- 2. TRANSAKTION ABSCHLIESSEN (Nur in Procedures erlaubt!)
    COMMIT; 
    
    -- 3. Rückgabewerte befüllen
    SELECT COUNT(genre_id) INTO new_count FROM genre;  
    result_message := 'Datensatz hinzugefügt. ID: ' || new_genre_id || ', Name: ' || new_genre;
    
    -- RETURN beendet nur die Prozedur, gibt aber result_message und new_count automatisch zurück
    RETURN; 
END;
$$;

-- Aufruf der Prozedur:
CALL add_genre('Heavy Metal', 97, NULL, NULL);
```

--------------------------------------------------------------------------------

### Flashcards

Inwiefern unterscheiden sich Funktionen (FUNCTIONS) und Prozeduren (PROCEDURES) hinsichtlich ihres Einsatzzwecks und der Transaktionssteuerung?
?
Funktionen liefern immer einen Wert zurück und werden für Berechnungen innerhalb regulärer SQL-Anweisungen (z.B. SELECT) genutzt. Prozeduren steuern Prozessabläufe und können im Gegensatz zu Funktionen eigene Transaktionsbefehle (wie COMMIT oder ROLLBACK) enthalten.
<!--SR:!2026-06-11,1,230-->

Mit welchem Befehl wird eine PROCEDURE aufgerufen und wie unterscheidet sich dieser vom Aufruf einer Funktion?::Eine Prozedur wird zwingend mit dem Befehl `CALL` aufgerufen (z.B. `CALL my_proc()`). Im Gegensatz zu Funktionen kann eine Prozedur nicht direkt innerhalb einer SQL-Anweisung (z.B. im SELECT) verwendet werden.

Erklären Sie den Unterschied zwischen IN-, OUT- und INOUT-Parametern bei Prozeduren.
?
**IN:** Reine Eingabewerte, die der Prozedur übergeben werden. **OUT:** Dienen ausschließlich der Rückgabe von Werten an den Aufrufer (da Prozeduren kein normales RETURN für Werte nutzen können). **INOUT:** Parameter, die sowohl als Eingabe empfangen werden, als auch verändert als Ausgabe zurückgegeben werden.
<!--SR:!2026-06-10,0,230-->

Welche Rolle spielt das Schlüsselwort `RETURN` innerhalb einer PROCEDURE?::Es dient ausschließlich dazu, die Ausführung der Prozedur sofort zu beenden. Es liefert (anders als bei einer Funktion) niemals einen Wert an den Aufrufer zurück.

Wie ruft man in der Java-Programmierung über JDBC eine Stored Procedure auf?::Man nutzt dafür nicht das normale `Statement`, sondern ein spezielles `CallableStatement` (z.B. `conn.prepareCall("CALL proc_name(?, ?)");`).

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Procedure]]
SORT file.mtime DESC
```