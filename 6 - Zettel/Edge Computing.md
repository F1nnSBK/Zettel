#Note

2026-06-12

Tags: [[Cloud Computing]], [[Systemarchitektur]], [[IoT]], [[Bereitstellungsmodelle]]
#cloud_computing

---
Das klassische Cloud Computing basiert auf der strikten Zentralisierung von Rechenleistung. Angesichts des massiven zu erwartenden Wachstums an datenproduzierenden Geräten stößt dieses Modell jedoch an physikalische Grenzen. **Edge Computing** beschreibt als Gegenentwurf die Verarbeitung von Daten **so nahe wie möglich am Entstehungsort**.

Die Architektur unterscheidet hierbei drei logische Ebenen:

1. **Far Edge (Producers):** Die eigentlichen Produzenten der Daten (Edge Devices), wie beispielsweise eine Videokamera in einer Gießerei, die Bilder zur Qualitätskontrolle erzeugt.
2. **Edge Computing:** Lokale Infrastruktur in der Nähe des Entstehungsortes, die direkte, ortsabhängige Entscheidungen trifft (z.B. die sofortige Justierung von Produktionsparametern auf Basis der Kamerabilder).
3. **Private / Public Cloud:** Erst im letzten Schritt, und nach einer massiven Vorfilterung am Edge, werden aggregierte Daten zur langfristigen Auswertung in die Cloud weitergeleitet.

Architektonische Hebel: Latenz, Bandbreite und Sicherheit

Die Dezentralisierung durch Edge Computing ermöglicht zentrale Anwendungsszenarien, die in einer reinen Cloud-Architektur unmöglich oder unwirtschaftlich wären:

- **Echtzeitverarbeitung (Smart Factory):** Durch den Wegfall des Netzwerkwegs in die Cloud können Analysen in Millisekundenbruchteilen erfolgen (z.B. das sofortige Herausfiltern fehlerhafter Teile am Fließband).
- **Datenreduktion & Bandbreitenschonung:** Bei Anwendungsfällen mit extremem Bandbreitenbedarf (wie hochauflösende Live-Events oder Turbinendaten) fungiert das Edge als Kompressionsschicht, die nur noch relevante Anomalien über das Netz verschickt.
- **Resilienz (Unabhängige Verarbeitung):** Die Systeme können kritische Prozesse auch dann aufrechterhalten, wenn die Internetverbindung zur zentralen Cloud ausfällt.
- **Privacy by Design:** Sensible Daten (wie biometrische Authentifizierung) werden direkt am Entstehungsort verarbeitet und verlassen diesen nie. Beispielsweise kann ein lokales Security-Gateway Zugänge verifizieren, ohne jede Anfrage samt Schlüssel an die Cloud zu senden.

Der Trade-off: Heterogenität und Wartungshölle

Der architektonische Preis für diese enorme Leistungssteigerung am Rand des Netzwerks ist eine radikale Erhöhung der operativen Komplexität. Edge Computing steht vor massiven Herausforderungen, was die **Wartung der Software bis hin zu den abertausenden Datenproduzenten** angeht. Zudem stellt die extreme **Heterogenität der Edge Devices** (unterschiedliche Betriebssysteme, Architekturen und Leistungsfähigkeiten) eine gigantische Hürde für eine einheitliche Verwaltung und orchestrierte Sicherheit dar.

---

### Flashcards

Was beschreibt das Architektur-Konzept des "Edge Computing" im Gegensatz zum klassischen Cloud Computing?
?
Edge Computing kennzeichnet die Verarbeitung von Daten **so nahe wie möglich an ihrem Entstehungsort** (dem "Rand" des Netzwerks). Anstatt alle Rohdaten ungefiltert in eine zentrale Cloud zu senden, werden sie lokal ausgewertet, und nur noch relevante Informationen werden weitergeleitet.

Welche vier zentralen Vorteile (architektonische Hebel) entstehen durch die Nutzung von Edge Computing für datenintensive Prozesse?
?
1. **Echtzeitverarbeitung** für minimale Latenzen (z.B. in der Smart Factory).
2. **Datenreduktion** zur Bewältigung extremen Bandbreitenbedarfs.
3. **Ausfall Resilienz**, da die Verarbeitung unabhängig von einer bestehenden Internetverbindung funktioniert.
4. **Datenschutz (Privacy)**, da sensible Daten den Entstehungsort zur Authentifizierung nicht mehr zwingend verlassen müssen.

Was sind die zwei massivsten operativen Herausforderungen beim flächendeckenden Einsatz von Edge Computing?::Die hochkomplexe **Wartung** der Software, die auf abertausenden dezentralen Endgeräten aktuell gehalten werden muss, sowie die **Heterogenität** der Edge-Geräte, die eine einheitliche Verwaltung erschwert.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Edge Computing]]
SORT file.mtime DESC
```