#Note

2026-06-09

Tags: [[Datenbanksystem]], [[Relationale Datenbank]], [[SQL DDL]], [[Logische Operatoren]], [[Daten]]
#datenbanken 

---
Datenbankseitige **Functions** gehören zur serverseitigen Programmierung. Anstatt Rohdaten an ein Java-Programm zu schicken, damit dieses rechnet, lassen wir die Datenbank selbst rechnen und schicken nur das fertige Ergebnis zurück. Eine Funktion wird immer über `CREATE FUNCTION` erstellt und kann direkt in ganz normalen SQL-Abfragen (wie im `SELECT`) aufgerufen werden.

Je nach Komplexität der Anforderung wählt man zwischen zwei Sprachen:

1. Die puristische Variante: LANGUAGE SQL

Hier sind **nur reine SQL-Befehle** erlaubt. Es gibt keine Schleifen, keine IF-Bedingungen und keine Variablen-Deklaration.

- **Das Wichtigste:** Es gibt in der Regel kein explizites `RETURN`. Der Rückgabewert ergibt sich _implizit_ aus dem Ergebnis der allerletzten SQL-Anweisung in der Funktion.
- **Dollar-Quoting (****$$****):** Um den Code-Block ("Rumpf") vom Tabellenschema abzutrennen und Probleme mit internen Anführungszeichen zu vermeiden, wird der Code zwingend in `$$` eingeschlossen.

**Beispiel (LANGUAGE SQL):** Ein Kunde soll mit vollem Namen formatiert zurückgegeben werden.

```sql
CREATE OR REPLACE FUNCTION kundenname(cust_id integer) 
RETURNS varchar(100) 
LANGUAGE SQL 
AS $$
    -- Der letzte (und einzige) Befehl definiert den Rückgabewert
    SELECT "FirstName" || ' ' || "LastName" 
    FROM "Customer" 
    WHERE "CustomerId" = cust_id;
$$;

-- Aufruf in einer Abfrage:
SELECT kundenname(5);
```

_(Quelle: Vorlesung)_

_Hinweis:_ Wenn eine LANGUAGE SQL-Funktion mehrere DML-Anweisungen (`INSERT/UPDATE`) enthält, sollte der Block in `BEGIN ATOMIC ... END` gekapselt werden, um die Transaktionssicherheit (Atomarität) zu garantieren.

2. Die mächtige Variante: LANGUAGE PL/pgSQL

PL/pgSQL verbindet normales SQL mit den Elementen einer echten, prozeduralen Programmiersprache.

- **Variablen:** Werden im zwingend erforderlichen Block `DECLARE` definiert.
- **Abfragen speichern:** Man kann das Ergebnis eines SQL-Befehls mit `SELECT ... INTO <Variable>` direkt in eine Variable schreiben.
- **Logik:** Erlaubt `IF...THEN...ELSE`, `LOOP` und Fehlerbehandlung (`EXCEPTION`).
- **Rückgabe:** Der Code muss in `BEGIN ... END;` stehen und zwingend mit einem expliziten `RETURN <Wert>;` beendet werden.

**Beispiel (LANGUAGE PL/pgSQL):** Komplexe Rabatt-Berechnung mit Variablen und IF/ELSE-Logik.

```sql
CREATE OR REPLACE FUNCTION discount(invoice_id_param integer) 
RETURNS numeric 
LANGUAGE plpgsql 
AS $$ 
DECLARE
    -- Variablen müssen vorher zwingend deklariert werden
    invoice_total numeric;     
    discount_amount numeric := 0.00;  
BEGIN
    -- 1. Echten Wert aus Tabelle in lokale Variable schreiben
    SELECT total INTO invoice_total     
    FROM invoice     
    WHERE invoice_id = invoice_id_param;      
    
    -- 2. Prozedurale Logik (IF / ELSE)
    IF invoice_total > 10.00 THEN         
        discount_amount := invoice_total * 0.10;     
    ELSE         
        discount_amount := invoice_total * 0.05;     
    END IF;          
    
    -- 3. Explizites Return zwingend erforderlich
    RETURN discount_amount; 
END; 
$$;

-- Aufruf:
SELECT invoice_id, total, discount(invoice_id) AS Rabatt FROM invoice;
```

