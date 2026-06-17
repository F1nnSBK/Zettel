# DB-Klausur Survival-Sheet & Musterlösungen (DHBW 2026)

## 1. Musterlösungen der Probeklausur ("Beispiele Klausuraufgaben")

### Typ 1: DDL Tabelle erstellen (Seite 1)

_Aufgabenstellung:_

Gegeben ist das Relationen-Schema mit den Tabellen `track`, `album` und `artist`. Schreiben Sie einen SQL-Befehl für das Erstellen der Tabelle `album` mit allen Integritätsbedingungen (Hinweis: `artist_id` ist ein Fremdschlüssel, `album_id` der Primärschlüssel).

```
CREATE TABLE album (
    album_id int4 NOT NULL,
    title varchar(160) NOT NULL,
    artist_id int4 NOT NULL,
    CONSTRAINT pk_album PRIMARY KEY (album_id),
    CONSTRAINT fk_album_artist FOREIGN KEY (artist_id) REFERENCES artist(artist_id)
);
```

### Typ 2: DQL GROUP BY Auswertung (Seite 1-2)

_Aufgabenstellung:_

Gegeben ist eine Tabelle `xcustomer` mit Spalten für `last_name`, `country`, `email`, `company` und `postal_code`. Ermitteln Sie das Ergebnis der folgenden SQL-Abfrage:

`SELECT country, count(country) FROM xcustomer GROUP BY country HAVING count(country) > 1;`

```
country | count
--------+-------
Canada  |     2
Brazil  |     2
USA     |     2
```

_(Hinweis: Czech Republic, Austria und Germany fallen weg, da deren Anzahl jeweils genau 1 ist)_

### Typ 3: Multiple Choice Index (Seite 2)

_Aufgabenstellung:_

Welchen Hauptzweck erfüllt ein Index in einer relationalen Datenbanktabelle? (Bitte kreuzen Sie die richtige Antwort an).

- **Richtige Antwort:**
    
    `[X] Er beschleunigt Such- und Abfragevorgänge, indem er einen schnelleren Zugriff auf die Daten ermöglicht.`
    

### Typ 4: SQL-Join schreiben (Seite 2)

_Aufgabenstellung:_

Erstellen Sie einen SQL-Befehl für das gegebene Relationen-Schema, um folgende Anforderung umzusetzen: Finde die Titel aller Alben (aus der Tabelle `album`), die von dem Künstler mit dem Namen 'Metallica' (`name` aus der Tabelle `artist`) stammen.

```
SELECT al.title 
FROM album AS al
JOIN artist AS ar ON al.artist_id = ar.artist_id
WHERE ar.name = 'Metallica';
```

### Functions & Trigger - Typ 1: Auswertung (Seite 3)

_Aufgabenstellung:_

Gegeben ist die PL/pgSQL-Funktion `anzahl(unteregrenze int, oberegrenze int)` und ein Ausschnitt der Tabelle `invoice`. Was ist das Ergebnis des folgenden Selects, wenn diese Funktion aufgerufen wird?

`SELECT count(*) AS Gesamtanzahl, anzahl(10,100) AS imBereich FROM invoice;`

```
gesamtanzahl | imbereich
-------------+-----------
           9 |         1
```

_(Hinweis: Die Tabelle enthält insgesamt 9 Rechnungen. Nur der Datensatz mit der ID 23 hat einen Gesamtwert von `13.86`, der zwischen 10 und 100 liegt.)_

### Functions & Trigger - Typ 2: Trigger schreiben (Seite 4)

_Aufgabenstellung:_

Erstellen Sie einen Trigger und eine Trigger-Funktion, um folgende Anforderung umzusetzen: Beim Einfügen eines neuen Genres in die Tabelle `genre` soll geprüft werden, ob der `name` des Genres belegt ist. Wenn der `name` NULL ist, soll er automatisch auf den Text 'Untitled Genre' gesetzt werden.

```
-- 1. Trigger-Funktion (PL/pgSQL)
CREATE OR REPLACE FUNCTION handle_null_genre_name()
RETURNS TRIGGER 
LANGUAGE plpgsql
AS $$
BEGIN
    IF NEW.name IS NULL THEN
        NEW.name := 'Untitled Genre';
    END IF;
    RETURN NEW; -- Gibt den modifizierten Datensatz weiter
END;
$$;

-- 2. Trigger-Bindung
CREATE TRIGGER tr_genre_null_check
BEFORE INSERT ON genre
FOR EACH ROW
EXECUTE FUNCTION handle_null_genre_name();
```

