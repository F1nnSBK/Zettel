#Note

2026-06-12

Tags: [[Datenbanken]], [[Softwarearchitektur]], [[REST]], [[API]], [[Backend]]
#datenbanken

---
In modernen Softwarelandschaften erfolgt der Datenzugriff fast nie direkt. Früher (in der klassischen Client-Server-Zeit) formulierte die Java-Anwendung auf dem PC des Nutzers noch selbst den SQL-Code und feuerte ihn über JDBC direkt an die relationale Datenbank.

Dieser direkte Zugriff ist aus Sicherheits- und Wartungsgründen heute ein absolutes Anti-Pattern.

Das REST-Prinzip (Die moderne Alternative)

Anstatt direkt mit der Datenbank zu sprechen, wendet sich der Client (z. B. ein Webbrowser oder eine Mobile App) an einen Webservice (das Backend). Dieser Webservice implementiert das Architekturprinzip **REST** (Representational State Transfer).

Die Kommunikation über REST zeichnet sich durch folgende Merkmale aus:

1. **Das Protokoll:** Die Kommunikation erfolgt rein über das Internetprotokoll HTTP.
2. **Die Adressierung:** Daten werden als "Ressourcen" betrachtet, die über eindeutige URLs angesprochen werden (z. B. `/api/personen/1`).
3. **Die Aktionen (HTTP-Verben):** Anstelle von SQL-Befehlen (`SELECT`, `INSERT`, `UPDATE`, `DELETE`) nutzt der Client Standard-HTTP-Methoden:
    - **GET:** Ressourcen abfragen (Lesen).
    - **POST:** Neue Ressourcen erstellen.
    - **PUT:** Bestehende Ressourcen komplett aktualisieren.
    - **DELETE:** Ressourcen löschen.
4. **Das Format:** Der Datenaustausch zwischen Client und Backend erfolgt zumeist im maschinenlesbaren **JSON-Format** (JavaScript Object Notation).

**Architektur-Vorteil:** SQL ist nun vollständig im Backend gekapselt. Der Client muss (und darf) nicht wissen, ob im Hintergrund eine Oracle-, PostgreSQL- oder sogar eine NoSQL-Datenbank läuft.

---

### Flashcards

Wie unterscheidet sich der moderne Datenzugriff über einen Webservice (REST) architektonisch vom klassischen direkten Zugriff über JDBC?
?
Beim klassischen Zugriff kommuniziert die Anwendung (der Client) direkt via JDBC mit der Datenbank und formuliert den SQL-Code selbst. Bei REST erfolgt der Zugriff über ein Backend (Webservice) via HTTP; der Client nutzt nur Methoden wie GET oder POST, während die eigentliche SQL-Logik sicher im Backend gekapselt ist.

Wofür steht die Abkürzung REST und über welches Netzwerkprotokoll läuft diese Art der Kommunikation primär ab?::REST steht für **Representational State Transfer**. Die Kommunikation erfolgt primär über das **HTTP**-Protokoll.

Welche vier Standardmethoden (HTTP-Verben) werden in einer REST-API typischerweise verwendet, um das Datenbank-Konzept von CRUD (Create, Read, Update, Delete) über das Web abzubilden?::GET (Lesen), POST (Erstellen), PUT (Aktualisieren), DELETE (Löschen).

In welchem Datenformat werden strukturierte Informationen (wie z. B. die Antwort auf eine Anfrage nach Kundendaten) bei REST-Schnittstellen heutzutage standardmäßig übertragen?::Im **JSON**-Format (JavaScript Object Notation).


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[REST]]
SORT file.mtime DESC
```