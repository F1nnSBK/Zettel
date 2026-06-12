#Note

2026-06-12

Tags: [[Infrastrukturmanagement]], [[Systemarchitektur]], [[Automatisierung]]
#cloud_computing

---
In der traditionellen IT wurden Server wie "Haustiere" (Pets) gepflegt: Sie erhielten Namen, wurden jahrelang am Leben erhalten und händisch gepatcht ([[Mutable Infrastructure]]). Das fatale Resultat dieser Praxis sind **undokumentierte Systemzustände** und sogenannte **Schneeflocken-Konfigurationen**, bei denen kein Server dem anderen exakt gleicht und Administratoren aus Angst vor einem Crash jeden Neustart vermeiden.

**Immutable Infrastructure** (unveränderbare Infrastruktur) erzwingt einen radikalen Paradigmenwechsel: Server werden zu austauschbarem "Vieh" (Cattle). Der architektonische Grundgedanke lautet: **Es ist sicherer, ein aus Code reproduzierbares System neu zu starten, das erst 6 Minuten online ist, als ein manuell gepatchtes System zu betreiben, das seit 6 Jahren keinen Reboot mehr gesehen hat**. Es gibt schlichtweg keine nicht-codierten Infrastrukturveränderungen mehr. Wenn ein Update nötig ist, wird das alte System zerstört und ein komplett neues aus der Code-Basis (via CI/CD) hochgefahren.

Architektonische Symbiose mit der Cloud

Die Notwendigkeit für Immutable Infrastructure ist in der Cloud keine Geschmacksfrage, sondern ein hartes architektonisches Diktat. Durch den Bedarf, Lastspitzen durch **[[Horizontale Skalierung]]** abzufangen, müssen innerhalb von Sekundenbruchteilen hunderte neue Instanzen fehlerfrei bereitgestellt werden. Das manuelle Testen oder Konfigurieren von Code auf jeder einzelnen Maschine ist in solchen dynamischen Clustern absolut unmöglich.

Um diesen Automatisierungszwang zu befriedigen, werden Werkzeuge wie **Ansible, Puppet, Docker und Kubernetes** eingesetzt. Sie überführen den Zustand der Infrastruktur in versionierten Code. Die Auslieferung dieser Unveränderbarkeit wird durch durchstrukturierte Pipelines flankiert: **Continuous Integration** (Testen des Codes), **Continuous Delivery** (Bauen der Artefakte) und letztendlich **Continuous Deployment** (automatisiertes Ersetzen der alten Instanzen durch die neuen).

Trade-offs und Herausforderungen

Der Übergang zur Immutable Infrastructure erfordert den fundamentalen Aufbau neuen, spezialisierten Know-hows. Entwicklungs- und Betriebsteams müssen ihre Prozesse vollständig auf Code-Automatisierung umstellen. Jeder Hotfix, der früher in zwei Minuten per SSH auf dem Server gelöst wurde, muss nun den gesamten Lifecycle vom Code-Commit über den automatisierten Build bis zum Deployment durchlaufen. Dies erfordert eine extrem performante und fehlerresistente CI/CD-Architektur.

---

### Flashcards

Was ist der fundamentale Leitgedanke hinter dem Konzept der Immutable Infrastructure hinsichtlich der Systemlaufzeit und Fehleranfälligkeit?
?
Der Grundgedanke lautet, dass es wesentlich sicherer und verlässlicher ist, ein System neu zu starten, das erst 6 Minuten online ist (weil es jederzeit fehlerfrei aus Code reproduzierbar ist), anstatt panisch ein System am Leben zu erhalten, das seit 6 Jahren ohne Reboot läuft (Serverfestungen). Manuelle Änderungen sind strengstens verboten; jede Änderung ist im Code definiert.

Warum ist Immutable Infrastructure für Cloud-Architekturen, die [[Horizontale Skalierung]] nutzen, absolut unverzichtbar?::Weil bei horizontaler Skalierung dynamisch neue Knoten hoch- und heruntergefahren werden. Ein manuelles Konfigurieren oder Testen auf jeder einzelnen Maschine ist bei dieser Dynamik und Skalierung unmöglich, weshalb jede Instanz identisch und automatisiert aus einem Code-Blueprint entstehen muss.

Welche bekannten Werkzeuge werden typischerweise zum Aufbau und Management einer Immutable Infrastructure eingesetzt?::Werkzeuge wie Ansible, Puppet, Docker und Kubernetes (K8s).


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Immutable Infrastructure]]
SORT file.mtime DESC
```