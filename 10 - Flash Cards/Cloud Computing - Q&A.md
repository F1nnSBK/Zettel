
#cloud_computing_qa

### 1. Grundlagen & Motivation

Was sind Server-Festungen, wodurch entstehen sie und warum sind sie ein Problem für den Betrieb?
?
- **Was**: Langlaufende, isolierte Altsysteme, die manuell gepatcht und konfiguriert werden.
- **Entstehung**: Durch Mutable Infrastructure (manuelle Änderungen direkt auf dem Server) ohne Automatisierung und Dokumentation.
- **Problem**: Es entstehen undokumentierte, nicht reproduzierbare Zustände ("Schneeflocken-Server"). Dies führt zu Angst vor Neustarts (Unsicherheit des Wiederanlaufs), unzureichenden Sicherheits-Updates (Sicherheitslücken) und hemmt Innovationen, da Systeme nicht einfach repliziert oder aktualisiert werden können.


---

Wodurch entstehen lange Bereitstellungszeiten beim traditionellen On-Premise Betrieb und was sind die gewollten Auswirkungen hiervon?
?
Die langen Zeiten entstehen durch zeitintensive physische und manuelle Prozesse (Hardware bestellen, ins Rack einbauen, verkabeln, OS installieren). Die gewollte Auswirkung ist eine Art "Gatekeeping" (Entschleunigung), da jede Änderung vorher genau geprüft wird.

---

Was beschreibt die Fixkostenvariabilisierung im Cloud Computing?
?
Die Umwandlung von festen, hohen Vorab-Investitionen für Hardware (CapEx) in nutzungsabhängige, variable Kosten (OpEx) durch On-Demand-Abrechnung.

---
Nenne vier zentrale architektonische und ökonomische Vorteile von Cloud Computing.
?
1. Horizontale Skalierung (Scale-Out)
2. Innovation (Nutzung fertiger Bausteine wie KI oder Bilderkennung)
3. Globale Verteilung (Minimierung von Latenz durch weltweite Rechenzentren)
4. Fixkostenvariabilisierung (Nutzungsbasierte Abrechnung)

---
Worin unterscheiden sich vertikale Skalierung (Scale-Up) und horizontale Skalierung (Scale-Out)?
?
Vertikale Skalierung bedeutet die Aufrüstung bestehender Hardware (mehr RAM, stärkere CPU), was oft eine Downtime erfordert und physisch limitiert ist. Horizontale Skalierung bedeutet das Hinzufügen weiterer Knoten/Rechner, was im laufenden Betrieb passiert und nahezu unbegrenzt möglich ist, aber von der Anwendung architektonisch unterstützt werden muss.

---
Was ist der Unterschied zwischen Mutable und Immutable Infrastructure?
?
Bei der Mutable Infrastructure werden bestehende Server fortlaufend händisch gepatcht (führt zu Server-Festungen). Bei der Immutable Infrastructure (z.B. Docker) werden Laufzeitumgebungen nicht modifiziert, sondern bei jeder Änderung komplett neu aus Code generiert und ersetzt.

---
Welche drei zentralen Herausforderungen bringt Cloud Computing in der Praxis mit sich?
?
1. Fehlendes Know-how (Infrastructure as Code erfordert Programmierwissen)
2. Kostenmanagement (Budgetüberschreitung, Cloud Sprawl)
3. IT-Sicherheit (ungesicherte APIs, fehlende Governance)

---
Grenze Continuous Integration, Continuous Delivery und Continuous Deployment voneinander ab.
?
Continuous Integration automatisiert das Zusammenführen von Codeänderungen und das Ausführen von Tests.
Continuous Delivery automatisiert den Bau der Artefakte und bereitet das Deployment vor (manuelle Freigabe nötig).
Continuous Deployment automatisiert zusätzlich die tatsächliche Inbetriebnahme der neuen Softwareversion ohne manuellen Eingriff.

---

Was beschreibt die Power Usage Effectiveness (PUE) und wie wird sie berechnet?
?
Die PUE ist ein Maß für die Energieeffizienz eines Rechenzentrums. Sie wird berechnet als:
$$\text{PUE} = \frac{\text{Gesamter Energieverbrauch des Rechenzentrums}}{\text{Energieverbrauch der IT-Infrastruktur}}$$
Ein PUE-Wert von z.B. 1,58 bedeutet, dass für jede 100 W Leistung der IT-Hardware weitere 58 W für Kühlung und Verlustleistung anfallen. Je näher der Wert an 1,0 liegt, desto effizienter ist das Rechenzentrum.

---

Schneeflocken-Server (Snowflake Server)::Ein Server, dessen Konfiguration durch fortlaufende manuelle, undokumentierte Änderungen einzigartig und nicht reproduzierbar geworden ist (wie eine Schneeflocke). Dies führt zu schwer reproduzierbaren Fehlern und erschwert die Skalierung oder den Wiederaufbau nach Ausfällen.

---

### 2. Virtualisierung & Servicemodelle