### JDBC - Typ 1: Code-Ergänzung (Seite 5-6)

_Aufgabenstellung:_

Ergänzen Sie das vorgegebene Java-Programm (das bereits die Verbindung über das `Connection`-Objekt `conn` herstellt und Ressourcen am Ende schließt) im Bereich zwischen `START` und `ENDE` zur Umsetzung der folgenden Aufgaben:

- a) Alle Künstler (artist_id, name) aus der Tabelle `artist` ausgeben.
    
- b) Sicheres Einfügen eines neuen Künstlers mit PreparedStatement (Schutz vor SQL-Injection).
    

```java
// === START Code für Aufgaben a) und b) ===

// a) Alle Kuenstler ausgeben
Statement st = null;
ResultSet rs = null;
try {
    st = conn.createStatement();
    rs = st.executeQuery("SELECT artist_id, name FROM artist;");
    while (rs.next()) {
        int id = rs.getInt("artist_id");
        String name = rs.getString("name");
        System.out.println("ID: " + id + " | Name: " + name);
    }
} catch (SQLException e) {
    e.printStackTrace();
} finally {
    if (rs != null) rs.close();
    if (st != null) st.close();
}

// b) Sicheres Einfuegen mit PreparedStatement
String sql = "INSERT INTO artist (artist_id, name) VALUES (?, ?);";
try (PreparedStatement pst = conn.prepareStatement(sql)) {
    pst.setInt(1, 999);            // Setzt artist_id (Erster Parameter)
    pst.setString(2, "Metallica");  // Setzt name (Zweiter Parameter)
    pst.executeUpdate();
} catch (SQLException e) {
    e.printStackTrace();
}

// === ENDE Code für Aufgaben a) und b) ===
```

## 2. Übungsblatt: DB-interne Programmierung & Transaktionen

### Aufgabe 1: Avg track length of album (LANGUAGE SQL)

Erstellen Sie eine Funktion, die die durchschnittliche Länge (Milliseconds) aller Tracks eines bestimmten Albums (album_id) zurückgibt.

```
CREATE OR REPLACE FUNCTION get_avg_track_length(id integer)
RETURNS int
LANGUAGE SQL
AS $$
    SELECT AVG(milliseconds)
    FROM track
    WHERE album_id = id;
$$;
```

### Aufgabe 2: Track count by artist name (LANGUAGE SQL)

Erstellen Sie eine Funktion, die die Anzahl der Tracks zurückgibt, die von dem Künstler erstellt wurden, dessen Name als Parameter übergeben wird.

```sql
CREATE OR REPLACE FUNCTION count_tracks_by_artistname(suchname TEXT)
RETURNS int
LANGUAGE SQL
AS $$
    SELECT COUNT(t.track_id)
    FROM track AS t
    JOIN album AS a ON t.album_id = a.album_id
    JOIN artist AS r ON a.artist_id = r.artist_id
    WHERE r.name = suchname;
$$;
-- Hinweis: TEXT-Datentyp verhindert Typenkonflikte beim Join-Vergleich.
```

### Aufgabe 3: Employee hire date by ID (LANGUAGE SQL)

Erstellen Sie eine Funktion, die das Einstellungsdatum (HireDate) eines Mitarbeiters (Employee) anhand der übergebenen EmployeeId zurückgibt.

```
CREATE OR REPLACE FUNCTION get_employee_hire_date(emp_id int)
RETURNS date
LANGUAGE SQL
AS $$
    SELECT hire_date
    FROM employee
    WHERE employee_id = emp_id;
$$;
```

### Aufgabe 4: Total invoice lines by employee ID (LANGUAGE SQL)

Erstellen Sie eine Funktion, die die Gesamtzahl der Rechnungszeilen (InvoiceLine) zurückgibt, die von einem bestimmten EmployeeId betreut wurden.

```
CREATE OR REPLACE FUNCTION count_invoicelines_by_employee(id int)
RETURNS int
LANGUAGE SQL
AS $$
    SELECT COUNT(il.invoice_line_id)
    FROM invoice_line AS il
    JOIN invoice AS i ON il.invoice_id = i.invoice_id
    JOIN customer AS c ON i.customer_id = c.customer_id
    JOIN employee AS e ON c.support_rep_id = e.employee_id
    WHERE e.employee_id = id;
$$;
```

### Aufgabe 5: Check if customer has invoices (LANGUAGE PL/pgSQL)

