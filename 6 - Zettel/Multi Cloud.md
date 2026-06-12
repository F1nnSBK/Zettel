#Note

2026-06-12

Tags: [[Cloud Computing]], [[Bereitstellungsmodelle]], [[Systemarchitektur]], [[Lock-In]]
#cloud_computing

---
Das Bereitstellungsmodell der **Multi Cloud** markiert die höchste Stufe der Abstraktion von der konkreten IT-Infrastruktur,. In diesem Modell entscheidet sich ein Unternehmen bewusst gegen die exklusive Nutzung eines einzelnen Cloud-Providers und setzt stattdessen auf die gleichzeitige Nutzung **verschiedener Public Clouds** (wie AWS, Azure, Google Cloud),.

Um ein administratives Chaos zu verhindern, ist der architektonische Kern dieses Modells eine **einheitliche Verwaltungsoberfläche** (Self-Service-Portal und Automation),. Diese Management-Schicht abstrahiert die spezifischen Dienstleistungen und Schnittstellen der einzelnen Provider. Durch diese zentrale Steuerung können unternehmensweite **Governance-Konzepte** (beispielsweise für den Kostenüberblick) und einheitliche **Sicherheitskonzepte** über alle genutzten Clouds hinweg konsequent umgesetzt werden,.

Ökonomie: Kostenoptimierung vs. Lock-in Verschiebung

Die Multi Cloud zielt auf die Lösung zweier elementarer Probleme der Cloud-Architektur ab:

1. **Vermeidung des Lock-ins:** Durch die Verteilung der Workloads und die standardisierte Verwaltungsoberfläche wird die starke technologische und wirtschaftliche Bindung (Anbieter Lock-in) an eine einzelne Public Cloud effektiv verhindert,.
2. **Kostenoptimierter Betrieb:** Da das Unternehmen flexibel agieren kann, wird für jede spezifische Anwendung oder Aufgabe exakt jener Provider ausgewählt, bei dem die konkret benötigten Ressourcen aktuell am günstigsten angeboten werden,.

Der **architektonische Trade-off** für diese Freiheit ist jedoch gravierend. Zum einen entsteht eine **hohe Gesamtkomplexität** bei der Konfiguration und im dauerhaften Betrieb,. Zum anderen droht ein paradoxes, neues Risiko: Die Gefahr eines **Lock-ins bei der eingesetzten Verwaltungssoftware**,. Da diese Tools häufig proprietär sind oder individuelle Möglichkeiten zum Multi-Cloud-Management der Provider nutzen, wird die Abhängigkeit lediglich von der Infrastruktur- auf die Management-Ebene verschoben,.

Aus diesen Gründen ist die Multi Cloud keine Standardempfehlung, sondern sollte **nur von Unternehmen eingesetzt werden, die bereits intensive Erfahrungen mit Cloud Computing gesammelt haben** und ihren Betrieb nun strategisch konsolidieren möchten,.

---

### Flashcards

Welches architektonische Hauptziel verfolgt das Bereitstellungsmodell der Multi Cloud im Vergleich zur reinen Public Cloud?
?
Es zielt primär auf die **Vermeidung eines Anbieter-Lock-ins** ab, indem gleichzeitig verschiedene Public Clouds über eine einheitliche Verwaltungsoberfläche genutzt werden,. Zudem ermöglicht es einen **kostenoptimierten Betrieb**, da für jede Aufgabe gezielt der günstigste Anbieter gewählt werden kann,.

Welches neue, paradoxe Risiko entsteht bei dem Versuch, durch eine Multi Cloud den klassischen Provider-Lock-in zu verhindern?::Es entsteht die massive Gefahr eines neuen **Lock-ins an die eingesetzte einheitliche Verwaltungssoftware**, da diese Management-Tools häufig spezifisch an bestimmte Cloud-Provider gebunden sind,,.

Warum eignet sich die Multi Cloud Architektur nicht für Cloud-Anfänger, sondern primär für Unternehmen mit tiefgreifender IT-Expertise?::Weil die parallele Steuerung unterschiedlicher Provider über eine abstrakte, zentrale Schicht eine sehr **hohe Gesamtkomplexität** in der Konfiguration und im laufenden Betrieb erfordert.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Multi Cloud]]
SORT file.mtime DESC
```