Simulation::Vollständige Nachbildung eines Systems und seiner internen Wirkzusammenhänge durch Software zum reinen Erkenntnisgewinn (z.B. Flugsimulator, iPhone-Simulator).

Emulation::Stellt Schnittstellen und Funktionen eines Systems nach, oft ohne die interne Logik exakt zu kopieren, und dient als praxistauglicher Ersatz (z.B. JVM, WSL 1, Rosetta 2, virtuelle Netzwerkkarten).

Virtualisierung::Entkoppelt die Software-Ausführungsumgebung von der physischen Hardware unter Nutzung derselben Prozessorarchitektur (z.B. ESXi, KVM, VirtualBox) mit minimalen Performanceverlusten im Vergleich zur Emulation.

Wie funktioniert eine Emulation genau (Funktionsweise, Übersetzungs-Mechanismus) und was sind typische Praxisbeispiele?
?
- **Funktionsweise**: Eine Emulation bildet die Schnittstellen eines physischen oder virtuellen Systems nach, übernimmt jedoch **nicht** dessen interne Wirkzusammenhänge. Stattdessen werden angepasste Programmroutinen verwendet, um mit den Eingaben des Gastes denselben Output zu erzeugen wie das Originalsystem.
- **Übersetzungs-Mechanismus**:
  - **Interoperabilität (z.B. WSL 1)**: Fängt Systemaufrufe (Syscalls) ab. WSL 1 übersetzt Linux-Systembefehle zur Laufzeit in entsprechende Windows-Systemaufrufe und übersetzt die Ergebnisse wieder zurück.
  - **Architektur-Übersetzung (z.B. Rosetta 2)**: Übersetzt compilierten Maschinencode einer inkompatiblen Prozessorarchitektur (z.B. x86-Befehle für Intel) in Befehle der ausführenden CPU-Architektur (z.B. ARM-Befehle für Apple Silicon).
- **Zweck**: Ein praxistauglicher Ersatz, um Software auf eigentlich inkompatibler Hardware/Infrastruktur lauffähig zu machen (hat durch die Übersetzung jedoch einen spürbaren Performance-Overhead).

---

Vergleiche Voll-Virtualisierung (VM) und Prozessvirtualisierung (Container) hinsichtlich Gründe für Overhead (Speicher und CPU).
?
Die Voll-Virtualisierung startet ein komplettes Gast-Betriebssystem und reserviert physische Hardware, was zu einem großen Speicher-Overhead (3-4 GB Imagegröße) und CPU-Verlusten (durch Hypervisor-Übersetzung) führt. Die Prozessvirtualisierung teilt sich den Kernel des Hosts, enthält nur die Anwendung samt Abhängigkeiten (50-500 MB) und nutzt Kernel-Aufrufe 1:1, was nativen Speed ohne CPU-Overhead ermöglicht.

---

Wie unterscheiden sich cgroups und namespaces bei der Prozessvirtualisierung im Linux-Kernel?
?
- **cgroups (control groups)**: Schränken die *Nutzung* von physischen Ressourcen ein (z.B. CPU-Limit, RAM-Limit, GPU-Nutzung, Dateisystem-Größe).
- **namespaces**: Schränken die *Sichtbarkeit* von Systemressourcen für einen Prozess ein (z.B. sieht ein Container nur seine eigenen Prozesse [PID], Netzwerkschnittstellen [NET], Mountpoints [MNT] und unprivilegierten User).

---

Welche Vorteile entstehen durch die Kombination von Voll-Virtualisierung (VMs) und Prozessvirtualisierung (Containern)?
?
- **Sicherheits-Härtung**: Die starke Hardware-Isolation der VM schützt das Host-System vor potenziellen Ausbrüchen (Breakouts) aus dem Container.
- **Flexibilität**: Container können auf VMs betrieben werden, was das Hosten auf beliebigen Cloud-Infrastrukturen (IaaS) ermöglicht.
- **Ressourcen-Management**: VMs erlauben eine einfache, dedizierte Aufteilung von Hardwarekontingenten pro Mandant/Projekt, während Container innerhalb dieser Grenzen dynamisch skalieren.

---

Welche Vorteile bietet die Prozessvirtualisierung (z.B. Docker) für die Phasen Entwicklung, Test und Betrieb?
?
- **Entwicklung**: Schneller Start von lokalen Abhängigkeiten (z.B. Datenbanken) und vollständiges Packaging aller Bibliotheken, was "Works on my machine"-Probleme eliminiert.
- **Test**: Bereitstellung von absolut identischen, reproduzierbaren Testumgebungen in Sekunden (Dev/Test/Prod nutzen dasselbe Image).
- **Betrieb**: Extrem schnelle horizontale Skalierung (Scale-Out), hohe Ressourceneffizienz (kein Gast-OS-Overhead) und native Ausführungsgeschwindigkeit.

---

Ordne die 5 Cloud-Bereitstellungsmodelle (Private Cloud, Hybrid Cloud, Virtual Private Cloud, Public Cloud, Multi-Cloud) nach steigendem Abstraktionsgrad von der Infrastruktur.
?
`[Niedrigste Abstraktion/Höchster Wartungsaufwand] Private Cloud -> Hybrid Cloud -> Virtual Private Cloud (VPC) -> Public Cloud -> Multi-Cloud [Höchste Abstraktion]`

