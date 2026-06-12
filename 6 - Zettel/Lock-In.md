#Note

2026-06-12

Tags: [[Cloud Computing]], [[Systemarchitektur]], [[Servicemodelle]]
#cloud_computing

---
Der Preis der Abstraktion

In der Cloud-Architektur beschreibt der **Vendor Lock-in** den Verlust der technologischen Souveränität eines Unternehmens. Wenn der Betrieb von Hard- und Software zunehmend an die spezifischen Möglichkeiten und Schnittstellen eines Anbieters (Public Cloud) angepasst wird, wird ein späterer Umzug (Migration) zu einem anderen Cloud-Provider technisch massiv erschwert und unverhältnismäßig teuer.

Dieser Effekt skaliert direkt mit den gewählten Cloud-Servicemodellen. Bei [[IaaS]] mietet der Kunde rudimentäre virtuelle Maschinen; der Code läuft auf einem standardisierten Betriebssystem und lässt sich relativ leicht zu einem anderen Provider migrieren. Je höher jedoch die Abstraktion wird, desto stärker wird der Lock-in:

- **[[PaaS]]:** Hier entsteht ein starker Lock-in an die konkrete Plattform, da Laufzeitumgebungen, unterstützte Java-Features, Test-Funktionen und Skalierungs-Logiken von Provider zu Provider stark variieren.
- **[[FaaS]]:** Erzeugt einen massiven Lock-in, da die Kernlogik der Applikation tief mit proprietären Programmierschnittstellen (APIs) und anbieterspezifischen Funktionsblöcken verzahnt wird.
- **[[SaaS]]:** Markiert den **maximalen Lock-in**. Die Anwendung und ihr Betrieb sind vollständig vom Provider vorgegeben; Portabilität existiert de facto nicht, da die Software das proprietäre Differenzierungsmerkmal des Cloud-Anbieters ist.

Selbst On-Premise ist nicht Lock-in-frei

Interessanterweise ist der Lock-in-Effekt kein exklusives Problem der Public Cloud. Im klassischen On-Premise-Betrieb entsteht durch die Minimierung von Hardwareinkompatibilitäten oft ein harter **Hardware Lock-in**, bei dem Server und Komponenten stets vom gleichen Hersteller bezogen werden müssen, um das Ausfallrisiko zu senken.

Architektonische Fluchtwege: Multi Cloud und Hybrid Cloud

Um dem Lock-in einer einzelnen Public Cloud zu entgehen, nutzt die Systemarchitektur verteilte Bereitstellungsmodelle: Die **[[Hybrid Cloud]]** und vor allem die **[[Multi Cloud]]** nutzen einheitliche Verwaltungsoberflächen, um virtuelle Ressourcen über verschiedene Public Clouds oder private Rechenzentren hinweg bereitzustellen. Durch diese Abstraktionsschicht wird der direkte Lock-in an einen einzelnen Provider vermieden, da Workloads dorthin verschoben werden können, wo sie am günstigsten ausgeführt werden. Das **paradoxe Risiko** dieser Strategie ist jedoch, dass das Unternehmen nun Gefahr läuft, sich einem neuen **Lock-in der spezifischen Verwaltungssoftware** zu unterwerfen, da diese Tools häufig ebenfalls stark an bestimmte Cloud-Provider gebunden oder proprietär sind.

---

### Flashcards

In welchem architektonischen Verhältnis stehen der Abstraktionsgrad von Cloud-Servicemodellen und das Risiko eines Vendor Lock-ins?
?
Das Verhältnis ist **direkt proportional**. Je mehr Kontrolle und operative Verantwortung der Kunde an den Cloud-Provider abgibt (wie bei [[PaaS]], [[FaaS]], [[SaaS]]), desto tiefer verzahnt sich der Anwendungscode mit proprietären Systemen und Laufzeitumgebungen, was den Lock-in drastisch erhöht.

Warum entsteht bei Platform as a Service (PaaS) und Function as a Service (FaaS) ein extrem starker Plattform Lock-in?::Weil die Anwendung hart an die spezifischen Beschaffenheiten des Providers gebunden wird. Bei PaaS unterscheiden sich oft die nativ unterstützten Sprach-Features und Bibliotheken, während bei FaaS die Architektur zwingend in proprietäre Programmierschnittstellen und vorgegebene, anbieterspezifische Funktionsblöcke integriert werden muss.

Welche beiden Bereitstellungsmodelle werden primär eingesetzt, um einem Vendor Lock-in aktiv entgegenzuwirken, und welches neue Architekturrisiko provozieren sie dabei?::Die **Multi Cloud** und die **Hybrid Cloud**. Sie nutzen eine einheitliche Verwaltungssoftware, um Workloads über verschiedene Provider zu verteilen. Das neue Risiko dabei ist jedoch, dass das Unternehmen nun in einen **Lock-in der spezifischen Verwaltungssoftware** gerät.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Lock-In]]
SORT file.mtime DESC
```