Erstellen Sie eine Funktion, die prüft, ob ein Kunde (CustomerId) überhaupt Rechnungen in der Datenbank hat. Rückgabe "hat Rechnung" wenn mindestens eine Rechnung existiert, ansonsten "hat keine Rechnung".

```
CREATE OR REPLACE FUNCTION check_customer_invoices(cust_id integer)
RETURNS varchar(20)
LANGUAGE plpgsql
AS $$
BEGIN
    IF EXISTS (SELECT 1 FROM invoice WHERE customer_id = cust_id) THEN
        RETURN 'hat Rechnung';
    ELSE
        RETURN 'hat keine Rechnung';
    END IF; 
END;
$$;
```

### Aufgabe 6: Support rep email of customer, local variable (LANGUAGE PL/pgSQL)

Erstellen Sie eine Funktion, die die E-Mail-Adresse des Vertriebsmitarbeiters (SupportRepId) eines bestimmten Kunden (CustomerId) abruft. Speichern Sie das Ergebnis in einer lokalen Variablen, bevor Sie es zurückgeben.

```
CREATE OR REPLACE FUNCTION get_support_email(cust_id integer)
RETURNS text
LANGUAGE plpgsql
AS $$
DECLARE
    support_email text;
BEGIN
    SELECT e.email INTO support_email
    FROM customer AS c
    JOIN employee AS e ON c.support_rep_id = e.employee_id
    WHERE c.customer_id = cust_id;

    RETURN support_email;
END;
$$;
```

### Aufgabe 7: Calculate discount based on total (LANGUAGE PL/pgSQL)

Erstellen Sie eine Funktion, die den Rabatt auf eine Rechnung (invoice_id) berechnet. Ist "total" der Rechnung größer als 10.00, beträgt der Rabatt 10% des Gesamtbetrags; ansonsten beträgt er 5%.

```
CREATE OR REPLACE FUNCTION calculate_discount(invoice_id_param integer)
RETURNS numeric
LANGUAGE plpgsql
AS $$
DECLARE
    invoice_total numeric;
    discount_amount numeric := 0.00;
BEGIN 
    SELECT total INTO invoice_total
    FROM invoice
    WHERE invoice_id = invoice_id_param;

    IF invoice_total > 10.00 THEN
        discount_amount := invoice_total * 0.10;
    ELSE
        discount_amount := invoice_total * 0.05;
    END IF;

    RETURN discount_amount;
END;
$$;
```

### Aufgabe 8: Trigger: check hire_date update (LANGUAGE PL/pgSQL)

Erstellen sie einen Trigger und Trigger-Funktion. Bei der Aktualisierung des hire_date in der Tabelle employee soll überprüft werden, ob das neue Datum (NEW.HireDate) nach dem alten Datum (OLD.HireDate) liegt. Wenn nicht, soll eine Exception ausgelöst werden.

```
-- 1. Trigger-Funktion
CREATE OR REPLACE FUNCTION check_hire_date()
RETURNS TRIGGER
LANGUAGE plpgsql
AS $$
BEGIN
    IF NEW.hire_date < OLD.hire_date THEN
        RAISE EXCEPTION 'Das neue Einstellungsdatum darf nicht vor dem alten liegen';
    END IF;
    RETURN NEW;
END;
$$;

-- 2. Trigger-Bindung (Spaltenspezifisch vor dem Update)
CREATE TRIGGER check_date_forward
BEFORE UPDATE OF hire_date ON employee
FOR EACH ROW
EXECUTE FUNCTION check_hire_date();
```

### Aufgabe 9: Trigger: default media_type_id to most frequent (LANGUAGE PL/pgSQL)

Beim Einfügen eines neuen Tracks in die Tabelle track soll der "media_type_id" automatisch auf den Wert des am häufigsten verwendeten "media_type_id" in der Datenbank gesetzt werden, falls der Wert NULL ist.

```
-- 1. Trigger-Funktion
CREATE OR REPLACE FUNCTION default_media_type()
RETURNS TRIGGER
LANGUAGE plpgsql
AS $$
DECLARE
    most_used_media_id int;
BEGIN
    IF NEW.media_type_id IS NULL THEN
        -- Findet den am haeufigsten verwendeten Medientyp
        SELECT media_type_id INTO most_used_media_id
        FROM track
        GROUP BY media_type_id
        ORDER BY COUNT(*) DESC
        LIMIT 1;

        NEW.media_type_id := most_used_media_id;
    END IF;
    RETURN NEW;
END;
$$;

-- 2. Trigger-Bindung (Vor dem Einfuegen)
CREATE TRIGGER default_media_type_trigger
BEFORE INSERT ON track
FOR EACH ROW
EXECUTE FUNCTION default_media_type();
```