---

Die 7 Abstraktionsebenen der Cloud-Schichtenarchitektur (von unten nach oben) lauten:
Hardware, Hypervisor, Betriebssystem, Container, Laufzeit, Funktion, Anwendung.

---

Was sind Vorteile des geschichteten Aufbaus der Cloud-Schichtenarchitektur, angesichts dessen, dass jede Schicht zusätzlichen Wartungsaufwand verursacht?
?
Jede Schicht verbirgt die Komplexität der darunterliegenden Ebene und bietet eine klar definierte Schnittstelle. Dies ermöglicht es überhaupt erst, einzelne Ebenen modular auszulagern und die Verantwortung gezielt an spezialisierte Cloud-Provider abzugeben.

---
Welches Cloud-Servicemodell entspricht der Analogie "Leasing eines Autos"?
Infrastructure as Service (IaaS)

Welches Cloud-Servicemodell entspricht der Analogie "Mieten eines Autos"?
Container as a Service (CaaS)

Welches Cloud-Servicemodell entspricht der Analogie "Taxifahrt"?
Platform as a Service (PaaS)

Welches Cloud-Servicemodell entspricht der Analogie "Einzelfahrt im Bus"?
Function as a Service (FaaS)

Welches Cloud-Servicemodell entspricht der Analogie "Dauerkarte für den Bus"?
Software as a Service (SaaS)

---

Erkläre die 5 Automobil-/Verkehrsmittel-Analogien der Cloud-Servicemodelle (IaaS, CaaS, PaaS, FaaS, SaaS) und begründe die Zuordnung.
?
- **IaaS $\leftrightarrow$ Leasing eines Autos**: Der Kunde wählt das Auto (OS) und fährt selbst. Keine Anschaffung (CapEx), sondern eine regelmäßige Rate (OpEx). Wartung und Eigentum liegen beim Anbieter.
- **CaaS $\leftrightarrow$ Mieten eines Autos**: Das Auto wird situativ und kurzzeitig ausgewählt (Container) und selbst gefahren. Abrechnung erfolgt zeit- und kilometerbasiert (On-Demand).
- **PaaS $\leftrightarrow$ Taxifahrt**: Der Kunde fährt nicht selbst (Laufzeit/Server-Verwaltung wird vom Anbieter übernommen), sondern bestimmt nur Start und Ziel (Code/Anwendungsdaten). Abrechnung nach Strecke/Nutzung.
- **FaaS $\leftrightarrow$ Einzelfahrt im Bus**: Der Kunde nutzt ein fertiges Transportmittel für eine Teilstrecke (fertige API-Funktion) ohne Einfluss auf Route, Fahrzeiten oder Fahrzeug.
- **SaaS $\leftrightarrow$ Dauerkarte für den Bus**: Der Kunde nutzt das gesamte öffentliche Verkehrsnetz als fertiges Produkt (vollständige Anwendung), ohne jegliche Kontrolle über Betrieb oder Wartung.

---
Welche Verantwortung trägt der Kunde bei IaaS (Infrastructure as a Service)?
?
Der Provider abstrahiert Hardware und Hypervisor. Der Kunde übernimmt die volle Kontrolle und Wartungsverantwortung ab der Ebene des Betriebssystems (muss patchen, absichern, verwalten).

---
Warum entsteht bei Platform as a Service (PaaS) und Function as a Service (FaaS) ein starker Vendor Lock-in?
?
Weil der Anwendungscode tief mit proprietären Systemen des Providers verzahnt wird. Bei PaaS sind es spezifische Laufzeitumgebungen, Test- und Skalierungsfunktionen; bei FaaS sind es anbieterspezifische Programmierschnittstellen (APIs) und Funktionsblöcke.

---
Was sind zwei Vorteile und zwei Herausforderungen einer Hybrid Cloud?
?
Vorteile:
1. Kombination aus lokaler Datensouveränität für sensible Daten (Private Cloud)
2. Kurzfristige Skalierbarkeit für Lastspitzen (Bursting in die Public Cloud)

Herausforderungen:
1. Sehr hohe Konfigurationskomplexität (Netzwerk/Sicherheit)
2. Doppelte Kostenstrukturen für lokalen und Public-Cloud-Betrieb

---
Welches primäre Ziel verfolgt die Multi Cloud und welches neue Risiko entsteht dabei?
?
Das Ziel ist die Vermeidung eines Anbieter-Lock-ins (bei Public Clouds) und Kostenoptimierung durch dynamische Lastverteilung. Das neue Risiko ist die Verschiebung der Abhängigkeit auf die proprietäre, einheitliche Multi-Cloud-Verwaltungssoftware.