_(Quelle: Übungsaufgaben)_

--------------------------------------------------------------------------------

### Flashcards

Nenne zwei Architektur-Vorteile und zwei Risiken, die mit der Implementierung von Business-Logik direkt in der Datenbank (Functions/Procedures) verbunden sind.
?
**Vorteile:** Weniger Netzwerk-Traffic (keine Zwischenergebnisse werden zum Client geschickt) und bessere Performance. **Risiken:** Höhere Komplexität (Logik ist zwischen Backend und Datenbank verstreut) und schlechte Portierbarkeit (Vendor Lock-in) aufgrund proprietärer Herstellersprachen.
<!--SR:!2026-06-10,0,230-->

Inwiefern unterscheiden sich Funktionen (FUNCTIONS) und Prozeduren (PROCEDURES) hinsichtlich ihres Einsatzzwecks und der Transaktionssteuerung?
?
**Funktionen** liefern immer einen Wert zurück und werden typischerweise für Berechnungen innerhalb von SQL-Befehlen (z.B. SELECT) genutzt. **Prozeduren** liefern keinen Wert zurück (nur über Ausgabe-Parameter) und dienen der Steuerung von Prozessabläufen. Im Gegensatz zu Funktionen dürfen Prozeduren eigene Transaktionsbefehle (wie `COMMIT` oder `ROLLBACK`) ausführen.

Wie wird der Rückgabewert in einer Funktion mit `LANGUAGE SQL` festgelegt, wenn keine explizite RETURN-Anweisung verwendet wird?::Er ergibt sich implizit aus dem Ergebnis der **allerletzten SQL-Anweisung** im Funktionskörper.

Wozu dient das sogenannte "Dollar-Quoting" (`$$`) im Rumpf einer PostgreSQL-Funktion?::Es fungiert als Body-Delimiter, um den auszuführenden Programmcode zu umschließen. Dies vermeidet Syntax-Probleme, falls der enthaltene Code selbst wieder einfache Anführungszeichen (`'`) oder Zeilenumbrüche enthält.

Welche Bedeutung hat das Konstrukt `BEGIN ATOMIC ... END` innerhalb einer SQL-Funktion?::Es garantiert die Transaktionssicherheit (Atomarität) für den Fall, dass die SQL-Funktion mehrere DML-Operationen (`INSERT/UPDATE/DELETE`) ausführt. Entweder werden alle Schritte erfolgreich verarbeitet oder alle bei einem Fehler vollständig zurückgerollt.

Welche prozeduralen Elemente bietet die Sprache `PL/pgSQL`, die im reinen `LANGUAGE SQL` nicht zur Verfügung stehen?::Sie bietet Ablaufsteuerungen (Kontrollstrukturen) wie `IF...THEN`, `LOOP` oder `WHILE`, die Deklaration von lokalen Variablen sowie eine robuste Fehlerbehandlung über `EXCEPTION`.

Wo müssen Variablen in einer PL/pgSQL-Funktion deklariert werden und welche Ausnahme gibt es dabei?::Alle Variablen müssen im `DECLARE`-Block deklariert werden. Die einzige Ausnahme sind die **Übergabeparameter** der Funktion; diese sind implizit deklariert und direkt im Codeblock verfügbar.
<!--SR:!2026-06-10,0,230-->

Mit welcher Anweisung können Abfrageergebnisse in PL/pgSQL direkt in deklarierten Variablen gespeichert werden?::Durch die Anweisung `SELECT ... INTO <Variablenname>`.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Function]]
SORT file.mtime DESC
```