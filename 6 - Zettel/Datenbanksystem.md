#Note

2026-06-09

Tags: [[Datenbanken]], [[Grundlagen]], [[Architektur]]
#datenbanken 

---
Ein **Datenbanksystem (DBS)** ist eine Software zur applikationsunabhängigen Beschreibung, Speicherung und Abfrage von Daten. Es stellt in der betrieblichen Praxis die Brücke zwischen der physischen Speicherung auf der Hardware und den Anfragen der Nutzer oder Applikationen dar.

Ein DBS ist konzeptionell zwingend zweigeteilt:

1. **Datenbank (DB) / Speicherungskomponente:** Eine logische Einheit zusammengehörender Nutzdaten sowie sämtlicher Meta-Informationen (Systemkatalog/Information Schema) dazu.
2. **Datenbank-Management-System (DBMS) / Verwaltungskomponente:** Die Software, die Werkzeuge bereitstellt, um Datenbanken zu erstellen, mit Daten zu füllen und zu verwalten. _(Beispiel: Die PostgreSQL-Installation auf einem Server)_

#### Kernaufgaben des DBMS

Das DBMS ist die alleinige Instanz, die direkt auf die Daten zugreifen darf. Es übernimmt als "Gatekeeper" überlebenswichtige Systemaufgaben für den sicheren Betrieb:

| Aufgabe                           | Beschreibung                                                                                                                  |
| --------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| **Exklusiver Datenzugriff**       | Das DBMS ist die einzige Komponente mit direktem Zugriff auf den physischen Speicher.                                         |
| **Konsistenz & Integrität**       | Stellt sicher, dass die Daten jederzeit regelkonform, korrekt und widerspruchsfrei bleiben (semantische Integrität).          |
| **Zugriffskontrolle (Türsteher)** | Verwaltung von Berechtigungen (Autorisierung); blockiert unautorisierte Zugriffe und verhindert Systemkonflikte.              |
| **Mehrbenutzer-Synchronisation**  | Koordination gleichzeitiger Zugriffe, um Anomalien und Datenverlust zu vermeiden (Sicherstellung der **ACID**-Eigenschaften). |
| **Transparente Prozesse**         | Ressourcen-Optimierung, Backup, und Transaktions-Logging laufen unsichtbar im Hintergrund ab.                                 |

Das DBMS stellt den Nutzern und Anwendungen dafür spezifische Datenbanksprachen zur Verfügung (insbesondere **DDL** zur Strukturdefinition und **DML** zur Datenmanipulation).

--------------------------------------------------------------------------------

### Flashcards

Woraus setzt sich ein Datenbanksystem (DBS) formal zusammen?::Aus der Datenbank (logische Datenmenge / Speicherungskomponente) und dem Datenbank-Management-System (verwaltende Software).
<!--SR:!2026-06-10,0,230-->

Was ist der Unterschied zwischen einer Datenbank (DB) und einem Datenbank-Management-System (DBMS)?::Die DB ist der strukturierte Datentopf inkl. Metadaten. Das DBMS ist die aktive Software (z.B. der PostgreSQL-Serverprozess), welche die Datenbanken verwaltet, Anfragen entgegennimmt und Schreibvorgänge physisch ausführt.

Welche Rolle übernimmt das DBMS bei der Zugriffskontrolle?
?
Das DBMS fungiert als "Türsteher". Es besitzt den exklusiven, einzigen direkten Zugriff auf den physischen Speicher. Jede Applikation und jeder Nutzer muss zwingend über das DBMS gehen, welches dann die Berechtigungen (Autorisierung) prüft und Systemkonflikte verhindert.
<!--SR:!2026-06-10,0,230-->

Warum ist die Koordination von Mehrbenutzerzugriffen (Concurrency) eine Kernanforderung an ein DBMS?
?
Da in einem Informationssystem oft hunderte Prozesse gleichzeitig lesen und schreiben wollen, muss das DBMS diese Zugriffe synchronisieren, um Inkonsistenzen (z.B. Lost Updates) zu vermeiden. In relationalen Datenbanken wird dies durch die Einhaltung der ACID-Eigenschaften garantiert.
<!--SR:!2026-06-11,1,230-->


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Datenbanksystem]]
SORT file.mtime DESC
```