---
Wie unterscheidet sich Edge Computing von einer Private Cloud in Bezug auf den Anwendungsfokus?
?
Die Private Cloud fokussiert sich auf die zentrale Datensouveränität in einem lokalen Rechenzentrum. Edge Computing dezentralisiert die Verarbeitung direkt an den Entstehungsort der Daten (z.B. Sensoren), fokussiert auf Echtzeitverarbeitung (Latenzminimierung) und die Reduktion von Bandbreitenbedarf.

---
Airgap-Umgebungen::Infrastrukturkonfigurationen (oft in einer Private Cloud), die physisch oder logisch komplett vom Internet isoliert sind, um maximale Sicherheit zu gewährleisten.

---

### 3. Docker Grundlagen & Copy-On-Write

Auf welchen beiden Linux-Kernelfunktionen basiert die Prozessvirtualisierung mit Docker?
cgroups (Ressourcen-Limits) und namespaces (Sichtbarkeits-Limits)

---
Erkläre das Prinzip von Copy-On-Write bei der Verwendung von Docker.
?
Das Docker Image selbst ist read-only (schreibgeschützt). Startet man einen Container, erhält dieser eine temporäre, beschreibbare R/W-Schicht. Soll eine Datei im Container geändert werden, wird sie zuerst aus dem schreibgeschützten Image in diese temporäre Schicht kopiert ("Copy") und nur dort modifiziert ("Write"). Beim Beenden des Containers wird die gesamte Schicht restlos gelöscht.

---
Was bewirken die Parameter -d, -p und -it beim Befehl 'docker container run'?
?
-d (detached): Container läuft im Hintergrund.
-p (publish): Leitet einen Host-Port auf einen Container-Port um (HostPort:ContainerPort).
-it (interactive, tty): Ersetzt das Startkommando und erlaubt eine interaktive Befehlseingabe (z.B. eine Bash-Shell) im Container.

---
Was bewirkt die Option '--rm' beim Befehl 'docker container run'?
?
Sie sorgt dafür, dass der Docker Container nach seinem Beenden (Stoppen) automatisch und restlos vom System gelöscht wird.

---
Was bedeuten die vier Abschnitte eines Docker Image Tags (z.B. registry/user/image:version)?
?
1. Adresse der Registry (optional, Standard ist Docker Hub)
2. User/Organisation (Pflichtfeld, außer bei offiziellen Images)
3. Imagename (Pflichtfeld)
4. Version (optional, wird ohne Angabe automatisch zu 'latest')

---
Warum ist das Weglassen einer expliziten Version, sodass 'latest' gesetzt wird, strikt zu vermeiden?
?
Weil 'latest' keine Aktualität garantiert, sondern nur ein Standardwert für eine unbekannte Version ist. Es referenziert potenziell verschiedene Stände auf Client und Registry, verhindert reproduzierbare Builds und macht Rücksprünge (Rollbacks) unmöglich.

---
Was für ein Problem kann durch das Verwenden eines statischen Versionstags (wie :1 oder :latest) in Kombination mit einem Orchestrator (z.B. Kubernetes) auftreten?
?
Wird ein Image aktualisiert, aber unter exakt demselben statischen Tag gepusht, erkennt der Orchestrator die Änderung oft nicht, da sich der Name des Tags nicht geändert hat. Die laufenden Container werden dann nicht durch die neue Version ersetzt.

---
Nenne zwei Strategien, wie sich "unique Tags" für ein selbst erstelltes Image ableiten lassen, um fehlerhaftes Caching zu verhindern.
?
1. Nutzung des Git-Commit-Hashes des Quellcodes.
2. Nutzung einer eindeutigen Build-ID aus der CI/CD-Pipeline.

---

- Nenne die Docker-Kommandozeilen-Befehle für folgende Aufgaben. Image aus Dockerfile im aktuellen Ordner bauen (mit Tag exam:1)::`docker image build -t exam:1 .`
- Nenne die Docker-Kommandozeilen-Befehle für folgende Aufgaben. Schichten eines Images anzeigen::`docker image history exam:1`
- Nenne die Docker-Kommandozeilen-Befehle für folgende Aufgaben. Laufende und gestoppte Container listen::`docker container list -a`
- Nenne die Docker-Kommandozeilen-Befehle für folgende Aufgaben. Image aus lokaler Ablage löschen::`docker image rm <name>`
- Nenne die Docker-Kommandozeilen-Befehle für folgende Aufgaben. Logs eines Containers ansehen::`docker container logs <container-id>`
- Nenne die Docker-Kommandozeilen-Befehle für folgende Aufgaben. Ressourcenverbrauch von Containern anzeigen::`docker container stats <container-id>`

---

Wie startet man einen zuvor gestoppten interaktiven Container erneut, sodass man wieder interaktiv Befehle eingeben kann?
?
Mit dem Befehl `docker container start -i <container-id>` (die Option `-i` / `--interactive` hält standardmäßig das Terminal/die Standardeingabe offen).

---

