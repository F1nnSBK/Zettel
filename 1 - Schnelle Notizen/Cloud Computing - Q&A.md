#cloud_computing_qa
## Thema 1: Grundlagen und Motivation (PDF 1)

Warum ist Cloud Computing ein radikaler Paradigmenwechsel zum traditionellen On-Premise-Betrieb und welche strukturellen Folgen hat das für Unternehmen?
?
Leitfrage: Thema 1 (Grundlagen und Motivation)

Was sind „Server-Festungen“, wodurch entstehen sie und warum sind sie ein Problem für den Betrieb?
?
Lernziel: Den Schmerz des On-Premise-Betriebs (z.B. Server-Festungen, Schneeflocken-Effekt) erklären.

Nennen und erläutern Sie 4 Vorteile des Cloud Computings (z.B. Fixkostenvariabilisierung, Skaleneffekte, On-Demand).
?
Lernziel: Die sechs zentralen Vorteile der Cloud benennen und wirtschaftlich argumentieren.

Warum sprengen Cloud-Projekte oft das Budget (Kostenmanagement) und welche neuen Sicherheitsrisiken (API-Nutzung, Datenabfluss) entstehen?
?
Lernziel: Die neuen Herausforderungen der Cloud (Kosten, Sicherheit, fehlendes Know-how) einordnen.

Erläutern Sie das Prinzip „mutable infrastructure“ im Gegensatz zur „immutable infrastructure“.
?
Lernziel: Mutable vs. Immutable Infrastructure unterscheiden.

Wie argumentiere ich in der Klausur zum Thema Grundlagen und Motivation (Cloud-Vorteile und Risiken)?
?
Klausurstrategie: Argumentiere wirtschaftlich und architektonisch, nicht nur technisch!
- Vorteile: Schreibe nicht nur „es ist billiger“, sondern verwende den Begriff Fixkostenvariabilisierung (Zahlen nach tatsächlichem Aufwand statt hohem Vorab-Investment).
- Risiken: Wenn nach Sicherheit gefragt wird, nenne nicht „Hacker“, sondern spezifische Cloud-Risiken: Weltweite Sichtbarkeit ungesicherter APIs, Fehlkonfiguration von Speicher-Rechten, Fehlen physischer Zugangskontrollen.

---

## Thema 2: Virtualisierung, Servicemodelle & Bereitstellung (PDF 2)

Wie definiert das Maß der abgegebenen Kontrolle die jeweilige Cloud-Dienstleistung und welches Bereitstellungsmodell passt zu welcher Anforderung?
?
Leitfrage: Thema 2 (Virtualisierung, Servicemodelle & Bereitstellung)

Benennen Sie die 7 Abstraktionsebenen (Hardware bis Anwendung) und ordnen Sie die Cloud-Servicemodelle (IaaS bis SaaS) dem jeweiligen Nutzungsobjekt zu.
?
Lernziel: Die 7 Abstraktionsebenen der Cloud-Architektur beherrschen.

Was sind die Vorteile eines geschichteten Aufbaus, angesichts dessen, dass jede Schicht eigentlich Overhead bedeutet?
?
Lernziel: Den Trade-off zwischen Wartungsaufwand und Lock-in-Risiko argumentieren.

Welche Dienstleistungsstufe des Cloud Computing hat Parallelen zum Mieten eines Autos und warum?
?
Lernziel: Die Transport-Analogien (Leasing, Mietauto, Taxi, Bus) zur Abgrenzung nutzen.

Erläutern Sie zwei Vorteile und zwei Herausforderungen einer Hybrid Cloud.
?
Lernziel: Hybrid, Multi und Edge Computing als architektonische Lösungsansätze verstehen.

Wie argumentiere ich in der Klausur zu Servicemodellen und Bereitstellung?
?
Klausurstrategie:
- Zuordnen: Präzise Begriffspaare nutzen. IaaS = Betriebssystem, CaaS = Container, PaaS = Laufzeit (Runtime), FaaS = Funktion, SaaS = Anwendung.
- Vergleichen: Bei den Bereitstellungsmodellen (z.B. Hybrid Cloud) immer in Trade-offs denken. Die Hybrid Cloud kombiniert Skalierung (Public) und Datensouveränität (Private), der "Preis" dafür ist aber zwingend eine massive Konfigurationskomplexität und doppelte Kostenstruktur.

---

## Thema 3: Docker & Prozessvirtualisierung (PDF 3)

Wie standardisiert Docker Laufzeitumgebungen und wie übersetzt man dieses Prinzip in ein sauberes, sicheres Dockerfile?
?
Leitfrage: Thema 3 (Docker & Prozessvirtualisierung)

Vergleichen Sie VM und Container hinsichtlich der Gründe für Overhead bei Speicher und CPU.
?
Lernziel: Container vs. Virtuelle Maschinen abgrenzen.

Erläutern Sie das Prinzip von Copy-On-Write bei der Verwendung von Docker.
?
Lernziel: Das Copy-On-Write Prinzip und die Flüchtigkeit von Containern erklären.

Warum ist es nicht sinnvoll, einen SSH Server im Docker Container zu installieren oder Build-Befehle wie mvn clean install ins finale Image aufzunehmen?
?
Lernziel: Best-Practices für Dockerfiles anwenden (Layer-Caching, Security).

Wie argumentiere ich in der Klausur, wenn ich ein Dockerfile optimieren muss?
?
Klausurstrategie: Suche systematisch nach drei Fehlern:
1. Tagging: Wurde :latest verwendet? Schlecht! Verhindert deterministische Builds. Nutze spezifische Versions-Tags.
2. Schichten-Overhead: Gibt es viele einzelne RUN-Befehle? Schlecht! Verknüpfe sie mit &&, da sonst für jeden Befehl ein unveränderlicher, speicherfressender Layer erzeugt wird.
3. Sicherheit: Läuft der Prozess als Root? Schlecht! Nutze den USER-Befehl für Least-Privilege.

