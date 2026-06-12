#Note

2026-06-12

Tags: [[Datenbanken]], [[Java]], [[JDBC]], [[Backend]], [[API]]
#datenbanken 

---
**JDBC (Java Database Connectivity)** ist die Standard-Schnittstelle in der Java-Welt (Pakete `java.sql` und `javax.sql`), um auf relationale Datenbanken zuzugreifen. Die Genialität von JDBC ist seine **Datenbankneutralität**: Das Java-Programm muss nicht wissen, ob im Keller eine Oracle, MySQL oder PostgreSQL läuft. Der Java-Code bleibt immer exakt gleich.

Die Magie der Treiber (Typ 4)

Damit der neutrale Java-Code von der spezifischen Datenbank verstanden wird, schaltet man einen Treiber dazwischen. Dieser übersetzt das JDBC-SQL in das proprietäre DBMS-SQL. Es gibt 4 Treibertypen. In modernen Anwendungen (und in unseren Übungen für PostgreSQL) verwendet man fast ausschließlich den **Typ 4 Treiber** (Database-Protocol / Pure Java). Er ist komplett in Java geschrieben, plattformunabhängig und wandelt JDBC-Calls direkt in das Netzwerkprotokoll der jeweiligen Datenbank um.

Der eiserne 6-Schritte-Ablauf

Jedes klassische JDBC-Programm folgt gnadenlos dieser Architekturfolge:

1. **Laden des Treibers:** (`.jar` Datei im Projekt hinterlegen).
2. **Herstellen der Verbindung (Connection):** `Connection conn = DriverManager.getConnection(url, user, password);`
3. **Erzeugen eines Statement-Objekts:** `Statement st = conn.createStatement();`
4. **Ausführen der Anfrage:** Hier gibt es eine strikte Trennung:
    - _Für DQL (SELECT):_ `ResultSet rs = st.executeQuery("SELECT...");`
    - _Für DML/DDL (INSERT, UPDATE, CREATE):_ `int affectedRows = st.executeUpdate("UPDATE...");`
5. **Auswertung der Ergebnisse:** (Nur bei SELECT-Abfragen) Da Java objektorientiert arbeitet, die Datenbank aber Relationen (Tabellen) zurückliefert, nutzt JDBC ein **Cursor-Konzept**. Der Cursor zeigt auf eine Zeile. Mit `rs.next()` springt man in einer `while`-Schleife zur nächsten Zeile, bis keine mehr da ist (Rückgabe `false`). Innerhalb der Schleife liest man die Zellen mit z.B. `rs.getInt("genre_id")` aus.
6. **Schließen der Verbindung (Resource Management):** Zwingend erforderlich! `rs.close()`, `st.close()` und `conn.close()` müssen (meist in einem `finally` Block) aufgerufen werden, um Speicherlecks zu verhindern.

Sicherheit und Transaktionen

- **Transaktionen:** JDBC arbeitet standardmäßig im Auto-Commit-Modus. Für echte Transaktionen muss dieser über `conn.setAutoCommit(false)` deaktiviert werden. Danach steuert man manuell mit `conn.commit()` oder `conn.rollback()`.
- **Fehlerbehandlung:** Jeder JDBC-Call kann fehlschlagen (z.B. Verbindungsabbruch). Daher muss alles in einem `try-catch`-Block für die `SQLException` gekapselt werden.
- **Prepared Statements:** Normale `Statements` sind anfällig für **SQL Injections** (Hacker schmuggeln Schadcode über Benutzereingaben in den String, z.B. `OR 1=1`). `PreparedStatements` verhindern dies, indem sie Parameter vorkompilieren und validieren. Zudem sind sie performanter bei mehrfacher Ausführung.

---

### Flashcards

Was ist JDBC und welche Rolle spielt es als Abstraktionsschicht in der Java-Programmierung?
?
JDBC ist die Java-Implementierung des SQL/CLI-Standards und dient als Klassenbibliothek für den Zugriff auf SQL-Datenbanken. Als Abstraktionsschicht ermöglicht es Datenbankneutralität, sodass das zugrundeliegende DBMS ohne große Codeänderungen einfach ausgetauscht werden kann.