Wie funktioniert der Docker Build-Cache und wie wird seine Gültigkeit überprüft?
?
Beim Ausführen von `docker image build` prüft der Docker-Daemon jede Zeile des Dockerfiles von oben nach unten gegen den Cache:
1. Für `COPY` und `ADD`: Es wird ein Hash/Prüfsumme der lokalen Quelldateien berechnet. Stimmt dieser mit dem Cache überein, wird die Schicht wiederverwendet.
2. Für andere Befehle (z.B. `RUN`): Es wird der reine Text der Anweisung verglichen.
Tritt bei einer Zeile ein Cache-Miss auf (z.B. geänderter Quellcode oder anderer Befehl), werden diese Schicht und **alle darauf folgenden Schichten** ungültig und müssen neu gebaut werden.

---

### 4. Dockerfile Best Practices & Security

Warum fordert die Schichtenarchitektur, dass Befehle im Dockerfile streng nach ihrer Änderungsfrequenz abwärts sortiert werden?
?
Weil Docker einen Build-Cache nutzt. Ändert sich ein Befehl oder eine kopierte Datei, ändert sich die Prüfsumme dieser Schicht. Diese Schicht und zwingend alle darunterliegenden Schichten müssen dann neu gebaut werden. Häufige Änderungen (wie Quellcode) müssen daher ganz nach unten.

---
Warum sollten zusammengehörige Befehle im Dockerfile (wie apk update und apk add) mit && kombiniert werden?
?
Da jede Instruktion im Dockerfile (wie RUN) eine eigene, physische read-only Schicht erzeugt. Die Bündelung mit && vermeidet redundante, unnötige Schichten und spart massiv Speicherplatz.

---
Warum ist es nicht sinnvoll, einen SSH Server im Docker Container zu installieren?
?
Es bricht das fundamentale Prinzip der Prozess-Isolierung ("Ein Prozess pro Container") und vergrößert die Angriffsfläche massiv. Für Debugging-Zwecke nutzt man stattdessen den nativen Befehl `docker container exec`.

---
Kann man in das Dockerfile den Befehl 'mvn clean install' aufnehmen? Was ist die Konsequenz hiervon?
?
Architektonisch ist das ein Fehler (Anti-Pattern). Die Konsequenz ist, dass der gesamte Quellcode, das Build-Werkzeug und Gigabytes an Abhängigkeiten dauerhaft in das Image "eingebacken" werden. In ein finales Image gehört nur das bereits fertig kompilierte Artefakt (z.B. app.jar).

---
Welche Dockerfile-Instruktion ist als Dokumentation notwendig, damit ein Container anzeigt, dass er intern auf Port 8000 horcht?
?
EXPOSE 8000

---
Wie stellt man in einem Dockerfile sicher, dass eine Variable nur zur Bauzeit des Images, aber nicht mehr zur Laufzeit des Containers verfügbar ist?
?
Indem man den Befehl ARG anstelle von ENV verwendet.

---
Nenne zwei Docker-Optionen für den 'docker container run' Befehl, mit denen sensible Daten (Passwörter) übergeben werden können, ohne sie ins Dockerfile zu schreiben.
?
1. `--env` (oder `-e`) für die direkte Übergabe einzelner Variablen.
2. `--env-file` zum Einlesen einer kompletten Datei mit Umgebungsvariablen.

---
Welches Sicherheitsrisiko birgt die Shell-Notation beim CMD-Befehl (z.B. CMD java -jar app.jar) und was ist die Alternative?
?
Bei der Shell-Notation wird die Anwendung als Unterprozess einer Shell gestartet. Bricht ein Angreifer aus, hat er Zugriff auf alle Shell-Werkzeuge. Man sollte zwingend die Exec-Notation in Array-Form verwenden (z.B. `CMD ["java", "-jar", "app.jar"]`).

---
Wie setzt man die Non-Root Ausführung als Best Practice in einem Dockerfile um?
?
Da Prozesse standardmäßig als "root" laufen, legt man mit `RUN addgroup ... && adduser ...` einen eigenen unprivilegierten Benutzer und eine Gruppe an. Danach nutzt man den Befehl `USER <Benutzername>`, damit alle folgenden Befehle und der Container-Start unter diesem sicheren Account laufen.

---
Wie lassen sich in einer Spring Boot Anwendung (im Container) unterschiedliche Sprachprofile (z.B. 'dev' oder 'prod') steuern?
?
Über die Nutzung von Spring Profilen. Diese werden meist über eine Umgebungsvariable gesteuert, indem man dem Container zur Laufzeit den Wert übergibt, z.B. via `--env Spring.profiles.active=prod`.

---
Um in Java zu überprüfen, ob ein String (z.B. ein API-Key im Header) mit einem anderen String inhaltlich exakt übereinstimmt, verwendet man die Methode:
string_1.contentEquals(string_2)

---

Das Kommando WORKDIR setzt im Container das Ausgangsverzeichnis für alle folgenden Kommandos, sodass das Wiederholen gleicher Verzeichnispräfixe entfällt und Fehler vermieden werden.

---

