#Note

2026-06-09

Tags: [[Datenbanken]], [[Datenbankentwurf]], [[Constraints]], [[Entität]], [[Datenbanksystem]]
#datenbanken 

---
Die **Datenintegrität** stellt die fehlerfreie, korrekte und widerspruchsfreie Speicherung von Daten sicher. Während die _Konsistenz_ den fehlerfreien Zustand der Datenbank beschreibt, ist die _Integrität_ das zugrundeliegende Regelwerk (die Constraints), das diesen Zustand erzwingt.

Die Überwachung dieser Regeln übernimmt das Datenbank-Management-System (DBMS) bei jeder einzelnen Einfüge-, Änderungs- oder Löschoperation völlig automatisch.

Man unterscheidet vier Ebenen der Integrität:

1. Domain-Integrität (Wertebereichsintegrität)

Stellt sicher, dass die Werte innerhalb einer einzelnen Spalte (Attribut) zulässig und sinnvoll sind.

- **Mechanismen:** Festlegung des Datentyps (z.B. `INT`), Vorgabe von Standardwerten (`DEFAULT`), Pflichtfelder (`NOT NULL`) und logische Wertebereichsgrenzen (`CHECK`).
- **Praxis-Beispiel (CHECK & NOT NULL):** Wir legen fest, dass das Alter eines Mitarbeiters immer angegeben werden muss und mindestens 18 sein muss: `emp_age INTEGER NOT NULL CHECK (emp_age >= 18)`

2. Entity-Integrität (Intra-relationale Integrität)

Stellt sicher, dass jede Zeile (Tupel) einer Tabelle absolut eindeutig identifizierbar ist.

- **Mechanismen:** Jede Relation muss zwingend einen Primärschlüssel (`PRIMARY KEY`) besitzen. Kein Teil dieses Schlüssels darf leer (`NULL`) sein, und der Wert darf nicht doppelt vorkommen.
- **Praxis-Beispiel:** Zwei Studenten dürfen nicht dieselbe Matrikelnummer haben.

3. Referentielle Integrität

Überwacht die Korrektheit der Beziehungen _zwischen_ zwei Tabellen. Ein Fremdschlüssel (Foreign Key) in einer Detailtabelle muss immer auf einen real existierenden Primärschlüssel in der Haupttabelle verweisen (oder er muss `NULL` sein).

- **Das Problem:** Was passiert mit den Angestellten, wenn die Abteilung (Haupttabelle), der sie zugeordnet sind, gelöscht wird?
- **Verfahren (Lösch- und Änderungsregeln):**
    - **RESTRICT / NO ACTION:** Das DBMS blockiert den Löschvorgang der Abteilung mit einem Fehler, solange dort noch Mitarbeiter arbeiten.
    - **CASCADE:** Löscht man die Abteilung, löscht das DBMS vollautomatisch auch alle Mitarbeiter dieser Abteilung (Kaskadierung).
    - **SET NULL:** Löscht man die Abteilung, bleiben die Mitarbeiter erhalten, aber ihr Abteilungs-Fremdschlüssel wird auf `NULL` (abteilungslos) gesetzt.

4. Benutzerdefinierte Integrität

Dies sind sehr spezifische, oft komplexe Geschäftsregeln, die sich nicht einfach durch die Standard-Constraints abbilden lassen.

- **Mechanismus:** Da sie oft anwendungsbezogen sind, werden sie entweder direkt im Code der Applikation (Backend) oder über datenbankinterne Programme (z.B. Trigger oder Stored Procedures) realisiert.

--------------------------------------------------------------------------------

### Flashcards

Was ist der Unterschied zwischen Datenintegrität und Datenkonsistenz?
?
Die **Integrität** ist die Ursache: Sie definiert die Regeln und Mechanismen (Constraints) beim [[Datenbankentwurf]]. Die **Konsistenz** ist das Ergebnis: Der fehlerfreie, widerspruchslose Zustand der Daten zur Laufzeit, weil die Integritätsregeln eingehalten werden.

Was stellt die Domain-Integrität (Wertebereichsintegrität) sicher und wie wird sie in SQL umgesetzt?
?
Sie sichert die Korrektheit der Werte innerhalb einer einzelnen Spalte. Umgesetzt wird sie durch Datentypen, `NOT NULL` (Pflichtfelder), `DEFAULT` (Standardwerte) und `CHECK`-Constraints (z.B. `Alter >= 18`).

Was besagt die Entity-Integrität?::Dass jede Zeile in einer Tabelle absolut eindeutig identifizierbar sein muss. Es muss einen Primärschlüssel geben, dieser darf nicht doppelt vorkommen und nicht `NULL` sein.

Welche fundamentale Regel beschreibt die Referentielle Integrität?::Ein Fremdschlüssel (Foreign Key) in einer Tabelle muss immer auf einen existierenden Primärschlüsselwert in der referenzierten Haupttabelle verweisen (oder er darf `NULL` sein). Es darf keine "verwaisten" Verweise geben.

Was passiert bei einer 1:n-Beziehung, wenn für den Fremdschlüssel `ON DELETE RESTRICT` (bzw. `NO ACTION`) definiert wurde und der Master-Datensatz gelöscht werden soll?::Das DBMS verhindert das Löschen des Master-Datensatzes und wirft einen Fehler, solange noch Detail-Datensätze existieren, die auf ihn verweisen.

Was passiert bei `ON DELETE CASCADE`?::Wenn der referenzierte Master-Datensatz gelöscht wird, löscht das DBMS vollautomatisch auch alle abhängigen Detail-Datensätze (kaskadierendes Löschen).

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Datenintegrität]]
SORT file.mtime DESC
```