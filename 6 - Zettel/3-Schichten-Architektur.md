#Note

2026-06-12

Tags: [[Datenbanken]], [[Softwarearchitektur]], [[Backend]], [[REST]], [[JDBC]]
#datenbanken 

---
Die **3-Schichten-Architektur** ist das dominierende Design-Pattern für moderne, skalierbare Web- und Enterprise-Anwendungen. Anstatt eine monolithische Software zu schreiben, die direkt auf Festplatten zugreift, wird das System in drei isolierte, hochspezialisierte Bereiche (Tiers) unterteilt, die sich gegenseitig nur über Schnittstellen kennen.

Dies führt zu klaren Verantwortlichkeiten, besserer Wartbarkeit, massiv erhöhter Sicherheit und guter Skalierbarkeit.

Die 3 Schichten im Detail

1. Präsentationsschicht (Client / Frontend)

Hier interagiert der Endnutzer mit dem System.

- **Beispiele:** Webbrowser (HTML/JS), Mobile App (iOS/Android), Desktop-Client.
- **Aufgaben:** Darstellung der Daten (User Interface), Entgegennehmen von Benutzereingaben, Senden von HTTP/REST-Anfragen an das Backend.
- **Eiserne Regel:** Diese Schicht enthält **kein SQL** und besitzt absolut **keine Datenbankzugangsdaten**! Würde der Client direkt mit der Datenbank sprechen, hätte jeder App-Nutzer potenziell Vollzugriff auf alle Daten.

2. Anwendungsschicht (Backend / Business Logic)

Das Gehirn der Software. Clients greifen ausschließlich über eine REST-API auf das Backend zu, und nur das Backend greift auf die Datenbank zu.

- **Beispiele:** Java-Server (Spring Boot, Jakarta EE).
- **Aufgaben:** Ausführen der Kern-Geschäftslogik, Validierung der Daten, Durchsetzen von Geschäftsregeln, Sicherheit (Login/Autorisierung/Rollen) und die Transaktionssteuerung.
- **Technologien:** REST/HTTP (Richtung Client) und JDBC/JPA (Richtung Datenbank).

3. Datenschicht (Datenbank / Persistenz)

Der sichere Tresor am Ende der Kette.

- **Beispiele:** PostgreSQL, Oracle, SAP HANA, MongoDB.
- **Aufgaben:** Persistente Speicherung der Daten, Sicherstellung der Datenintegrität, Garantie von ACID-Transaktionen und optimierte physische Abfragen.

---

### Flashcards

Nennen Sie die drei Schichten der modernen Anwendungsarchitektur und ordnen Sie die „Geschäftslogik“ der korrekten Schicht zu.
?
1. Präsentationsschicht (Client)
2. Anwendungsschicht (Backend)
3. Datenschicht (Datenbank) Die „Geschäftslogik“ gehört architektonisch zwingend in die **Anwendungsschicht** (das Backend).

Nenne zwei absolute No-Gos (Sicherheitsrisiken) bezüglich der Präsentationsschicht (Client) in einer 3-Schichten-Architektur.::Die Präsentationsschicht darf niemals direkten SQL-Code ausführen und darf niemals Datenbankzugangsdaten (Credentials) enthalten.

Wie kommunizieren die drei Schichten untereinander (Schnittstellen)?::Die Präsentationsschicht kommuniziert mit der Anwendungsschicht typischerweise über Web-Protokolle (z. B. HTTP/REST). Die Anwendungsschicht kommuniziert mit der Datenschicht über spezialisierte Datenbanktreiber oder APIs (z. B. JDBC, JPA, Hibernate).

Nenne drei wesentliche Vorteile, die eine strikte Trennung in drei Schichten für die Softwareentwicklung mit sich bringt.::1. Klare Verantwortlichkeiten, 2. Bessere Wartbarkeit/Austauschbarkeit einzelner Schichten, 3. Höhere Sicherheit (da die Datenbank vom Internet abgeschirmt hinter dem Backend liegt), 4. Gute Skalierbarkeit.

Was ist der Unterschied bezüglich der Transaktionssteuerung zwischen der Anwendungsschicht und der Datenschicht?::Die Datenschicht (Datenbank) führt die physischen ACID-Transaktionen aus und sichert sie ab. Die Anwendungsschicht (Backend) _steuert_ diese jedoch logisch (z.B. indem sie in Java bestimmt, wann `commit()` oder `rollback()` aufgerufen wird).


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[3-Schichten-Architektur]]
SORT file.mtime DESC
```