Nennen Sie die vier JDBC-Treibertypen. Welcher Typ wird im Rahmen der Vorlesung für den Zugriff auf PostgreSQL genutzt?
?
Die Typen sind: Typ 1 (JDBC-ODBC Bridge), Typ 2 (Native-API), Typ 3 (Middleware-Treiber) und Typ 4 (Pure Java / Database-Protocol). Im Kurs wird der **Typ 4 Treiber** genutzt, der JDBC-Calls direkt in das Protokoll der Datenbank umsetzt.

Erläutern Sie das Prinzip „Write Once, Run Anywhere“ im Kontext von JDBC.::Das Prinzip bedeutet, dass die Java-Anwendung unabhängig von der konkreten Datenbank implementiert werden kann. Der JDBC-Treiber transformiert das einheitliche JDBC-SQL automatisch in das jeweilige proprietäre DBMS-SQL. Der Code läuft somit mit jeder relationalen Datenbank, für die ein Standard-Treiber vorliegt.

Skizzieren Sie die typischen 6 Schritte eines JDBC-Programms vom Laden des Treibers bis zum Schließen der Verbindung.::1. Laden des Treibers, 2. Herstellen der Verbindung, 3. Erzeugen eines Statement-Objekts, 4. Ausführen der Anfrage/Updates, 5. Auswertung der Ergebnisse (bei Abfragen), 6. Schließen der Verbindung.

Wann verwendet man die Methode `executeQuery()` und wann `executeUpdate()`? Was ist der jeweilige Rückgabetyp?
?
`executeQuery()` wird für SELECT-Abfragen genutzt und liefert ein `ResultSet` (die Datensätze) zurück. `executeUpdate()` dient für DML- (INSERT, UPDATE, DELETE) oder DDL-Anweisungen und gibt die Anzahl der betroffenen Zeilen als Ganzzahl (`int`) zurück.

Erklären Sie das Cursor-Konzept beim Auswerten eines ResultSet. Wie navigiert man durch die Ergebnismenge?::Ein Cursor fungiert als Iterator über die Tupel der Ergebnismenge, um den Strukturkonflikt (Tabelle vs. Objekt) zu lösen. Mit der Methode `next()` springt man in einer Schleife zum jeweils nächsten Datensatz, bis das Ende der Tabelle erreicht ist (Rückgabe `false`).

Warum ist es wichtig, Objekte wie ResultSet, Statement und Connection explizit zu schließen (`close()`)?::Werden diese Ressourcen nicht manuell geschlossen, werden sie vom System nicht direkt freigegeben. Dies führt zu unnötigem Ressourcenverbrauch und Speicherlecks.

Wie lässt sich das Standardverhalten (Auto-Commit) in JDBC deaktivieren und wie schließt man eine Transaktion stattdessen manuell ab?::Mit `conn.setAutoCommit(false)` wird das automatische Commit deaktiviert. Manuelle Abschlüsse erfolgen danach über `conn.commit()` (bei Erfolg) oder im Fehlerfall über `conn.rollback()`.

Was versteht man unter „SQL Injection“ und wie kann bösartiger Code über einfache Statement-Abfragen in das System gelangen?::Bei einer SQL Injection wird die Logik eines SQL-Befehls durch manipulierte Benutzereingaben verändert (z. B. durch Anhängen von `OR 1=1`), um Filter zu umgehen oder unbefugten Zugriff auf Daten zu erhalten.

Warum gelten PreparedStatements als sicherer und performanter im Vergleich zu herkömmlichen Statement-Objekten?::**Sicherer:** Sie prüfen die Gültigkeit der Parameter vor der Verarbeitung und verhindern so SQL Injections. **Performanter:** Die Anfrage muss von der Datenbank nur einmal optimiert ("geparsed") werden und kann dann rasend schnell mehrfach mit verschiedenen Parametern ausgeführt werden.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[JDBC]]
SORT file.mtime DESC
```