---

# Teil 2: Übungsklausur (Probeklausuren) – Fragen & Musterlösungen

Frage 1: Grundlagen und "Server-Festungen" (aus Probeklausur 1a)
Aufgabe: Was sind "Server-Festungen", wodurch entstehen sie und warum sind sie ein Problem für den Betrieb? (3 Punkte)
?
Musterlösung:
- Was sie sind: Server-Festungen sind isolierte, extrem langlaufende Altsysteme, bei denen Administratoren alles Erdenkliche tun, um einen Neustart zu verhindern.
- Entstehung: Sie entstehen durch das Prinzip der Mutable Infrastructure: Systeme werden nach dem Deployment über Jahre hinweg händisch und oft undokumentiert gepatcht und verändert (Schneeflocken-Effekt).
- Problem: Der Zustand des Servers ist nicht mehr reproduzierbar. Fällt die Hardware aus, kann das System nicht identisch neu aufgebaut oder zur Bewältigung von Last horizontal herausskaliert werden.

Frage 2: Servicemodelle & Analogien (aus Probeklausur 1d)
Aufgabe: Welche Dienstleistungsstufe des Cloud Computing hat Parallelen zum Mieten eines Autos und warum? (2 Punkte)
?
Musterlösung:
Das Modell Container as a Service (CaaS) entspricht dem Mieten eines Autos.
Begründung: Der Kunde wählt situativ eine Fahrzeugklasse (Ressourcenausstattung/Containergröße) und zahlt exakt nach Nutzung (On-Demand). Das Fahrzeug bleibt Fremdeigentum und die Wartung des Autos (das Host-Betriebssystem) übernimmt der Vermieter (Cloud-Provider). Der Kunde steuert das Auto jedoch noch selbst, das heißt, er baut und verwaltet den reinen Container-Prozess.

Frage 3: Architekturmodelle (aus Probeklausur 2e & 2f)
Aufgabe: Erläutern Sie den Unterschied zwischen Edge Computing und einer Private Cloud in Bezug auf den Anwendungsfokus. (2 Punkte)
?
Musterlösung:
- Eine Private Cloud zentralisiert Daten in einem lokalen, hochsicheren Rechenzentrum primär mit dem Fokus auf maximale Datensouveränität und Kontrolle (z.B. für Kernsysteme und Datenbanken).
- Edge Computing hingegen dezentralisiert die Verarbeitung und verlagert sie direkt an den Entstehungsort der Daten (den "Rand" des Netzwerks, z.B. an Sensoren in einer Fabrik). Der Fokus liegt hierbei nicht primär auf klassischer Datenspeicherung, sondern auf Echtzeitverarbeitung (minimale Latenz) und Bandbreitenreduktion (nur komprimierte Anomalien werden ins Netz gesendet).

Frage 4: Docker & Copy-On-Write (aus Probeklausur 3i)
Aufgabe: Erläutern Sie das Prinzip von Copy-On-Write bei der Verwendung von Docker. (2 Punkte)
?
Musterlösung:
Ein Docker Image ist strikt read-only (schreibgeschützt). Um zur Laufzeit Dateien verändern zu können, erhält jeder gestartete Container eine flüchtige, beschreibbare R/W-Schicht.
Versucht der Container-Prozess eine Originaldatei zu modifizieren, wird diese im ersten Schritt aus dem schreibgeschützten Image in die beschreibbare Schicht kopiert ("Copy") und erst dort modifiziert ("Write"). Das Original-Image bleibt unangetastet, und nach Beenden des Containers wird die gesamte Schreibschicht unwiderruflich gelöscht.

Frage 5: Dockerfile Best Practices (aus Probeklausur 3b & 3c)
Szenario: Ein Entwickler hat folgendes in sein Dockerfile geschrieben:
FROM javaee/springdemo:latest
RUN apk update
RUN apk add curl
Er hat zudem Build-Befehle wie mvn clean install sowie einen SSH-Server im Container installiert.
Aufgabe: Erläutern Sie Optimierungen für das Dockerfile und bewerten Sie die Integration von mvn clean install und SSH.
?
Musterlösung:
- Optimierung 1 (Tagging): Zeile 1 muss angepasst werden. Das Tag :latest muss zwingend durch ein präzises, stabiles Versionstag (z.B. 1.2.1 oder alpine3.9) ersetzt werden, um deterministische und reproduzierbare Builds zu garantieren.
- Optimierung 2 (Layering): Die Zeilen 2 und 3 müssen mit einem logischen UND (&&) zusammengefasst werden (RUN apk update && apk add curl). Andernfalls erzeugt jeder RUN-Befehl eine eigene Image-Schicht, was zu unnötigem "Image Bloat" (Speicherverschwendung) führt.
- Bewertung SSH: Ein SSH-Server hat in einem Container nichts zu suchen. Ein Container folgt dem Prinzip "Ein Prozess pro Container" (Process Isolation). SSH vergrößert nur die Angriffsfläche und bricht dieses Paradigma. Für Debugging nutzt man docker container exec -it <id> sh.
- Bewertung mvn clean install: Das ist ein architektonischer Fehler. Dieser Befehl lädt den kompletten Source Code sowie MB/GB an Build-Werkzeugen (Maven) und Abhängigkeiten in das Image herunter. Ein Docker Image darf jedoch nur das fertige, kompilierte Artefakt (z.B. die .jar Datei) enthalten. Der Build-Schritt muss vorher in der CI/CD-Pipeline (oder in einem Multi-Stage-Build) stattfinden.