Warum sollten COPY-Befehle im Dockerfile so präzise wie möglich formuliert werden und Wildcards (wie `COPY target/*`) vermieden werden?
?
Weil Wildcards dazu führen, dass bei jeder minimalen Änderung an *irgendeiner* Datei im Quellordner (auch irrelevanten) der Build-Cache für diese Schicht und alle folgenden Schichten ungültig wird. Ein präziser Befehl (z.B. `COPY target/app.jar .`) verifiziert gezielt nur das fertige Artefakt und erhält die Cache-Effizienz.

---

In welcher Reihenfolge werden Umgebungsvariablen in Docker ausgewertet und welche Priorität haben sie beim Überschreiben?
?
Von niedriger zu hoher Priorität (wobei spätere Werte frühere überschreiben):
1. Definitionen im Dockerfile (`ENV`)
2. Werte aus einer Datei, die per `--env-file` übergeben wird (Laufzeit)
3. Einzelne Laufzeitargumente via `--env` (oder `-e`) beim Container-Start (`docker run`)

---

### 5. On-Premise & Cloud-Vergleich

Warum führt das traditionelle On-Premise Hosting bei neuen Projekten oft zu "Worst-Case-Sizing" und Opportunitätskosten?
?
Weil Ressourcen zu einem sehr frühen Zeitpunkt beantragt werden müssen, an dem der tatsächliche Bedarf noch unklar ist. Aus Angst vor späteren Engpässen wird oft das Doppelte der eigentlich benötigten Hardware gekauft. Das bindet unnötig Kapital (Opportunitätskosten), welches an anderer Stelle fehlt (besonders kritisch für Start-ups).

---
Welches konkrete Problem ergibt sich beim On-Premise Betrieb auf geteilten Servern bezüglich Updates von Laufzeitumgebungen?
?
Ein Konsenszwang: Aktualisierungen geteilter Komponenten (z.B. Java-Laufzeitumgebung oder Datenbank) können oft erst durchgeführt werden, wenn alle Anwendungen auf diesem Server die neue Version unterstützen. Das führt zur Verteidigung des Status Quo und hemmt Innovationen.

---
Welche Rolle spielen "Skaleneffekte" (Fixkostendegression) für Cloud Provider und welche drei Bereiche profitieren davon besonders?
?
Cloud Provider können massive Investitionen auf sehr viele Kunden umlegen, wodurch die Stückkosten sinken. Davon profitieren für den Endkunden besonders:
1. Leistung: High Performance Computing wird auch für normale Nutzer bestellbar.
2. Sicherheit: Enorme Budgets für Red Teams und DDoS-Schutz.
3. Ausfallsicherheit: Weltweite Infrastruktur und hochverfügbarer Speicher (integrierte Backups).

---
Warum sind die reinen monatlichen Server-Mietkosten in der Cloud oft höher als beim On-Premise Hosting, und warum rechnet es sich wirtschaftlich meist dennoch?
?
Die sichtbaren monatlichen Cloud-Kosten (Nutzungsentgelte) sind oft höher. Der Kostenvorteil der Cloud entsteht jedoch durch den Wegfall verdeckter Kosten (Umlagekosten) für den On-Premise-Betrieb, wie Personalaufwand für die Wartung, Klimatisierung, Strom und Hardware-Upgrades.

---

Wie berechnen sich die monatlichen Kosten für einen On-Premise Server (am Beispiel Dell PowerEdge R740 aus den Slides) und wie stehen sie im Vergleich zu Azure?
?
- **Hardware (Abschreibung)**: Anschaffung 2.214,16€ / 3 Jahre Abschreibung (36 Monate) = **61,50€/Monat**
- **Stromkosten**: 750 Watt Vollauslastung. Bei 30% typischer Auslastung = 162 kWh. Multipliziert mit dem PUE-Faktor 1,58 (Kühlung/Verlustleistung) = 255,96 kWh. Bei 0,30€/kWh = **76,79€/Monat**
- **Personalkosten**: 3h Wartung/Monat bei 28€/h (basierend auf 44.000€ Jahresgehalt / 1567h) = **84,00€/Monat**
- **Gesamtkosten**: 61,50€ + 76,79€ + 84,00€ = **222,29€/Monat** (ca. 40% günstiger als Azure D4 v4 mit 4 vCPU, 16GB RAM für **313,82€/Monat**).

---

Warum ist der Betrieb in der Cloud trotz höherer reiner monatlicher Server-Mietpreise (z.B. 313,82€ vs. 222,29€) oft wirtschaftlicher?
?
Weil in den reinen On-Premise Kosten viele indirekte/unquantifizierte Umlagekosten fehlen:
1. **Redundanz & Sicherheit**: Physischer Objektschutz, Notstromdiesel, DDoS-Schutz, Red Teams.
2. **Skalierung & Flexibilität**: On-Demand Zubuchung/Abbestellung verhindert Überprovisionierung (Worst-Case-Sizing) und hohe Opportunitätskosten.
3. **Ausfallsicherheit**: Backup-Infrastruktur, gespiegelter Speicher (z.B. SAN über 2 Standorte).
4. **Verteilte Infrastruktur**: Globale Verteilung minimiert Latenzen für Endkunden.

