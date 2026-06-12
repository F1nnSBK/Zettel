#Note

2026-06-12

Tags: [[Horizontale Skalierung]], [[Lock-In]], [[Public Cloud]]
#cloud_computing 

---
Der Paradigmenwechsel: Von Hardware zu Services

Der Umstieg auf **[[Cloud Computing]]** markiert den Tod der klassischen Hardware-Identifikation. In einer [[On-Premise]]-Architektur besitzt das Unternehmen physische Maschinen, trägt das volle Risiko des Livegangs und ist für Betrieb sowie Kühlung verantwortlich. Die Cloud abstrahiert diese physische Realität. Wie eine Wolke aus unzähligen, mikroskopischen Wassertropfen als einheitliches Gebilde am Himmel erscheint, so orchestriert die Cloud eine hochkomplexe Ansammlung von IT-Ressourcen zu einem nahtlosen Pool virtueller Dienstleistungen.

Der architektonische Kern dieses Konzepts liegt in der **Entkopplung**. Ressourcen werden nicht länger vorab für maximal zu erwartende Lastspitzen beschafft (was zu gewaltigen Opportunitätskosten und Leerlauf führt), sondern flexibel per API bereitgestellt. Dies ermöglicht den Sprung zur agilen Prototypenentwicklung und zum risikolosen Experimentieren, da Instanzen bei Nichtgebrauch einfach wieder deprovisioniert werden können.

Die Hebelwirkung der Skalierbarkeit & Skaleneffekte

Ein System ist nur dann robust, wenn es atmen kann. Die Cloud ermöglicht fundamentale Leistungsanpassungen:

1. **[[Vertikale Skalierung]] (Scale-Up):** Erhöhung der CPU- oder RAM-Ressourcen einer Maschine. Hat harte architektonische Grenzen und erfordert meist eine Systemunterbrechung.
2. **[[Horizontale Skalierung]] (Scale-Out):** Das Hinzufügen weiterer Knoten. Dies ist das absolute Herzstück web-skalierbarer Systeme. Die Applikation muss dafür zustandslos (stateless) konzipiert sein, profitiert dann aber von nahezu unendlichen Wachstumsmöglichkeiten im laufenden Betrieb.

Zusätzlich profitieren Cloud-Provider von extremen **Fixkostendegressionen (Skaleneffekten)**. Da sie Hardwaremengen in gigantischem Ausmaß beschaffen und extrem fokussiertes Know-How (Red Teams für Security) bündeln können, verteilen sich diese massiven Vorabinvestitionen auf Millionen von Cloud-Diensten, was die Stückkosten drastisch reduziert.

Die dunkle Triade der Cloud-Risiken

Trotz der enormen Vorteile (On-Demand Bereitstellung, globale Verteilung, Zugriff auf KI und Machine Learning) erzeugt die Cloud neue, gravierende Architekturprobleme:

- **Kosten-Explosion durch Ineffizienz:** Da Kosten nach Verbrauch („Aufwand“) entstehen, erzeugt ungenutzte, aber laufende Infrastruktur (Zombie-Ressourcen) oder die simple Portierung nicht-optimierter Systeme horrende Kosten. Bis zu 58% der Unternehmen berichten von teureren Cloud-Migrationen als ursprünglich geplant.
- **Der Verlust der IT-Governance:** Entwickler können per Klick Ressourcen starten. Ohne hart einkodierte, zentrale Richtlinien entstehen unkontrollierte Netzwerke, unautorisierte API-Nutzungen und Compliance-Verletzungen, da Daten ohne Freigabe auf anderen Kontinenten landen können.
- **Notwendigkeit für Immutable Infrastructure:** Administratoren müssen zwingend auf skriptbasierte Konfigurationen (Infrastructure as Code) umstellen. Wer in der Cloud Server wie früher per Hand konfiguriert (Mutable Infrastructure), erzeugt nicht-reproduzierbare "Schneeflocken-Server", die in verteilten Architekturen fatale Ausfälle garantieren.

---

### Flashcards

Warum ist das Kostenmanagement durch Fixkostenvariabilisierung im Cloud Computing ein massives architekturelles Risiko und nicht nur ein rein wirtschaftlicher Vorteil?
?
Die Umwandlung von Fixkosten in variable, nutzungsabhängige Kosten (Fixkostenvariabilisierung) eliminiert zwar die hohen Anfangsinvestitionen. Wird Cloud Computing jedoch für alte, architektonisch nicht optimierte Applikationen ("Lift-and-Shift") verwendet oder werden nicht mehr benötigte Ressourcen (Zombie-Ressourcen) von den Entwicklern nicht gelöscht, explodieren die laufenden Kosten unkontrolliert. Umfragen zeigen, dass solche Fehlkonfigurationen Budgets schnell um 70% sprengen.

Was ist der Unterschied zwischen **[[Vertikale Skalierung]]** und **[[Horizontale Skalierung]]** hinsichtlich des Anwendungsbetriebs?::Vertikale Skalierung (mehr RAM/CPU) erfordert oft einen Stopp der Anwendung und ist durch Hardwaregrenzen limitiert. Horizontale Skalierung (mehr Rechnerknoten) ermöglicht granulare Leistungssteigerung im laufenden Betrieb, zwingt die Anwendung aber dazu, diese verteilte Struktur architektonisch zu unterstützen.

Warum führt Cloud Computing häufig zum Verlust der **IT-Governance** und zur Erhöhung von Sicherheitsrisiken?::Weil der langwierige, zentrale Beschaffungsprozess durch sofortigen Self-Service ersetzt wird. Entwickler können weltweit Ressourcen provisionieren, was ohne hart codierte Kontrollstrukturen zu falschen Speicherorten (Compliance-Bruch), verwaisten Administrationsrechten und ungeschützten APIs führt.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Cloud Computing]]
SORT file.mtime DESC
```