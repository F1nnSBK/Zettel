#Note

2026-06-12

Tags: [[Virtualisierung]], [[Container]], [[Linux]]
#cloud_computing

---
In der klassischen Voll-Virtualisierung teilt ein Hypervisor einem Gast-Betriebssystem Ressourcen wie RAM und CPU hart zu. Wenn einer virtuellen Maschine 16 GB RAM zugewiesen sind, sind diese 16 GB auf dem physischen Host blockiert – auch wenn die Anwendung in der VM gerade völlig im Leerlauf ist und nur 1 GB benötigt. Diese Ineffizienz verhindert massives, kostengünstiges Skalieren in der Cloud.

Die [[Prozessvirtualisierung]] löst dieses Problem radikal, indem sie auf Gast-Betriebssysteme und Hypervisoren verzichtet. Doch ohne Hypervisor entsteht ein kritisches architektonisches Risiko: Das "Noisy Neighbor"-Problem. Ein einzelner fehlerhafter oder bösartiger Prozess in einem Container könnte 100% der CPU oder des Arbeitsspeichers des Hosts anfordern und so alle anderen parallel laufenden Container zum Absturz bringen.

Die Lösung: Feingranulare Drosselung durch den Kernel

Um dieses Chaos zu verhindern, nutzt moderne Prozessvirtualisierung (wie Docker) die Linux-Kernelfunktion **[[cgroups]]** (Control Groups).

**cgroups** fungieren als strenger Ressourcen-Verwalter direkt im Host-Betriebssystem. Sie ermöglichen es, den Zugriff auf Hardwareressourcen extrem feingranular zu steuern und hart zu limitieren. Der Container Manager definiert über cgroups exakte Quotas:

- **CPU-Limit:** Ein Container darf maximal 25% der Prozessorzeit beanspruchen.
- **RAM-Limit:** Ein Container darf nicht mehr als 500 MB Arbeitsspeicher belegen; überschreitet er dies, wird der Prozess vom Kernel beendet (OOM-Killed).
- Auch Zugriffe auf Grafikkarten, Dateisysteme (Storage I/O) und Netzwerk-Bandbreiten werden hierdurch gedrosselt.

Das brillante architektonische Resultat: Es werden immer nur exakt jene Ressourcen physisch belegt, die _tatsächlich_ im Moment benötigt werden. Das ermöglicht nahezu native Anwendungsgeschwindigkeiten bei einem Bruchteil des Speicherbedarfs.

Die architektonische Symbiose mit Namespaces

cgroups existieren architektonisch nie isoliert, wenn es um Container geht. Sie decken nur die Dimension der **Nutzung** ab. Damit ein Container-Prozess aber auch logisch isoliert wird (also keine Prozesse außerhalb seines eigenen Containers manipulieren kann), müssen cgroups zwingend mit **[[namespaces]]** kombiniert werden, die die Dimension der **Sichtbarkeit** (Isolation der Prozessbäume, Netzwerke etc.) regulieren. Zusammen bilden sie die vollständige Illusion eines eigenständigen Rechners. Ein architektonischer Nachteil dieser Methode bleibt jedoch die schwächere Isolation im Vergleich zur Voll-Virtualisierung, da die physische Hardware für die Prozesse weiterhin sichtbar bleibt und Ausbrüche aus der Container-Umgebung (Container Escapes) möglich sind.

---

Flashcards

Was ist die exakte Aufgabe von `cgroups` (Control Groups) im Kontext der Prozessvirtualisierung?
?
`cgroups` sind eine Linux-Kernelfunktion, die den physischen Ressourcenverbrauch (wie CPU-Auslastung, RAM-Limits, Grafikkarte und Dateisystem-I/O) von Prozessen feingranular limitiert und steuert. Sie verhindern, dass ein einzelner Container das gesamte Host-System monopolisiert.

Was ist der fundamentale funktionale Unterschied zwischen `cgroups` und `namespaces` in einer Container-Architektur?::`cgroups` schränken ein, welche Ressourcen ein Prozess in welchem Umfang **nutzen** darf (CPU, RAM). `namespaces` schränken ein, welche anderen Ressourcen oder Prozesse ein Prozess **sehen** darf (Sichtbarkeit/Isolation).

Welches architektonische Ineffizienz-Problem der Voll-Virtualisierung wird durch den Einsatz von `cgroups` elegant gelöst?
::
Bei der Voll-Virtualisierung werden zugewiesene Ressourcen starr blockiert, auch wenn die VM im Leerlauf ist. `cgroups` erlauben es dem Kernel, Limits zu setzen, aber physischen Speicher und CPU-Zyklen immer nur dann zu belegen, wenn sie von der Anwendung tatsächlich in diesem Moment benötigt werden.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[cgroups]]
SORT file.mtime DESC
```