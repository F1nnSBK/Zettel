#Note

2026-06-12

Tags: [[Cloud Computing]], [[Servicemodelle]], [[Container]], [[Docker]]
#cloud_computing

---
**Container as a Service (CaaS)** ist ein Cloud-Dienstleistungsmodell, das die architektonische Lücke zwischen der rohen Infrastruktur ([[IaaS]]) und den strikten Laufzeitumgebungen ([[PaaS]]) schließt. Es basiert technologisch vollständig auf der **[[Prozessvirtualisierung]]**.

Der fundamentale Unterschied zu IaaS ist die Verantwortungsübergabe des Betriebssystems: Der Cloud-Anbieter abstrahiert die konkrete physische Hardware, den Hypervisor und **das Host-Betriebssystem** vom Kunden. Das definierte Nutzungsobjekt für den Kunden ist der **Container**. Der Kunde konfiguriert lediglich die Ressourcenausstattung (wie CPU-Kerne und RAM) und übergibt dem Provider ein fertiges Container-Image, welches dieser in seiner bereitgestellten Umgebung ausführt. Die Pflichten für OS-Updates und Kernel-Patching entfallen somit für das Unternehmen.

Die Mietauto-Analogie

Um die Charakteristika von CaaS greifbar zu machen, eignet sich in der Transport-Metapher das **Mietauto**. Der Kunde wählt für einen konkreten, meist kurzfristigen Einsatz situativ eine passende Fahrzeugklasse (Container-Größe) aus einer eher kleinen Auswahl. Abgerechnet wird streng nach Nutzung (On-Demand Rechnung), etwa nach Zeit oder Kilometern. Das Fahrzeug bleibt Fremdeigentum der Vermietungsgesellschaft, die auch die komplette Wartung des Wagens (des Betriebssystems) übernimmt. Der Fahrer (Kunde) steuert das Auto jedoch weiterhin selbst (verwaltet den Container-Prozess).

Der operative Hebel: Autoscaling

Durch den Wegfall des Gast-Betriebssystems starten Container in CaaS-Umgebungen in Millisekundenbruchteilen. Diese Eigenschaft ermöglicht den größten operativen Hebel dieses Modells: Das **Autoscaling**. Der Cloud-Anbieter kann das System so konfigurieren, dass bei erhöhter Nachfrage (Lastspitzen) vollautomatisch und ohne manuelles Eingreifen weitere Container-Images gestartet werden. Sinkt die Nachfrage wieder, werden die Container reduziert. Dies garantiert extrem effizientes Ressourcenmanagement, bei dem immer nur jene Leistung bezahlt wird, die im jeweiligen Moment zwingend erforderlich ist.

---

### Flashcards

Was stellt der Cloud-Provider bei Container as a Service (CaaS) zur Verfügung und was ist die primäre Aufgabe des Kunden?
?
Der Provider stellt eine vollständige **Container-Umgebung** bereit und abstrahiert dabei sowohl die Hardware als auch das Host-Betriebssystem. Der Kunde muss sich nicht um das OS kümmern, sondern erstellt lediglich das **Container-Image**, welches vom Anbieter ausgeführt wird.

Welche reale Transport-Analogie beschreibt das CaaS-Modell am treffendsten und warum?::Die Analogie des **Mietautos**. Der Kunde wählt aus einer kleineren Auswahl situativ eine Klasse aus, bezahlt exakt nach Nutzung (On-Demand), das Auto bleibt Fremdeigentum und die Wartung (des Betriebssystems) ist an den Vermieter ausgelagert.

Welchen massiven operativen Vorteil bietet CaaS zur Bewältigung von unvorhersehbaren Lastspitzen (bspw. im E-Commerce)?::Das **Autoscaling**. Der Cloud-Provider kann so konfiguriert werden, dass er bei erhöhter Nachfrage vollautomatisch weitere Container-Instanzen hochfährt und diese bei sinkender Nachfrage wieder reduziert, ohne dass ein Administrator eingreifen muss.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[CaaS]]
SORT file.mtime DESC
```