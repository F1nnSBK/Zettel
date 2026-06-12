#Note

2026-06-12

Tags: [[Datenbanken]], [[Sicherheit]], [[SQL Injection]], [[Hacking]], [[JDBC]]
#datenbanken 

---
Die **SQL-Injection** (SQL-Einschleusung) ist eine der bekanntesten und gefährlichsten Angriffsmethoden auf datenbankgestützte Webanwendungen. Sie passiert, wenn bösartiger Code über Eingabefelder einer Benutzeroberfläche in die SQL-Query gelangt, weil der SQL-Befehl im Backend durch einfache String-Verkettung (Konkatenation) zusammengebaut wird.

Die Anatomie des Angriffs (Beispiel)

Nehmen wir an, wir nutzen ein reguläres JDBC `Statement` und wollen ein Genre über eine Nutzeingabe aktualisieren.

**Der fehlerhafte Java-Code des Entwicklers:**

```java
String stcommand = "UPDATE genre SET name = 'Blues Rock' WHERE name = " + eingabe;
```

**Der Angriff:** Der normale Benutzer würde vielleicht `'Blues'` eingeben. Ein Angreifer emuliert jedoch folgende Eingabe:

```java
String eingabe = "'Blues' OR 1=1;";
```

**Das fatale Resultat:** Das Java-Programm fügt die Strings zusammen und schickt folgenden, völlig validen SQL-Befehl an die Datenbank:

```sql
UPDATE genre SET name = 'Blues Rock' WHERE name = 'Blues' OR 1=1;
```

Da die Bedingung `1=1` eine mathematische Tautologie (immer wahr) ist, wird die `WHERE`-Klausel für **alle** Datensätze der Tabelle erfüllt. Im Ergebnis ändert dieser Befehl die Namen aller Genres in der gesamten Tabelle in 'Blues Rock', was zu einem massiven Datenverlust führt.

Die Lösung

Die Lösung zur Verhinderung einer SQL-Injection ist die konsequente Nutzung von **Prepared Statements**. Da diese das SQL-Skelett und die Parameter strikt trennen, validiert die Datenbank den injizierten Code nicht als auszuführende Befehle (`OR 1=1`), sondern behandelt ihn als harmlosen Text. (Die Datenbank sucht dann nach einem Genre, das wörtlich `"'Blues' OR 1=1;"` heißt, und der Angriff verpufft wirkungslos).

**WICHTIGER RECHTLICHER HINWEIS** Das Ausprobieren von SQL-Injection auf fremden Seiten ist kein Kavaliersdelikt! Es ist strafbar nach **§ 202a des Strafgesetzbuches (Ausspähen von Daten)**. Wer unbefugt Zugangsmechanismen überwindet, um an fremde Daten zu gelangen, wird mit einer Freiheitsstrafe bis zu drei Jahren oder mit Geldstrafe bestraft.

---

### Flashcards

Sicherheit: Was versteht man unter „SQL Injection“ und wie kann bösartiger Code über einfache Statement-Abfragen in das System gelangen?
?
Bei einer SQL-Injection wird die Logik eines SQL-Befehls durch manipulierte Benutzereingaben verändert. Dies geschieht, wenn Eingaben aus einer Benutzeroberfläche ungeprüft (z.B. durch einfache String-Verkettung) in einen SQL-Code übernommen werden. Angreifer hängen beispielsweise logische Konstrukte wie `OR 1=1` an, um Filter zu umgehen oder unbefugten Zugriff auf Daten zu erhalten.

Was passiert bei dem Befehl `UPDATE genre SET name = 'Blues Rock' WHERE name = 'Blues' OR 1=1;` und warum ist das so gefährlich?::Da die logische Bedingung `1=1` immer wahr ist, greift die `WHERE`-Klausel nicht mehr nur für 'Blues', sondern für ausnahmslos jeden Datensatz. Im Ergebnis werden die Namen aller existierenden Datensätze der Tabelle unwiderruflich überschrieben.

Warum gelten `Prepared Statements` als das effektivste Mittel gegen SQL-Injections?::Weil sie die Programm-Logik (das SQL-Skelett) strikt von den Benutzerdaten trennen. Das Datenbanksystem prüft die Gültigkeit der Parameter vor der Verarbeitung und behandelt schädlichen injizierten Code ausschließlich als harmlosen Textwert, der nicht ausgeführt werden kann.

Ist das Testen von SQL-Injections auf einer fremden Website legal, solange man keine Daten stiehlt oder zerstört?::Nein! Das reine Ausprobieren und Überwinden der Zugangssicherung ist nach **§ 202a StGB (Ausspähen von Daten)** strafbar und kann mit bis zu drei Jahren Freiheitsstrafe oder Geldstrafe geahndet werden.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[SQL-Injection]]
SORT file.mtime DESC
```