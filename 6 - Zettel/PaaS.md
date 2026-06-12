#Note

2026-06-12

Tags: [[Cloud Computing]], [[Servicemodelle]], [[Systemarchitektur]], [[Softwareentwicklung]]
#cloud_computing

---
Platform as a Service (PaaS) geht in der Abstraktionshierarchie der Cloud-Modelle einen entscheidenden Schritt weiter als [[IaaS]] oder [[CaaS]]. Der Cloud-Provider übernimmt nicht nur die Verwaltung der Hardware, des Hypervisors und des Betriebssystems, sondern stellt auch die komplette **Laufzeitumgebung (Runtime)** – wie beispielsweise eine vorkonfigurierte Java- oder Node.js-Umgebung – fix und fertig zur Verfügung.

Der architektonische Paradigmenwechsel für den Kunden liegt im radikal verkleinerten Verantwortungsbereich: Er **übergibt nur noch den Anwendungscode**. Das gesamte Hosting, die Prozess-Isolierung und die Skalierung bei Lastspitzen werden vom Cloud-Provider im Hintergrund abgewickelt, ohne dass der Kunde Einblick in die konkrete Ausführung oder Hardwareauswahl erhält (oft gibt es nur eine minimale Auswahl an Konfigurationen).

Die Taxi-Analogie

Um die Charakteristik von PaaS im Vergleich zu anderen Modellen greifbar zu machen, dient in der Transport-Metapher die **Fahrt in einem Taxi**. Während der Kunde bei IaaS (Leasing-Auto) und CaaS (Mietauto) das Fahrzeug noch selbst steuert (den Container-Prozess verwaltet), ist er bei PaaS erstmals reiner Beifahrer. Er gibt lediglich die Abholzeit und das Fahrtziel vor (den auszuführenden Anwendungscode). Das Taxiunternehmen (der Cloud Provider) wählt das konkrete Fahrzeug, stellt den Fahrer und übernimmt die gesamte Wartung. Abgerechnet wird On-Demand nach gefahrenen Kilometern und Autoklasse.

Trade-off: Bequemlichkeit gegen Plattform Lock-In

PaaS bietet für Entwicklerteams gigantische Vorteile, da der komplette operative Overhead (Infrastruktur-Wartung, Patching, Load-Balancing) entfällt und Applikationen extrem schnell bereitgestellt werden können.

Diese Bequemlichkeit wird jedoch mit einem massiven **Vendor Lock-In** (Herstellerbindung) erkauft. Da jeder Cloud-Provider seine PaaS-Umgebungen individuell aufbaut, unterscheiden sich die Laufzeitumgebungen oft gravierend hinsichtlich der unterstützten Sprach-Features, der angebundenen Bibliotheken und der integrierten Funktionen zum automatisierten Testen und Skalieren. Ein Code, der hochgradig für eine spezifische PaaS-Lösung optimiert wurde, lässt sich in der Regel nicht ohne massiven Refactoring-Aufwand zu einem anderen Cloud-Provider portieren.

---

### Flashcards

Was stellt der Cloud-Provider bei Platform as a Service (PaaS) bereit und auf was reduziert sich die operative Verantwortung des Kunden?
?
Der Provider stellt die gesamte Infrastruktur inklusive der **Laufzeitumgebung** bereit und übernimmt die Isolierung und den Betrieb. Die operative Verantwortung des Kunden reduziert sich darauf, lediglich den reinen **Anwendungscode** zu schreiben und an die Plattform zu übergeben.

Mit welcher Transport-Analogie lässt sich das PaaS-Modell präzise beschreiben und was bedeutet das für die Kontrolle des Kunden?::Die Analogie ist die **Taxifahrt**. Der Kunde ist nicht länger der Fahrer (wie bei IaaS/CaaS), sondern Beifahrer. Er gibt lediglich das Ziel vor (Code), während der Anbieter das Fahrzeug lenkt, es auswählt und wartet. Der Kunde gibt somit die operative Kontrolle über die Ausführung ab.

Warum geht die Nutzung von Platform as a Service (PaaS) architektonisch in der Regel mit einem sehr starken Vendor Lock-in (Anbieterbindung) einher?::Weil der Anwendungscode stark an die proprietären Spezifikationen des Plattformbetreibers (z.B. spezifisch unterstützte Java-Features, proprietäre Skalierungs-Logiken oder Test-Schnittstellen) angepasst wird. Ein Wechsel der Laufzeitumgebung zu einem anderen Provider ist daher nicht ohne großen Aufwand möglich.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[PaaS]]
SORT file.mtime DESC
```