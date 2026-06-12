#Note

2026-06-12

Tags: [[Datenbanken]], [[NoSQL]], [[Polystore]], [[Architektur]], [[Big Data]]
#datenbanken 

---
**Polystores** (und Multi-Model-Datenbanken) sind die architektonische Antwort auf die Erkenntnis: **"One Size Does Not Fit All"**. Keine existierende Datenbank-Technologie ist in der Lage, alle Anforderungen von modernen Big-Data-Anwendungen (hochgradig vernetzt, unstrukturiert, rasend schnell und absolut fehlerfrei) gleichzeitig in Perfektion zu lösen.

Anstatt also Kompromisse einzugehen, integrieren Polystores mehrere spezialisierte Datensilos (Best of Breed) und stellen nach außen hin eine gemeinsame Abfrageschnittstelle zur Verfügung.

Das Paradebeispiel: E-Commerce-Architektur

Ein moderner Online-Shop würde seine Architektur im Polystore wie folgt aufteilen:

1. **Kundendaten & Bestellungen:** Werden in einer **Relationalen DB** gespeichert, da hier kein Verlust toleriert wird und zwingend harte ACID-Transaktionen benötigt werden.
2. **Produktkatalog:** Wird in einer **Dokumenten-DB** (z. B. MongoDB) abgelegt, da Produkte stark variable Attribute besitzen und das JSON-Format hier extreme Flexibilität (Schemafreiheit) bietet.
3. **Empfehlungslogik ("Kunden kauften auch"):** Läuft in einer **Graph-DB** (z. B. Neo4j), da diese hochkomplexen Traversierungen (Indexfreie Nachbarschaft) in konstanter Zeit ausführen kann.
4. **Log-Dateien & Klickpfade:** Landen in einer extrem schnellen **Key-Value DB** (z. B. Redis), um maximale Schreibgeschwindigkeit zu garantieren.

Die drei großen Herausforderungen (Grenzen)

Diese architektonische Utopie hat jedoch einen extrem hohen Preis:

1. **Komplexität:** Das Unternehmen muss mehrere völlig verschiedene Systeme gleichzeitig warten und überwachen.
2. **Performance-Engpass:** Wenn eine Abfrage Daten aus mehreren Systemen kombinieren muss, entsteht beim Datentransfer zwischen den Töpfen eine hohe Latenz und Netzwerklast (Overhead).
3. **Fehlende Transaktionssicherheit:** Globale Konsistenz (ACID) über Systemgrenzen hinweg ist technisch extrem schwierig, oft nicht möglich oder macht das System unerträglich langsam.

---

### Flashcards

Was ist das Kernprinzip eines Polystores?
?
Ein Polystore vereint heterogene Speicher-Engines (wie Relational, Graph, Dokument, Key-Value) unter einer gemeinsamen Abfrageschnittstelle. Das Kernprinzip ist, dass die Daten physisch in ihrer jeweiligen nativen, hochspezialisierten Datenbank verbleiben, um die effizienteste Engine für das spezifische Datenformat zu nutzen ("One Size Does Not Fit All").

Wie würde man in einer Polystore-Architektur für einen E-Commerce-Shop die Datenbereiche "Bestellungen", "Produktkatalog", "Log-Dateien" und "Kunden-Empfehlungen" aufteilen?
?
- Bestellungen → **Relationale DB** (für ACID-Transaktionssicherheit).
- Produktkatalog → **Dokumenten-DB** (für schemaflexible JSON-Attribute).
- Log-Dateien → **Key-Value DB** (für maximalen Schreibdurchsatz).
- Empfehlungen → **Graph-DB** (für schnelle Traversierung vernetzter Daten).

Nennen Sie die drei wesentlichen technischen und administrativen Herausforderungen, die beim Einsatz von Polystores entstehen.
?
1. **Komplexität:** Hoher Aufwand durch die Wartung und Administration mehrerer unterschiedlicher Systeme.
2. **Performance-Engpass:** Der Datentransfer zwischen den verschiedenen Datensilos erzeugt Netzwerklast und hohe Latenzen (Overhead).
3. **Transaktionen:** Es ist extrem schwer und langsam, globale Konsistenz (ACID-Garantien) über die Grenzen verschiedener Datenbanksysteme hinweg zu garantieren.

Worin liegt der Unterschied zwischen der Philosophie eines "Polystores" und dem Versuch, eine einzelne, riesige "Kompromiss-Datenbank" zu bauen?::Der Polystore akzeptiert das Paradigma "One Size Does Not Fit All" und integriert spezialisierte "Best of Breed"-Datensilos, anstatt die Daten mit Gewalt in ein einziges, für manche Anwendungsfälle ineffizientes Speicherformat zu zwingen.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Polystore]]
SORT file.mtime DESC
```