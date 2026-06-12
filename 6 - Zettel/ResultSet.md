#Note

2026-06-12

Tags: [[Datenbanken]], [[Java]], [[JDBC]], [[ResultSet]], [[Cursor]]
#datenbanken 

---
Das **ResultSet** ist das zentrale Antwortobjekt, das man in JDBC erhält, wenn man eine DQL-Anweisung (ein `SELECT`) mittels der Methode `executeQuery()` an die Datenbank schickt.

Das fundamentale Problem: Der Strukturkonflikt

Wenn die Datenbank antwortet, liefert sie eine _Relation_ (eine Tabelle mit Spalten und Zeilen). Die Programmiersprache Java kennt dieses Konstrukt nativ nicht, sondern arbeitet objektorientiert. Diesen Konflikt der unterschiedlichen Datenstrukturen (Relation vs. Tupel) nennt man den Object-Relational Impedance Mismatch.

Die Lösung: Das Cursor-Konzept

Um diesen Konflikt zu lösen, nutzt JDBC einen **Cursor als Iterator**.

- Der Cursor ist ein Zeiger, der zunächst _vor_ der ersten Zeile der Ergebnismenge steht.
- Mit dem Aufruf der Methode `next()` wird der Cursor um genau einen Datensatz nach unten verschoben.
- Solange es einen weiteren Datensatz gibt, liefert `next()` den booleschen Wert `true` zurück. Ist das Ende der Tabelle erreicht, liefert es `false`.

Daher wird das ResultSet fast immer in einer `while`-Schleife ausgewertet:

```java
// SQL Befehl ausführen
ResultSet rs = st.executeQuery("SELECT * FROM chinook.genre;");

// Den Cursor Zeile für Zeile durch die Tabelle bewegen
while (rs.next()) {
    // Daten der aktuellen Zeile über Getter-Methoden auslesen
    Integer id = rs.getInt("genre_id");
    String name = rs.getString("name");
    
    // (Optional) Cursorposition ermitteln
    int pos = rs.getRow(); 
    
    System.out.println("ID: " + id + ", Name: " + name);
}
```



Ressourcenfreigabe (Extrem Wichtig!)

Datenbankverbindungen und Cursor sind native Systemressourcen (außerhalb des reinen Java-Arbeitsspeichers). Wenn man mit dem Auslesen fertig ist, müssen das ResultSet (`rs.close()`), das Statement (`st.close()`) und die Connection (`conn.close()`) **zwingend** manuell geschlossen werden. Geschieht dies nicht, werden die Ressourcen auf dem Datenbankserver nicht sofort freigegeben, was zu Speicherlecks ("Memory Leaks") und irgendwann zum kompletten Stillstand der Anwendung führt.

---

### Flashcards

Erklären Sie das Cursor-Konzept beim Auswerten eines ResultSet. Wie navigiert man durch die Ergebnismenge?
?
Ein Cursor fungiert als Iterator über die Tupel (Zeilen) der Ergebnismenge. Er löst den Strukturkonflikt (Relation vs. Tupel) zwischen SQL und der Programmiersprache. Mit der Methode `next()` springt man in einer Schleife zum jeweils nächsten Datensatz, bis das Ende der Tabelle erreicht ist (die Methode gibt dann `false` zurück).

Mit welcher JDBC-Methode wird ein SQL-Befehl ausgeführt, um überhaupt ein ResultSet zu erzeugen?::Mit der Methode `executeQuery()` (welche zwingend eine `SELECT`-Anweisung voraussetzt).

Wie liest man innerhalb einer `while(rs.next())`-Schleife die konkreten Werte aus der aktuellen Zeile des ResultSets aus?::Durch typspezifische Getter-Methoden (wie z. B. `rs.getInt("spaltenname")` oder `rs.getString("spaltenname")`), die als Parameter entweder den Spaltennamen oder die Spaltennummer erhalten.

Warum ist es wichtig, Objekte wie ResultSet, Statement und Connection nach der Nutzung explizit zu schließen (`close()`)?::Werden diese Ressourcen nicht manuell geschlossen, werden sie vom System nicht direkt freigegeben. Dies führt zu einem unnötigen Ressourcenverbrauch (blockierte Verbindungen auf dem Datenbankserver) und potenziellen Speicherlecks.

Welchen SQL-Befehlen ist die Rückgabe eines ResultSets strikt vorbehalten, und was liefern die anderen Befehle (INSERT, UPDATE) stattdessen zurück?::Nur `SELECT`-Anfragen (`executeQuery()`) liefern ein ResultSet zurück. DML- und DDL-Anweisungen (ausgeführt mit `executeUpdate()`) liefern stattdessen einen Integer-Wert zurück, der die Anzahl der betroffenen Zeilen angibt.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[ResultSet]]
SORT file.mtime DESC
```