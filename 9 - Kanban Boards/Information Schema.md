#Note

2026-06-09

Tags: [[Datenbanksystem]], [[Relationale Datenbank]], [[SQL DDL]], [[Datenbankentwurf]], [[Attribut]]
#datenbanken 

---
Das **Information Schema** (oft auch als Systemkatalog oder Data Dictionary bezeichnet) ist der Ort, an dem ein relationales Datenbankmanagementsystem (RDBMS) seine eigenen Verwaltungsdaten ablegt.

Es speichert die sogenannten **Metadaten**. Das sind beispielsweise Informationen über alle existierenden Tabellen, die darin enthaltenen Spalten, definierte Integritätsbedingungen (Constraints) und die Zugriffsrechte der Datenbank.

Die Genialität des Systemkatalogs

Das architektonisch Besondere an diesem Katalog ist, dass das RDBMS diese Verwaltungsdaten nicht in irgendwelchen kryptischen, unlesbaren Konfigurationsdateien speichert, sondern als **reguläre relationale Tabellen**. Das bedeutet, dass Entwickler und Administratoren das System mit genau denselben `SELECT`-Befehlen abfragen können, die sie auch für normale Nutzerdaten verwenden.

Standardisierung: ISO vs. Herstellerspezifisch

Mit der Norm SQL2 (SQL-92) wurden diese Verwaltungsdaten standardisiert. Jede normgerechte Datenbank enthält ein vordefiniertes Schema mit dem exakten Namen `information_schema`. Da es sich um einen ISO-Standard handelt, sind die Abfragen gegen dieses Schema systemübergreifend fast identisch, egal ob man Microsoft SQL Server, MySQL oder PostgreSQL verwendet.

Gleichzeitig besitzt jedes Datenbanksystem noch einen eigenen, tiefergehenden Katalog, dessen Implementierung von der Datenbank abhängig ist (bei PostgreSQL sind das beispielsweise die `pg_*` Tabellen wie `pg_attribute`). Diese sind jedoch streng proprietär und funktionieren bei einem Datenbankwechsel nicht mehr.

Code-Implementation: Den Katalog abfragen

Hier sind einige klassische DQL-Abfragen gegen den Systemkatalog:

```sql
-- Alle Tabellen der gesamten Datenbank auflisten
SELECT * FROM information_schema.tables; 

-- Welche Tabellen gibt es spezifisch in unserem Schema 'chinook'?
SELECT * FROM information_schema.tables 
WHERE table_schema = 'chinook';

-- Hersteller-spezifische Abfrage (nur PostgreSQL): 
-- Suche nach allen Attributen mit dem Namen 'billing_country'
SELECT * FROM pg_attribute 
WHERE attname LIKE 'billing_country';
```


---

### Flashcards

Was speichert ein relationales Datenbankmanagementsystem (RDBMS) in seinem Systemkatalog?::Es speichert dort die Metadaten. Das sind Verwaltungsinformationen über das System selbst, wie z.B. Informationen über alle Tabellen, Spalten, Constraints und Zugriffsrechte.

In welcher architektonischen Form liegen die Verwaltungsinformationen im Systemkatalog vor und wie greift man darauf zu?::Sie liegen als reguläre relationale Tabellen vor und können mit ganz normalen SQL-Abfragen (`SELECT`) ausgelesen werden.

Was ist das `Information_Schema` und welchen konkreten Vorteil bietet es gegenüber datenbankspezifischen Systemtabellen (wie z. B. `pg_*` in PostgreSQL)?
?
Das `Information_Schema` ist ein ISO-Standard für Verwaltungsdaten (Metadaten). Der entscheidende Vorteil ist, dass es systemübergreifend fast identisch ist (z. B. in SQL Server, MySQL und PostgreSQL). Herstellerspezifische Tabellen wie `pg_*` sind hingegen an PostgreSQL gebunden und würden bei einer Migration auf eine andere Datenbank abbrechen.

Wann wurde das `Information_Schema` standardisiert?::Mit der Norm SQL2 (im Jahr 1992).

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Information Schema]]
SORT file.mtime DESC
```