### Aufgabe 10: Repeatable Read Execution Script (Praxis)

Zwei parallele Sessions (Autocommit aus in DBeaver/psql). Ablauf:

**Session 1 Script:**

```
SET SCHEMA 'chinook';
START TRANSACTION;
SET TRANSACTION ISOLATION LEVEL REPEATABLE READ;

-- Schritt 3: Update ausfuehren und committen waehrend Session 2 aktiv ist
UPDATE genre SET name = 'RR' WHERE genre_id = 4;
COMMIT;
```

**Session 2 Script:**

```
SET SCHEMA 'chinook';
START TRANSACTION;
SET TRANSACTION ISOLATION LEVEL REPEATABLE READ;

-- Schritt 2: Initialen Wert auslesen
SELECT * FROM genre WHERE genre_id = 4;

-- Schritt 4: Erneut lesen (Wert bleibt unveraendert trotz Commit in Session 1)
SELECT * FROM genre WHERE genre_id = 4;

-- Schritt 5: Commit und erneutes Auslesen (Aenderung nun sichtbar)
COMMIT;
SELECT * FROM genre WHERE genre_id = 4;
```

### Aufgabe 11: Was ist eine Transaktion & ACID-Eigenschaften (Theorie)

- **Definition:** Eine Transaktion ist eine logische Einheit von Datenbankanweisungen (Logical Unit of Work), die eine Datenbank von einem konsistenten Zustand in einen neuen konsistenten Zustand überführt.
    
- **ACID-Garantien:**
    
    - **Atomicity (Atomarität):** Ganz-oder-gar-nicht-Prinzip. Bei Fehlern erfolgt ein `ROLLBACK` aller Teilschritte.
        
    - **Consistency (Konsistenz):** Einhaltung aller Integritätsbedingungen vor und nach der Transaktion.
        
    - **Isolation (Isolation):** Parallele Transaktionen beeinflussen sich nicht gegenseitig. Zwischenzustände sind unsichtbar.
        
    - **Durability (Dauerhaftigkeit):** Nach dem `COMMIT` sind Änderungen permanent gespeichert (auch bei Systemausfall geschützt via Write-Ahead-Logging).
        

### Aufgabe 12: Pessimistisches vs. Optimistisches Locking (Theorie)

- **Pessimistische Strategie:**
    
    - _Prinzip:_ Konflikte werden erwartet. Sperrt Daten sofort beim Zugriff (Locks).
        
    - _Nachteil:_ Wartezeiten für andere Transaktionen, hohes Risiko von **Deadlocks** (gegenseitige Blockierung).
        
    - _Einsatz:_ Bei vielen parallelen Schreibzugriffen/Konflikten.
        
- **Optimistische Strategie:**
    
    - _Prinzip:_ Konflikte sind selten. Transaktionen arbeiten ohne Sperren auf Kopien. Erst vor dem `COMMIT` wird validiert, ob sich die Originaldaten geändert haben.
        
    - _Nachteil:_ Bei Konflikten erfolgt ein harter Abbruch (`ROLLBACK`) und die Transaktion muss komplett neu starten.
        
    - _Einsatz:_ Bei niedriger Konfliktrate (viele Lesezugriffe, wenige Schreibzugriffe).
        

### Aufgabe 13: Die 3 Concurrency-Probleme & Verbot (Theorie)

- **Dirty Read (READ UNCOMMITTED):** TA1 liest Daten von TA2, bevor TA2 diese committed hat. Nimmt TA2 die Änderung zurück (Rollback), arbeitet TA1 auf ungültigen Daten.
    
- **Non-Repeatable Read (READ COMMITTED):** TA1 liest einen Datensatz zweimal. TA2 ändert/löscht diesen Datensatz dazwischen und committet. TA1 sieht beim zweiten Lesen einen anderen Wert.
    
- **Phantom Read (REPEATABLE READ):** TA1 liest einen Bereich (z.B. per `COUNT`). TA2 fügt neue Zeilen in diesen Bereich ein und committet. TA1 sieht beim zweiten Lesen neue "Phantome".
    
