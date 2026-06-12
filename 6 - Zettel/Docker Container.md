#Note

2026-06-12

Tags: [[Virtualisierung]], [[Docker]], [[Systemarchitektur]]
#cloud_computing

---
Vom Rezept zur aktiven Laufzeitumgebung

Um die Architektur von Docker zu meistern, muss die fundamentale Trennung zwischen Zustand und Prozess verstanden werden. Ein [[Docker Image]] ist lediglich eine read-only Beschreibung der Laufzeitumgebung und des auszuführenden Prozesses – es ist selbst nicht ausführbar. Der **Docker Container** hingegen ist die aktive Laufzeit-Repräsentation dieses Images. Wird ein Image ausgeführt, wird eine isolierte Kopie instanziiert. Da Container keine Hardwarebindung besitzen und keinen trägen Betriebssystem-Kernel booten müssen, lassen sie sich extrem leicht und in Millisekundenbruchteilen replizieren. Dies bildet das perfekte architektonische Fundament für massive [[Horizontale Skalierung]].

Flüchtigkeit und das Copy-On-Write Prinzip

Das kritischste Design-Paradigma eines Docker Containers ist seine garantierte Zustandslosigkeit (Statelessness). Bei der Ausführung eines Images werden alle Instruktionen in ein striktes read-only Dateisystem überführt. Da Anwendungen zur Laufzeit jedoch zwingend Dateien schreiben müssen (z.B. Logfiles, temporäre Caches), erhält jeder Docker-Container eine zusätzliche **beschreibbare Schicht (Read/Write-Layer)**.

Muss eine bestehende Datei des Images modifiziert werden, greift das **[[Copy-On-Write]]** Prinzip: Die Datei wird aus der unteren, read-only Schicht in die beschreibbare Schicht heraufkopiert und erst dort verändert. Das Original-Image bleibt auf ewig unangetastet. Die architektonische Konsequenz: **Nach Beenden des Docker Containers wird diese gesamte beschreibbare Schicht unwiderruflich gelöscht**. Jeder Neustart eines Containers aus demselben Image beginnt wieder bei einem absolut makellosen, identischen Nullzustand.

Orchestrierung und Laufzeitkontrolle

Der Lebenszyklus eines Containers wird vollständig durch den Docker Daemon gesteuert. Wird der Befehl `docker container run` abgesetzt, prüft der Daemon, ob das Image lokal vorliegt, lädt es andernfalls aus einer Registry herunter, erstellt den Container und gibt dessen Output an die Kommandozeile weiter (Attached Mode).

Um das Verhalten in professionellen Cloud-Umgebungen zu steuern, erzwingt die Systemarchitektur spezifische Laufzeitoptionen:

- **Port-Publishing (****-p****):** Da Container netzwerktechnisch isoliert sind, leitet diese Option gezielt Traffic vom Host-Betriebssystem an definierte Ports des Containers weiter (z.B. Port 80 zu 80).
- **Detached Mode (****-d****):** Entkoppelt den Container von der Kommandozeile und lässt ihn als echten Service im Hintergrund laufen.
- **Interactive Mode (****-it****):** Ersetzt Startkommandos und öffnet eine interaktive Shell innerhalb der isolierten Umgebung, primär für Debugging-Zwecke.

---

### Flashcards

Was ist der fundamentale architektonische Unterschied zwischen einem Docker Image und einem Docker Container in Bezug auf ihren Ausführungszustand?
?
Das Docker Image ist die statische, schreibgeschützte (Read-Only) Beschreibung der Laufzeitumgebung (das "Rezept") und selbst nicht ausführbar. Der Docker Container ist die aktive, flüchtige Laufzeit-Repräsentation dieses Images (der "laufende Prozess"), der keine Hardwarebindung besitzt und massenhaft repliziert werden kann.

Wie löst der Docker Container das Problem, Dateianpassungen zur Laufzeit vornehmen zu können, obwohl das zugrundeliegende Dateisystem des Images strikt schreibgeschützt (Read-Only) ist?
?
Durch eine zusätzliche beschreibbare Schicht (Read/Write-Layer) und das **Copy-On-Write** Prinzip. Zu ändernde Dateien werden aus dem Image in diese temporäre Schicht kopiert und nur dort modifiziert. Wird der Container beendet, wird diese gesamte Schreibschicht unwiderruflich gelöscht.

Welche drei zentralen Parameter können beim Befehl `docker container run` mitgegeben werden, um das Netzwerk- und Ausführungsverhalten des Containers in der Architektur maßgeblich zu steuern?
?
1. **-p** **(Publish):** Leitet Netzwerkverkehr vom Host-System an einen definierten Port des Containers weiter.
2. **-d** **(Detached):** Startet den Container im Hintergrund, anstatt die aktuelle Kommandozeile zu blockieren.
3. **-it** **(Interactive & TTY):** Ermöglicht eine interaktive Befehlseingabe innerhalb des Containers, indem Startkommandos ersetzt werden.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Docker Container]]
SORT file.mtime DESC
```