---
Nenne typische Ursachen, warum Unternehmen ihr Cloud-Budget oft massiv überschreiten.
?
- "Lift-and-Shift": Alte, nicht für die Cloud optimierte Anwendungen werden unverändert verschoben und verschwenden Ressourcen.
- "Zombie-Server": Nicht mehr benötigte Test-Ressourcen werden vergessen und nicht deprovisioniert.
- Zu sorglose Nutzung attraktiver (aber teurer) Cloud-Features durch Entwickler.

---
Welche drei konkreten Probleme entstehen durch den Wegfall einer zentralen IT-Governance im Cloud Computing?
?
1. Gesetzesverstöße: DSGVO-Probleme, wenn Entwickler Daten versehentlich in falschen Regionen (weltweit) speichern.
2. Qualitätsverlust: Unternehmensweite Standards für Daten- und Codequalität können schwerer durchgesetzt werden.
3. Fehlende Synergien: Lösungen werden in isolierten Teams mehrfach programmiert (Wiederverwendbarkeit sinkt).

---
Was ist das primäre Ziel von Continuous Integration (CI) im Cloud-Umfeld?
?
Die automatisierte Durchführung von statischer Codeanalyse, Buildskripten und Tests (Unit/Integration) bei jeder Code-Änderung. So soll sichergestellt werden, dass Inkompatibilitäten, die durch parallele Programmierungstätigkeit in Teams entstehen, so früh wie möglich erkannt werden.

---
Nenne die drei Hauptgründe für den Einsatz von Virtualisierung im Anwendungsbetrieb.
?
1. Isolation: Eindämmung von Laufzeitfehlern (Sandboxing) und getrennte Bibliotheken.
2. Multiplizität: Parallelbetrieb mehrerer (Alt- und Neu-)Systeme auf derselben Hardware zur Fixkostendegression.
3. Portabilität: Einfacher Umzug auf neue Hardware und exakte Kopien der Systemkonfiguration für Testumgebungen.

---
Unterscheide Typ I (Bare-Metal) und Typ II (Hosted) Hypervisor hinsichtlich Architektur und Vor-/Nachteilen.
?
Typ I (Bare-Metal): Sitzt direkt auf der Hardware (z.B. ESX-i). Bietet höchste Performance und Sicherheit, da keine Angriffsfläche durch ein darunterliegendes Host-Betriebssystem besteht.
Typ II (Hosted): Wird als Anwendung auf einem vollwertigen Host-Betriebssystem installiert (z.B. VirtualBox). Hat Performance-Verluste durch die doppelte Übersetzung und geringere Sicherheit, erlaubt aber die multifunktionale Nutzung des Host-Rechners für andere Desktop-Anwendungen.

---
Was versteht man unter Para-Virtualisierung und was ist ihr entscheidender architektonischer Nachteil?
?
Bei der Para-Virtualisierung wird das Gast-Betriebssystem aktiv angepasst, sodass es Hardware-Ressourcen nicht direkt anspricht, sondern über virtuelle Treiber direkte API-Aufrufe an den Hypervisor sendet. Das bringt eine extrem hohe Performance.
Nachteil: Da das Betriebssystem tiefgreifend modifiziert werden muss, ist dies nur mit Open-Source-Systemen (wie Linux) möglich, nicht aber mit proprietären Systemen wie Windows.

---
Warum ist die Isolation bei Containern (Prozessvirtualisierung) schwächer als bei virtuellen Maschinen (Voll-Virtualisierung)?
?
Virtuelle Maschinen sind strikt isoliert und sehen nur logisch abstrahierte Hardware. Container teilen sich den Kernel des Host-Betriebssystems und die Prozesse sehen die echte physische Hardware. Das Risiko von Ausbrüchen (Breakouts) durch Angreifer aus dem Container auf das Host-System ist dadurch höher.

---
Was ist eine Virtual Private Cloud (VPC) und wie unterscheidet sie sich von einer klassischen Private Cloud?
?
Eine VPC nutzt die Infrastruktur einer Public Cloud, isoliert dort aber einen geschlossenen Netzwerkbereich, der von außen nicht sichtbar und nur über VPN erreichbar ist. Eine klassische Private Cloud wird hingegen vollständig auf eigener, lokaler Hardware (im eigenen Rechenzentrum) betrieben.

---
Aus welchen zwei zentralen Bestandteilen besteht die Docker-Architektur und was sind ihre Aufgaben?
?
1. Docker-Client: Ein Kommandozeilen-Werkzeug, das Befehle des Nutzers entgegennimmt und via REST-API weiterleitet.
2. Docker-Daemon (Server): Nimmt die Befehle entgegen, lädt Images von der Registry, erstellt und verwaltet die laufenden Container.

---
Welches Paradigma aus der Frachtschifffahrt übernimmt Docker und welche drei Vorteile ergeben sich daraus für die IT?
?
Das Paradigma des Standardcontainers. Daraus ergeben sich:
1. Planungssicherheit: Eine standardisierte Infrastruktur macht Dauer und Kosten planbar.
2. Performance: Sehr schnelle Bereitstellung (Ladung/Entladung) durch einheitliche Werkzeuge.
3. Sicherheit: Reduktion von "Transportschäden" und unvorhersehbaren Fehlern durch standardisierte und isolierte Umgebungen.

