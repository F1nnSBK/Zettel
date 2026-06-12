#Note

2026-06-12

Tags: [[Datenbanken]], [[Historisch]], [[IMS]], [[CODASYL]], [[Architektur]]
#datenbanken 

---
Vor der Einführung des relationalen Modells dominierten zwei nicht-relationale Konzepte den Markt, bei denen Daten in Knoten (Records) gespeichert und explizit miteinander verbunden wurden. Der Zugriff erfolgte bei beiden Systemen "navigierend" (durch Programmierung von Suchwegen). Auch nach dem Siegeszug von SQL wurden solche Ansätze in Nischen (z.B. CAD-Anwendungen) weiterhin genutzt.

1. Hierarchische Datenbanken (z. B. IBMs IMS)

Dieses Modell strukturiert Daten wie einen echten Baum.

- **Die Struktur:** Es gibt ein baumorientiertes Datenmodell, das ausschließlich **1:n-Beziehungen** zulässt.
- **Parent-Child-Prinzip:** Ein "Child-Record" (im IMS-Jargon auch "Segment" genannt) ist existenziell von seinem Vater abhängig. Es kann nur existieren, wenn der zugehörige "Parent" existiert.
- **Die Verbindung:** Die Relation zwischen Parent und Child wird explizit durch physische Verknüpfungen (Pointer) hergestellt, nicht logisch über übereinstimmende Werte (wie bei Fremdschlüsseln in SQL).
- **Nachteil:** Die Abfragesprache war sehr kryptisch und stark an die physische Programmierung gebunden.

2. Netzwerk-Datenbanken (CODASYL)

Weil das Baummodell bei komplexen Geschäftsdaten (wie Studenten, die mehrere Kurse besuchen) schnell an Grenzen stieß, wurde das Netzwerkmodell entwickelt und von der _CODASYL_-Gruppe normiert.

- **Die Struktur:** Das Modell bricht den strengen Baum auf und erlaubt echte **n:m-Beziehungen**. Durch die direkten Verbindungen der Knoten untereinander entsteht ein echtes Netz.
- **RECORD und SET:** Die Architektur basiert auf zwei Komponenten:
    - **RECORD:** Der eigentliche Datensatz (Knoten), bestehend aus Feldern und Wiederholungsgruppen.
    - **SET:** Definiert eine "Owner-Member"-Beziehung (Vater und Sohn).
- **Der Vorteil:** Jeder Record-Typ kann Owner oder Member in beliebig vielen Sets sein, d.h. ein Record kann mehrere Vorgänger haben. Dadurch existieren meist unterschiedliche, flexible Suchwege, um an einen gewünschten Datensatz zu gelangen.

---

### Flashcards

Welche beiden nicht-relationalen Datenbankmodelle existierten auf dem Markt, bevor Ted Codd das relationale Modell definierte?::Hierarchische Datenbanken (z. B. IMS) und netzwerkartige Datenbanken (z. B. CODASYL).

Wie unterschied sich der Datenzugriff in historischen Datenbanken fundamental von modernen deklarativen SQL-Abfragen?::Der Zugriff erfolgte "navigierend". Das bedeutet, der Programmierer musste den Suchweg durch die Datenstruktur (den Baum oder das Netz) explizit im Programmcode vorgeben.

Was ist das zentrale strukturelle Merkmal (und gleichzeitig die größte Einschränkung) eines hierarchischen Datenbanksystems wie IMS?::Es nutzt ein baumorientiertes Datenmodell, das architektonisch strikt auf 1:n-Beziehungen eingeschränkt ist. Ein "Child-Record" kann dabei nur existieren, wenn sein "Parent" existiert.

Welche fundamentale Verbesserung brachte das Netzwerk-Datenbankmodell gegenüber dem hierarchischen Modell?::Das Netzwerkmodell erlaubte **n:m-Beziehungen**. Da ein Record (Datensatz) mehrere Vorgänger haben konnte (als Member in verschiedenen Sets), entstand ein Netz mit unterschiedlichen Suchwegen anstelle eines starren Baumes.

Aus welchen zwei zentralen Strukturkomponenten besteht eine Netzwerk-Datenbank nach dem CODASYL-Standard?::Aus dem **RECORD** (dem eigentlichen Knoten mit Feldern) und dem **SET** (der Definition einer Owner-Member-Beziehung zwischen "Vater" und "Sohn").

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Historische Datenbankkonzepte]]
SORT file.mtime DESC
```