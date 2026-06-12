#Note

2026-06-12

Tags: [[Systemarchitektur]], [[Cloud Computing]], [[Docker]], [[DevOps]]
#cloud_computing

---
In der Vorlesung und Systemarchitektur wird der Begriff der **Schichtenarchitektur** in zwei fundamentalen, aber miteinander verwandten Kontexten verwendet: makroskopisch zur Definition von Cloud-Betriebsmodellen und mikroskopisch zur Konstruktion von Container-Laufzeitumgebungen.

1. Makroskopisch: Die 7 Abstraktionsebenen der Cloud

Um Cloud-Dienstleistungen architektonisch voneinander abzugrenzen, wird ein Schichtenmodell herangezogen, das die Abhängigkeiten eines Computersystems von der physischen Basis bis zur Endnutzer-Funktionalität beschreibt,. Es besteht aus 7 Ebenen:

1. **Hardware:** Die physischen Ressourcen (CPU, RAM, Netzwerk),.
2. **Hypervisor:** Verwaltet den Betrieb virtueller Maschinen,.
3. **Betriebssystem (OS):** Stellt den Kernel und Basis-Bibliotheken bereit,.
4. **Container:** Isolierte Prozessumgebungen auf Basis des geteilten OS-Kernels,.
5. **Laufzeit (Runtime):** Stellt Ausführungsumgebungen (z.B. Java) bereit,.
6. **Funktion:** Einzelne algorithmische Operationen oder Programmfunktionen,.
7. **Anwendung:** Die interaktive, finale Applikation,.

**Der Trade-off der Schichten:** Dieses Modell definiert die unterschiedlichen Cloud-Servicemodelle (IaaS, CaaS, PaaS, FaaS, SaaS). Je weiter oben in dieser Schichtenarchitektur der Schnitt gemacht wird (also je mehr Schichten der Cloud-Provider verantwortet), desto geringer wird der operative Wartungsaufwand für das Unternehmen,. Im exakt gleichen Gegenzug sinkt jedoch die Kontrolle drastisch, was die Gefahr eines massiven Vendor-Lock-ins (Bindung an den Anbieter) massiv erhöht,,.

2. Mikroskopisch: Die Schichtenarchitektur von Docker Images

Auf der Container-Ebene nutzt Docker das Prinzip der Schichtenarchitektur, um das Problem monströser, redundanter virtueller Maschinen (die oft 3-4 GB groß sind) zu lösen. Ein [[Docker Image]] ist keine monolithische Binärdatei, sondern besitzt einen **strukturierten Aufbau in Schichten (Layers)**,. Jede deklarative Anweisung im [[Dockerfile]] (z.B. ein `RUN` oder `COPY` Befehl) erzeugt eine eigene, unveränderliche Schicht samt kryptografischer Prüfsumme.

Diese Architektur ermöglicht zwei massive Effizienzgewinne für verteilte Systeme:

- **Deduplikation:** Jede Schicht wird physisch **nur ein einziges Mal gespeichert**. Wenn hunderte Images im Unternehmen dieselbe Basisschicht (z.B. Ubuntu) nutzen, belegt diese Schicht nur einmal Speicherplatz und muss bei einem Download (Pull) nicht redundant über das Netzwerk übertragen werden.
- **Der Build-Cache:** Beim Bauen eines Images gleicht der Docker-Daemon die Prüfsummen von oben nach unten ab. Haben sich Instruktionen nicht geändert, wird die Schicht in Millisekunden aus dem Cache geladen.

**Architektonischer Imperativ (Best Practice):** Diese Effizienz kollabiert jedoch bei schlechtem Systemdesign. Ändert sich eine Schicht (z.B. weil neuer Applikationscode kopiert wird), wird ihre Prüfsumme ungültig. **Die Konsequenz: Diese Schicht und alle darauf basierenden (darunterliegenden) Schichten müssen zwingend neu gebaut werden**,. Daher zwingt die Schichtenarchitektur Entwickler dazu, Befehle streng nach ihrer **Änderungsfrequenz** zu sortieren: Seltene Änderungen (wie Basisimages und Paketinstallationen) müssen ganz oben stehen, hochfrequente Änderungen (Kopieren von Code) zwingend ganz unten,. Um unnötige Schichten und "Image Bloat" zu vermeiden, müssen zusammengehörige Befehle zudem mit `&&` kombiniert werden.

---

### Flashcards

Welche 7 Abstraktionsebenen bilden die makroskopische Schichtenarchitektur als Grundlage für die Definition von Cloud-Dienstleistungen (von unten nach oben)?
?
1. Hardware, 2. Hypervisor, 3. Betriebssystem, 4. Container, 5. Laufzeit (Runtime), 6. Funktion, 7. Anwendung,.

Welcher fundamentale Trade-off (Zielkonflikt) entsteht bei der Entscheidung, auf welcher Ebene der Cloud-Schichtenarchitektur die Verantwortlichkeit an den Provider abgegeben wird?::Je mehr Schichten der Cloud-Provider übernimmt (z.B. bei SaaS oder PaaS), desto mehr sinkt der operative Wartungsaufwand für den Kunden. Im Gegenzug sinkt jedoch die Kontrolle massiv und das Risiko eines Vendor-Lock-ins (starke Bindung an den Anbieter) steigt signifikant,,.

Warum muss ein [[Dockerfile]] aufgrund der Docker-Schichtenarchitektur zwingend nach der "Änderungsfrequenz" der Befehle (von gering zu hoch) aufgebaut sein?::Weil Docker beim Bauen einen Cache nutzt, der Schichten anhand von Prüfsummen vergleicht. Ändert sich ein Befehl, werden diese Schicht **und alle darauf folgenden Schichten** ungültig und müssen neu gebaut werden. Steht eine häufige Änderung oben, wird der gesamte Cache bei jedem Build nutzlos zerstört,,.

Wie löst die Schichtenarchitektur von Docker das Problem massiver redundanter Speicherbelegung und langsamer Netzwerktransfers bei der Bereitstellung von Laufzeitumgebungen?::Durch Deduplikation. Jede generierte Schicht wird samt Prüfsumme nur **ein einziges Mal gespeichert**. Nutzen mehrere Images identische Schichten (z.B. dieselbe OS-Basis), belegen diese nur einmal Speicher und beim Herunterladen (Pull) werden immer nur jene Schichten übertragen, die auf dem Zielsystem noch fehlen.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Schichtenarchitektur]]
SORT file.mtime DESC
```