- **Das absolute Verbot:** Ein **Dirty Write** (Lost Update) – das Überschreiben uncommitted Daten durch eine parallele Transaktion – ist in der SQL-Norm in **allen** Isolation Leveln strikt verboten.
    

## 3. NoSQL CRUD (Redis & MongoDB)

### Redis (Key-Value)

- **Write:** `SET track:8888 "For Those About To Rock"`
    
- **Read:** `GET track:8888`
    
- **Delete:** `DEL track:8888`
    

### MongoDB (JSON-Documents)

- **Write:**
    
    ```
    db.track.insertOne({ track_id: 8888, name: "For Those About To Rock", price: 0.99 })
    ```
    
- **Read:**
    
    ```
    db.track.find({ track_id: 8888 })
    ```
    

## 4. Theorie-Dreieck (CAP, ACID, BASE)

### CAP-Theorem

- **C (Consistency):** Alle Knoten sehen zeitgleich dieselben Daten (Linearisierbarkeit).
    
- **A (Availability):** Jede fehlerfreie Anfrage erhält immer eine Antwort.
    
- **P (Partition Tolerance):** Das System läuft bei Netzwerkausfällen zwischen Knoten weiter.
    
- _Klausur-Regel:_ Da Netzwerkausfälle (P) real auftreten, muss ein verteiltes System P wählen und sich zwischen CP (Konsistenz) oder AP (Verfügbarkeit) entscheiden.
    

### ACID vs. BASE

- **ACID (Starke Konsistenz - RDBMS):**
    
    - Atomicity: Alles-oder-Nichts-Prinzip.
        
    - Consistency: Erhalt der Integrität (referenzielle Integrität, Foreign Keys).
        
    - Isolation: Transaktionen beeinflussen sich nicht gegenseitig.
        
    - Durability: Dauerhafte Speicherung nach Commit (gesichert über Redo-Logs & Savepoints).
        
- **BASE (Schwache Konsistenz - NoSQL):**
    
    - Basically Available: Grundlegende Verfügbarkeit wird priorisiert.
        
    - Soft State: Datenzustand ist flüchtig, Replikate können kurzzeitig asynchron sein.
        
    - Eventual Consistency: Replikate gleichen sich nach einer gewissen Zeit automatisch an.
        

## 5. Programmierung DB-seitig (Functions & Procedures)

### 5.1 Functions: LANGUAGE SQL vs. LANGUAGE PL/pgSQL

- **LANGUAGE SQL:** Reine SQL-Statements, kein `BEGIN/END`. Der Rückgabewert ergibt sich implizit aus der allerletzten Anweisung (SELECT oder DML mit `RETURNING`).
    
- **LANGUAGE PL/pgSQL:** Prozedurale Sprache mit `DECLARE`, `BEGIN/END`, `IF/THEN/ELSE`, Schleifen und `EXCEPTION`. Zuweisungen mit `:=`. `RETURN` ist zwingend erforderlich.
    

### 5.2 PROCEDURES (Prozeduren)

- Haben keinen Rückgabetyp (kein `RETURNS`).
    
- Aufruf über `CALL prozedur_name(params);`.
    
- **Unterschied zu Functions:** Dürfen Transaktionsbefehle wie `COMMIT`, `ROLLBACK` oder `START TRANSACTION` enthalten (Functions dürfen das nicht!).
    

#### Muster: Procedure mit IN und OUT Parametern (PL/pgSQL)

```
CREATE OR REPLACE PROCEDURE calculate_salary_bonus(
    IN p_emp_id int, 
    IN p_bonus_percentage numeric,
    OUT p_final_bonus numeric
)
LANGUAGE plpgsql
AS $$
DECLARE
    v_current_salary numeric;
BEGIN
    SELECT salary INTO v_current_salary 
    FROM employee 
    WHERE employee_id = p_emp_id;

    p_final_bonus := v_current_salary * (p_bonus_percentage / 100.0);
    
    -- Erlaubt in Procedures, verboten in Functions
    COMMIT; 
END;
$$;
```

## 6. JPA / Hibernate (Java Persistence API)

JPA löst den Object-Relational Impedance Mismatch (konzeptioneller Unterschied zwischen Objektmodell und relationaler Welt: Vererbung, Identität, Navigation).

### 6.1 Die 4 Zustände des Objekt-Lebenszyklus

1. **Transient (Neu):** Mit `new` erzeugt, existiert nur im Heap (RAM). Hat keine Verbindung zum PC, keine DB-ID.
    