---
Woran erkennt man ein offizielles Docker Image auf dem Docker Hub und was ist der Vorteil dieser Images?
?
Offizielle Images haben keinen User- oder Organisationsnamen im Tag (z.B. nur `ubuntu` statt `user/ubuntu`). Der Vorteil ist, dass Docker ein eigenes Team unterhält, das diese Images pflegt, regelmäßig aktualisiert und ihre Authentizität sicherstellt.

---
Warum sollte als Baseimage eine möglichst kleine Linux-Distribution (z.B. `alpine` mit ca. 5 MB statt `ubuntu` mit ca. 188 MB) gewählt werden? Nenne drei Gründe.
?
1. Die Download- und Upload-Dauer wird reduziert.
2. Der benötigte Speicherbedarf sinkt.
3. Die Angriffsfläche für potenzielle Sicherheitslücken wird verringert.

---
Warum muss ein eigenes Image zwingend neu gebaut werden, wenn das zugrundeliegende Baseimage (z.B. mit Sicherheitspatches) aktualisiert wurde?
?
Weil es kein automatisches Update von Images gibt und alle Anpassungen in laufenden Containern flüchtig sind. Dauerhafte Veränderungen und Sicherheitspatches lassen sich nur durch den vollständigen Neubau (Build-Prozess) in das eigene Image integrieren.

---
Für welche drei typischen Anwendungsfälle nutzt man Umgebungsvariablen in einer Spring Boot Anwendung innerhalb eines Docker Containers?
?
1. Endpunkte & Ressourcen: Steuerung von Datenbank-URLs je nach Umgebung (Dev vs. Prod).
2. Sicherheit: Übergabe sensibler Daten (Passwörter), damit diese nicht fest im Code oder in Logdateien stehen.
3. Feature-Toggles: Beschränkung des Funktionsumfangs je nach Laufzeitumgebung.

---
Ordne den fünf Cloud-Servicemodellen (IaaS, CaaS, PaaS, FaaS, SaaS) das jeweils primäre "Nutzungsobjekt" aus der Schichtenarchitektur zu.
?
- IaaS: Betriebssystem (OS)
- CaaS: Container
- PaaS: Laufzeitumgebung (Runtime)
- FaaS: Funktion
- SaaS: Anwendung

---
Warum wird eine REST-Methode, die im Java-Code mit `@Profile("dev")` annotiert ist, nicht aufgerufen, wenn im Dockerfile der Befehl `ENV Spring.profiles.active="prod"` steht?
?
Weil das Dockerfile das aktive Profil zur Laufzeit auf `prod` setzt. Die Spring Boot Anwendung ignoriert daraufhin alle Klassen oder Methoden, die explizit an das `dev`-Profil gebunden sind. Es handelt sich um einen Profil-Mismatch.

---
Wie kann man in einem Dockerfile eine Liste von Werten (z.B. Vornamen) definieren und in eine Klassenvariable (z.B. `String[] specialNames`) einer Spring Boot Anwendung laden?
?
1. **Im Dockerfile**: Die Werte als kommagetrennte Liste per Umgebungsvariable übergeben:
   `ENV specialNames="Check,Siri,CoolAid"`
2. **Im Java-Code (RestController)**: Die Variable mit der `@Value`-Annotation versehen, damit Spring Boot den Wert aus der Umgebungsvariable automatisch splittet und injiziert:
   `@Value("${specialNames}") String[] specialNames;`


---
Eine Spring Boot Anwendung ist so programmiert, dass sie intern auf Port 8000 horcht. Der Container startet fehlerfrei, aber es kommen von außen keine Netzwerkanfragen an. Welcher Befehl fehlt höchstwahrscheinlich im Dockerfile?
?
Der Befehl `EXPOSE 8000`. Ohne diesen dokumentierten Port lässt der Container standardmäßig keine eingehenden Netzwerkverbindungen auf diesem Port zu (unabhängig vom `-p` Flag beim `docker run`).

---
Schreibe ein optimiertes Dockerfile für eine Spring Boot App (`app.jar`), das folgende Best Practices umsetzt: Explizites Baseimage (Alpine), ARG statt ENV für Build-Variablen, Non-Root-User (`java` in Gruppe `javagr`), explizites Arbeitsverzeichnis (`app`), minimales COPY, EXPOSE 8000 und die Exec-Notation.
?
```
# Base image with explicit version tag
FROM openjdk:16-jdk-alpine

# Create unprivileged group and user for security
RUN addgroup -S javagr && adduser -S java -G javagr

# Build-time variable (not available at runtime)
ARG STAGE=prod

# Create and set working directory
RUN mkdir app
WORKDIR app

# Copy only the necessary executable artifact
COPY target/app.jar .

# Switch to unprivileged user
USER java

# Document the port the application listens on
EXPOSE 8000

# Start application using exec notation
CMD ["java", "-jar", "app.jar"]
```