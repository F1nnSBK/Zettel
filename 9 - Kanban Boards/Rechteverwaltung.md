#Note

2026-06-09

Tags: [[Datenbanksystem]], [[Relationale Datenbank]], [[SQL DDL]], [[Datenintegrität]], [[Projektmanagement]], [[Organistionsformen]], [[Qualitätsicherung]]
#datenbanken 

---
Die **Rechteverwaltung** (Data Control Language - DCL) regelt den Zugriff auf die Datenbankobjekte. Im Gegensatz zum reinen SQL-Standard (wie `SELECT` oder `JOIN`) weichen die Befehle hier bei verschiedenen Herstellern oft leicht voneinander ab, das Grundprinzip bleibt jedoch überall gleich.

Das wichtigste Leitmotiv beim Design der Sicherheitsarchitektur ist das **Prinzip der minimalen Rechte** (Least Privilege): Es wird nur Zugriff auf absolut relevante Daten gewährt.

1. Benutzerverwaltung (User)

Ein User repräsentiert eine Identität, die sich an der Datenbank anmeldet.

- **Erstellen:** `CREATE USER martin WITH PASSWORD '123456789';`
- **Die goldene Regel:** Neu erstellte User haben in einer relationalen Datenbank standardmäßig **keinerlei Rechte** – sie können sich einloggen, aber nichts sehen und nichts tun.
- **Löschen:** `DROP USER martin;`

2. Rechte vergeben und entziehen (GRANT & REVOKE)

Berechtigungen (wie `SELECT`, `INSERT`, `UPDATE`, `DELETE`, `CREATE` oder `ALL`) werden spezifisch auf Datenbankobjekte (z.B. Tabellen) angewendet. Man kann Rechte auch punktgenau nur auf einzelne Spalten vergeben (z.B. `GRANT SELECT (emp_first_name) ...`).

- **Rechte vergeben:** `GRANT <Berechtigung> ON <Objekt> TO <Nutzer/Rolle>;`
    - _Beispiel:_ `GRANT SELECT ON invoice TO martin;`
- **Rechte entziehen:** `REVOKE <Berechtigung> ON <Objekt> FROM <Nutzer/Rolle>;`
    - _Beispiel:_ `REVOKE SELECT ON emp_employee FROM martin;`

3. Best Practice: Rollenbasierte Zugriffskontrolle (RBAC)

Rechte direkt an einzelne User ("Benutzerbasierte Zugriffsrechte") zu vergeben, ist extrem risikobehaftet und wird bei wachsender Unternehmensgröße schnell unübersichtlich. Daher nutzt man **RBAC (Role Based Access Control)**:

1. Man erstellt logische Rollen (z.B. "Buchhaltung", "Support"): `CREATE ROLE buchhaltung;`. _(Auch neue Rollen haben zunächst keine Rechte__)._
2. Man gewährt der Rolle die nötigen Tabellenrechte: `GRANT SELECT ON invoice TO buchhaltung;`.
3. Man weist Usern diese Rolle zu: `GRANT buchhaltung TO martin;`. _Jeder User kann Mitglied in beliebig vielen Rollen sein, und jede Rolle kann beliebig viele Mitglieder haben__._

--------------------------------------------------------------------------------

Flashcards (Offizielle Wiederholungsfragen integriert)

Was fordert das "Prinzip der minimalen Rechte" (Least Privilege) in der Datenbank-Rechteverwaltung? :: Benutzern sollte immer nur der Zugriff auf die Daten gewährt werden, die für ihre aktuelle Rolle/Aufgabe absolut relevant sind.

Welchen Zustand bezüglich der Zugriffsrechte hat ein mit `CREATE USER` frisch erstellter Nutzer standardmäßig? :: Er hat standardmäßig keinerlei Rechte. Er kann auf keine Tabellen zugreifen, bis ihm diese explizit gewährt werden.

Mit welchem Befehl werden vergebene Berechtigungen auf eine Tabelle wieder entzogen? :: Mit dem Befehl `REVOKE` (z.B. `REVOKE SELECT ON tabelle FROM user;`).

Warum ist RBAC (Role Based Access Control) der benutzerbasierten Rechtevergabe konzeptionell weit überlegen? ? Weil benutzerbasierte Vergabe extrem unübersichtlich und fehleranfällig ist. Bei RBAC (Rollenbasiert) müssen Berechtigungen nicht jedem neuen User mühsam neu zugewiesen werden. Stattdessen werden neue Benutzer lediglich einer abstrakten Rolle (z.B. "Support") zugewiesen, die diese Rechte bereits zentral besitzt.

Welche drei SQL-Befehle (in korrekter Reihenfolge) sind nötig, um einem neuen Mitarbeiter "Martin" über das RBAC-Prinzip Leserechte auf die Tabelle "Rechnung" zu geben? ?

1. Erstellen der Rolle: `CREATE ROLE buchhaltung;`
2. Rechte an Rolle vergeben: `GRANT SELECT ON Rechnung TO buchhaltung;`
3. User der Rolle zuweisen: `GRANT buchhaltung TO martin;`


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Rechteverwaltung]]
SORT file.mtime DESC
```