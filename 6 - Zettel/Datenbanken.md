#Note

2026-06-12

Tags: [[Datenbanken]], [[Grundlagen]], [[Architektur]], [[Datenbanksystem]]
#datenbanken 

---
Um das weite Feld der Datenbanktechnologien (egal ob klassisch relational oder modern NoSQL) zu verstehen, müssen wir zunächst das Untersuchungsobjekt selbst definieren: **Die Daten**.

Die Informationspyramide (DIW)

Wir unterscheiden strikt zwischen drei Ebenen der Verarbeitung:

1. **Daten:** Sind reine Rohwerte, isolierte und völlig uninterpretierte Fakten und Kennwerte ohne jeglichen Kontext.
    - _Beispiel:_ Die Zahl "37" oder "Meier, 72076 Tübingen".
2. **Informationen:** Entstehen, wenn Daten interpretiert, verknüpft und in einen Kontext (Bedeutung / Semantik) gesetzt werden.
    - _Beispiel:_ "37 °C Temperatur" oder "Herr Meier wohnt in 72076 Tübingen".
3. **Wissen:** Ist die höchste Stufe. Von Wissen spricht man, wenn Informationen individuell verarbeitet, mit der eigenen Erfahrungswelt verknüpft und _für Entscheidungen_ nutzbar gemacht werden.
    - _Beispiel:_ "Bei 37 °C muss der Server gekühlt werden" oder "Mein alter Schulfreund Peter Meier wohnt hier".

Die Anatomie eines Datenbanksystems (DBS)

Der Begriff "Datenbank" wird im Alltag oft falsch verwendet. Fachlich müssen wir das **Datenbanksystem (DBS)** (die funktionale Gesamteinheit) in zwei strikt getrennte Kernkomponenten unterteilen:

1. **Die Datenbank (DB) - Speicherungskomponente:** Dies ist die rein logische Einheit zusammengehörender Daten samt ihrer Meta-Informationen (die organisierte Sammlung). Die Datenbank ist passiv.
2. **Das Datenbank-Management-System (DBMS) - Verwaltungskomponente:** Dies ist die aktive Software (die Werkzeuge), mit der die Datenbank erstellt, verwaltet und mit Daten gefüllt wird. Das DBMS enthält die Abfrage- und Manipulationssprache und ist für die Zugriffsrechte verantwortlich. Das DBMS ist der absolute Herrscher über die Hardware und hat folgende vier Hauptaufgaben:
    - **Exklusiver Datenzugriff:** Es ist die einzige Komponente, die direkt auf den physischen Speicher zugreift.
    - **Garant für Konsistenz & Integrität:** Es stellt sicher, dass Daten widerspruchsfrei und regelkonform bleiben.
    - **Zentrale Zugriffskontrolle:** Es agiert als "Türsteher", der Berechtigungen verwaltet.
    - **Transparente Hintergrundprozesse:** Es führt für den Nutzer unsichtbare Aufgaben wie Optimierung und Backups durch.

---

### Flashcards

Erklären Sie den konzeptionellen Unterschied zwischen "Daten", "Informationen" und "Wissen". ?
- **Daten** sind isolierte, uninterpretierte Rohwerte ohne Kontext (z.B. "37").
- **Informationen** sind Daten, die interpretiert, verknüpft und in einen bedeutungsvollen Kontext gesetzt wurden (z.B. "37 °C Temperatur").
- **Wissen** entsteht, wenn Informationen mit Erfahrungen vernetzt und als Grundlage für Entscheidungen genutzt werden (z.B. "Bei 37 °C muss der Server gekühlt werden").

Worin besteht der fachliche Unterschied zwischen einer Datenbank (DB), einem Datenbank-Management-System (DBMS) und einem Datenbanksystem (DBS)?
?
- Die **Datenbank (DB)** ist lediglich die logische, organisierte Sammlung der eigentlichen Daten und Meta-Informationen (die Speicherungskomponente).
- Das **DBMS** ist die Software, welche die Werkzeuge bereitstellt, um diese Daten abzufragen, zu sichern und zu verwalten (die Verwaltungskomponente).
- Das **Datenbanksystem (DBS)** ist der Überbegriff, der die funktionale Einheit aus beiden Teilen (Datenbank + DBMS) beschreibt.

Nennen Sie drei zentrale Systemaufgaben, die ein Datenbank-Management-System (DBMS) im Hintergrund übernimmt.
?
1. **Exklusiver Datenzugriff:** Es ist die einzige Komponente mit direktem Schreib-/Lesezugriff auf den physischen Speicher.
2. **Konsistenz und Integrität:** Es ist der Garant dafür, dass die Daten stets regelkonform und widerspruchsfrei bleiben.
3. **Zugriffskontrolle:** Es fungiert als "Türsteher", um Berechtigungen zu verwalten und unautorisierte Zugriffe abzuwehren.

Was besagen die Eigenschaften "Alter" und "Original" in Bezug auf Informationen (im Gegensatz zu materiellen Gütern)?::Informationen unterliegen keinem physikalischen Alterungsprozess und sie sind beliebig oft verlustfrei kopierbar, weshalb es das Konzept eines echten "Originals" (wie bei materiellen Objekten) in der digitalen Welt nicht gibt.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Datenbanken]]
SORT file.mtime DESC
```