2. **Managed (Verwaltet):** Im PC registriert (via `persist()` oder `find()`). Jede Änderung an Settern wird automatisch überwacht und beim `commit()` in die DB gespült.
    
3. **Detached (Abgelöst):** War managed, aber der `EntityManager` wurde geschlossen oder `detach()` gerufen. Änderungen werden nicht mehr verfolgt.
    
4. **Removed (Gelöscht):** Mit `remove()` markiert. Wird beim nächsten Sync (`flush`/`commit`) gelöscht.
    

### Klausurmuster: JPA-Operationen

```
em.getTransaction().begin();

try {
    // 1. CREATE (Transient -> Managed)
    Person p = new Person();
    p.setVorname("Max");
    em.persist(p); 

    // 2. READ (Laden per ID - hocheffizient)
    Person dbPerson = em.find(Person.class, 1L);

    // 3. UPDATE (Passiert automatisch auf Managed-Objekten!)
    if (dbPerson != null) {
        dbPerson.setVorname("Lena"); // Wird beim Commit automatisch synchronisiert
    }

    // 4. DELETE (Managed-Objekt zum Loeschen markieren)
    // em.remove(dbPerson);

    em.getTransaction().commit(); 
} catch (Exception e) {
    if (em.getTransaction().isActive()) em.getTransaction().rollback();
    e.printStackTrace();
} finally {
    em.close();
    factory.close();
}
```

## 7. Vor- und Nachteile datenbankseitiger Logik (Stored Procedures, Functions, Trigger)

- **Vorteile:**
    
    - **Performance:** Weniger Netzwerktraffic, da Zwischenergebnisse direkt in der DB verarbeitet werden und nur das Endergebnis an den Client geht.
        
    - **Sicherheit/Zentralisierung:** Einheitliche Durchsetzung von Geschäftslogik für alle Clients, die auf die DB zugreifen (Single Source of Truth).
        
- **Nachteile:**
    
    - **Architektur/Komplexität:** Logik ist über mehrere Schichten (Anwendungscode und Datenbankschicht) verteilt.
        
    - **Portierbarkeit:** Proprietäre SQL-Dialekte (PL/pgSQL vs. T-SQL) erschweren einen DB-Wechsel massiv.
        
    - **Entwicklungstooling:** Schlechtere Integration in Standard-IDEs, eingeschränkte Debugging-Möglichkeiten.
        

## 8. NoSQL Klassifizierungen & CAP-Zuordnung

1. **Key-Value Datenbanken**
    
    - _Prinzip:_ Speicherung von Werten unter einem eindeutigen Schlüssel. Extrem performant.
        
    - _Beispiel:_ Redis (AP oder CP, je nach Konfiguration).
        
2. **Dokumentenorientierte Datenbanken**
    
    - _Prinzip:_ Semistrukturierte Daten (JSON, XML).
        
    - _Beispiel:_ MongoDB (CP - Konsistenzfokus bei Partitionierung).
        
3. **Wide-Column Datenbanken (Spaltenorientiert)**
    
    - _Prinzip:_ Daten zeilenweise gruppiert in Spaltenfamilien, hochgradig partitioniert.
        
    - _Beispiel:_ Apache Cassandra (AP - hohe Verfügbarkeit).
        
4. **Graphdatenbanken**
    
    - _Prinzip:_ Fokus auf Beziehungen (Knoten und Kanten).
        
    - _Beispiel:_ Neo4j (In der Regel CA/Schnittstelle, da oft ACID-konform).
        

## 9. Object-Relational Impedance Mismatch (Die 5 Probleme)

1. **Identität (Identity):** Java nutzt Objektreferenz (` ==` oder `equals()`), RDBMS nutzt den Primärschlüssel (`Primary Key`).
    
2. **Granularität (Granularity):** Java nutzt beliebig viele nutzerdefinierte Klassen (z.B. Klasse `Address`), RDBMS speichert dies oft flach in wenigen Tabellenspalten der Haupttabelle.
    
3. **Vererbung (Inheritance):** Java kennt Vererbung nativ. RDBMS kennt keine Vererbung (Mapping-Strategien nötig: Single Table, Joined, Table per Class).
    
4. **Assoziation (Association):** Java nutzt gerichtete Objektreferenzen (A kennt B). RDBMS nutzt ungerichtete Fremdschlüsselbeziehungen mit n:m-Hilfstabellen.
    
5. **Navigation:** Java navigiert über Objektpfade (`order.getCustomer().getAddress()`). RDBMS benötigt hierfür teure relationale Joins.