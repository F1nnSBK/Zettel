#Note

2026-06-12

Tags: [[Cloud Computing]], [[Skalierung]], [[Systemarchitektur]]
#cloud_computing

---
Traditionelle Monolithen wachsen über die [[Vertikale Skalierung]] (Scale-Up), bei der RAM, CPU oder Festplatten durch leistungsstärkere Komponenten ersetzt werden. Dieser Ansatz stößt schnell an harte architektonische und physikalische Grenzen. Zudem erfordert der Hardware-Austausch meist eine ungewollte Systemunterbrechung (Downtime). Die **[[Horizontale Skalierung]]** (Scale-Out) verlagert das Paradigma: Statt einen Super-Computer zu bauen, nutzt man unzählige kleine Rechnerknoten (Commodity Hardware). Die Hardwareausstattung pro Knoten bleibt unangetastet, stattdessen wird die Anwendung schlichtweg auf weiteren Rechnern parallel ausgeführt. Der entscheidende Vorteil: Dies erlaubt **unterbrechungsfreie Leistungssteigerungen im laufenden Betrieb** und bietet theoretisch unendliche Wachstumsmöglichkeiten.

Architektonische Konsequenzen und Trade-offs

Horizontale Skalierung gibt es nicht umsonst. Die Anwendung _muss_ diese verteilte Architektur aktiv unterstützen. Das bedeutet fundamentale Änderungen im Softwaredesign:

1. **Statelessness (Zustandslosigkeit):** Anwendungen dürfen keinen nutzerspezifischen Zustand (wie Session-Daten) lokal im Speicher des Webservers ablegen. Da ein Load Balancer den nächsten Request des Nutzers an einen völlig anderen Knoten routen könnte, muss der Zustand zwingend an externe Systeme (z.B. ein verteilter Cache oder eine zentrale Datenbank) ausgelagert werden.
2. **Automatisierungszwang:** Da horizontale Skalierung bedeutet, dass ständig neue Maschinen aufgespannt und wieder zerstört werden, bricht das traditionelle Betriebsmodell ("Mutable Infrastructure") zusammen. Es ist unmöglich, auf hunderten Maschinen Code manuell zu testen oder Konfigurationen händisch anzupassen. Ein System, das horizontal skaliert, erfordert gnadenlos durchstrukturierte [[Continuous Integration]] und [[Continuous Deployment]] Pipelines sowie eine [[Immutable Infrastructure]],.

Symbiose mit Prozessvirtualisierung

Während virtuelle Maschinen (Voll-Virtualisierung) aufgrund ihrer umfassenden Imagegröße (3-4 GB) und ihres trägen Systemstarts nur eingeschränkt horizontal skalieren können, bildet die Prozessvirtualisierung (Container-Technologie) das perfekte Fundament. **[[Container]]** bündeln nur Abhängigkeiten und die Anwendung selbst (50-500 MB), verzichten auf einen eigenen Kernel und starten in Bruchteilen von Sekunden. Dies ermöglicht Cloud-Plattformen, im Rahmen von CaaS (Container as a Service), hocheffizientes Autoscaling durchzuführen, bei dem bei Lastspitzen blitzschnell neue Container hochgefahren werden,.

---

### Flashcards

Warum erfordert Horizontale Skalierung architektonisch zwingend den Einsatz von Paradigmen wie Immutable Infrastructure und umfassenden CI/CD-Pipelines?
?
Weil bei horizontaler Skalierung eine Anwendung über eine Vielzahl an parallel laufenden Knoten verteilt ist, die oft dynamisch hinzukommen oder entfernt werden. Händische Deployments, manuelles Testen oder nachträgliche Konfigurationen auf jedem einzelnen Rechner (Mutable Infrastructure) sind bei dieser Skalierungsform absolut unmöglich und fehleranfällig. Jede Instanz muss identisch automatisiert aus Code generiert werden,.

Was ist der gravierendste Unterschied zwischen vertikaler (Scale-Up) und horizontaler (Scale-Out) Skalierung in Bezug auf den Live-Betrieb einer Applikation?::Vertikale Skalierung erfordert meist einen Stopp der Anwendung (Downtime) und ist physikalisch limitiert, während horizontale Skalierung völlig unterbrechungsfrei im laufenden Betrieb durch das Zuschalten neuer Rechner realisiert werden kann,.

Warum eignen sich Container wesentlich besser für massive horizontale Skalierung als traditionelle Virtuelle Maschinen (VMs)?::Container nutzen Prozessvirtualisierung und haben dadurch eine minimale Imagegröße (Oft nur 50-500 MB) sowie einen rasend schnellen Systemstart, während VMs träge hochfahren und durch unnötigen Prozessor- sowie Speicheroverhead (volles Gast-OS) massiv ausgebremst werden.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Horizontale Skalierung]]
SORT file.mtime DESC
```