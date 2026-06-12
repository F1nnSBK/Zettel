#Note

2026-06-12

Tags: [[Datenbanken]], [[Java]], [[JDBC]], [[Sicherheit]], [[Performance]]
#datenbanken 

---
Normale JDBC-`Statements` erfordern, dass man SQL-Befehle und Benutzereingaben als einen langen String zusammenkettet (z. B. `"... WHERE name = '" + eingabe + "'"`). Das öffnet Tür und Tor für Hacker, die durch Eingaben wie `' OR 1=1;` die Abfragelogik manipulieren (SQL Injection).

Die Lösung hierfür sind **Prepared Statements**.

Das 2-Stufen-Funktionsprinzip

Ein Prepared Statement arbeitet nach einem zweistufigen Prozess:

1. **Vorbereitung (Prepare):** Das SQL-Skelett wird mit Platzhaltern definiert, an die Datenbank geschickt, dort vorkompiliert und vom DBMS optimiert.
2. **Ausführung (Execute):** Die Platzhalter (formale Parameter) werden durch konkrete Werte ersetzt und die fertige Anweisung wird ausgeführt.

Syntax und Platzhalter (?)

Parameter werden in der Query immer mit einem Fragezeichen (`?`) gekennzeichnet. Diese Platzhalter werden anschließend über typspezifische Setter-Methoden (wie `setInt()` oder `setString()`) befüllt.

**Beispiel (aus der Vorlesung): UPDATE-Befehl mit Benutzereingabe**

```java
String eingabe = "'Blues' OR 1=1;"; // Bösartige Eingabe eines Nutzers

// 1. Statement vorbereiten (mit SQL-Skelett und Platzhalter)
PreparedStatement pst = conn.prepareStatement("UPDATE genre SET name = 'Blues Rock' WHERE name = ?"); [3]

// 2. Platzhalter befüllen: Für den 1. Parameter wird die "eingabe" übergeben
pst.setString(1, eingabe); [3]

// 3. SQL Befehl ausführen
pst.executeUpdate(); [3]
```

_(Im Gegensatz zu einem normalen Statement wird die bösartige Eingabe hier von der Datenbank strikt als reiner Textwert behandelt und nicht als ausführbarer SQL-Code ausgeführt. Es wird nach einem Genre gesucht, das exakt den seltsamen Namen_ _"'Blues' OR 1=1;"_ _trägt, wodurch die Injection wirkungslos verpufft.)_

Die zwei großen Eigenschaften (Vorteile)

1. **Sicherheit ([[SQL-Injection]] Schutz):** Parameter sind strikt von der Befehlslogik getrennt. Das System prüft die Gültigkeit der Daten vor der Verarbeitung – schädlicher Code wird als reiner Text behandelt.
2. **Performance:** Da das SQL-Skelett schon im Vorfeld geparst und vom DBMS optimiert wird, entfällt dieser Overhead bei mehrfacher Ausführung. Man kann den Befehl tausendmal mit anderen Werten in einer Schleife abfeuern, ohne dass die Datenbank jedes Mal neu über den Abfrageplan nachdenken muss.

---

### Flashcards

Warum gelten PreparedStatements als sicherer und performanter im Vergleich zu herkömmlichen Statement-Objekten?
?
**Sicherer:** Da Parameter strikt von der SQL-Logik getrennt sind, prüft die Datenbank die Gültigkeit der Parameter vor der Verarbeitung und behandelt schädlichen Code nur als Text. Das erschwert SQL Injections. **Performanter:** Die Anfrage muss nur einmal optimiert („geparsed“) werden und kann dann mehrfach mit verschiedenen Parametern rasend schnell ausgeführt werden, da der Abfrageplan bereits steht.

Mit welchem Zeichen werden die flexiblen Parameter in der SQL-Skelett-Query eines Prepared Statements markiert?::Mit einem Fragezeichen (`?`).

Wie funktioniert das zweistufige Prinzip eines Prepared Statements?
?
1. **Vorbereitung (Prepare):** Das SQL-Skelett wird deklariert, an das DBMS geschickt, dort vorkompiliert und optimiert.
2. **Ausführung (Execute):** Die Platzhalter werden durch konkrete, aktuelle Werte (z.B. per `setString()`) ersetzt und die Anweisung wird ausgeführt.

Mit welcher Methode wird ein Prepared Statement-Objekt aus der Connection (Verbindung) erzeugt?::Mit der Methode `conn.prepareStatement("SQL-String mit ?")` (im Gegensatz zu `conn.createStatement()` beim normalen Statement).


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Prepared Statement]]
SORT file.mtime DESC
```