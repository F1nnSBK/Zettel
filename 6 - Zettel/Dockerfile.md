#Note

2026-06-12

Tags: [[Virtualisierung]], [[Docker]], [[DevOps]], [[Infrastructure as Code]]
#cloud_computing

---
Das **Dockerfile** ist das architektonische Werkzeug, um das Paradigma der [[Immutable Infrastructure]] in der Prozessvirtualisierung umzusetzen. Es handelt sich um eine einfache Textdatei (strikt mit dem Namen `Dockerfile` und ohne Dateiendung), die den exakten, schrittweisen Aufbau einer Laufzeitumgebung definiert. Der Bau des Images wird über den Kommandozeilenbefehl `docker image build -t <imagetag> .` angestoßen, wobei das System das Skript Zeile für Zeile abarbeitet.

Ein Dockerfile ist konzeptionell immer dreigeteilt:

1. **Das Baseimage:** Die fundamentale Grundlage (z.B. ein schlankes Linux).
2. **Die Konfigurationsanpassungen:** Installation von Abhängigkeiten, Kopieren von Dateien, Setzen von Variablen.
3. **Der Einstiegspunkt:** Das Startkommando für den [[Docker Container]].

Praxis-Beispiel aus der Systemarchitektur

Das folgende, aus den Architektur-Best-Practices abgeleitete Beispiel zeigt ein optimiertes Dockerfile für eine Java Spring Boot Anwendung:

```dockerfile
# 1. BASEIMAGE (Möglichst schlank und präzise versioniert)
FROM openjdk:8-jre-alpine3.9

# 2. KONFIGURATIONSANPASSUNGEN & ABHÄNGIGKEITEN
# RUN: Führt Befehle aus. Mit && gebündelt, um unnötige Schichten zu vermeiden.
RUN apk update && apk add curl
RUN mkdir app

# Best Practice: Non-Root Ausführung. Erstellt Gruppe und User.
RUN addgroup -S spring && adduser -S springuser -G spring
USER springuser

# WORKDIR: Setzt das Arbeitsverzeichnis für alle folgenden Befehle. 
# Verhindert fehleranfällige Pfadwiederholungen.
WORKDIR app

# COPY: Kopiert Dateien vom Host in das Image.
COPY . .

# EXPOSE: Dokumentiert den Port für eingehende Verbindungen.
EXPOSE 8080

# 3. EINSTIEGSKOMMANDO
# CMD: Startet den Applikationsprozess in Exec-Notation (Sicherheit).
CMD ["java", "-jar", "app.jar"]
```

Anatomie der Kernbefehle

- **FROM**: Referenziert das zwingend erforderliche Basisimage. Aus Sicherheits- und Effizienzgründen sollten offizielle, extrem schlanke Distributionen (wie `alpine` mit ca. 5 MB) und präzise Versions-Tags (niemals `latest`) gewählt werden.
- **ENV**: Setzt Startwerte für Umgebungsvariablen (wie `stage=prod`). _Vorsicht:_ Niemals für sensible Daten (Passwörter) verwenden, da diese über den Image-Verlauf (`docker image history`) im Klartext ausgelesen werden können.
- **RUN**: Führt Kommandos zur Bauzeit aus. Zusammengehörige Befehle sollten zwingend mit `&&` kombiniert werden, um die Anzahl an generierten Image-Schichten gering zu halten.
- **WORKDIR**: Setzt das Arbeitsverzeichnis für alle nachfolgenden Instruktionen und vermeidet so fehleranfälliges Copy-Paste von absoluten Pfaden.
- **COPY**: Überträgt Dateien vom lokalen Host-System in das Image. Der Befehl sollte stets so präzise wie möglich formuliert sein (Vorsicht bei Wildcards `*`), um zu verhindern, dass irrelevante Dateiänderungen den Build-Cache invalidieren.
- **EXPOSE**: Dient primär der Dokumentation und gibt an, über welche Ports der Container zur Laufzeit angesprochen werden kann (muss von der `publish` Option des Hosts getrennt betrachtet werden).
- **CMD**: Das finale Kommando, das nicht zur Bauzeit, sondern _beim Starten_ des Containers ausgeführt wird. Es sollte in der **Exec-Notation** (als Array) spezifiziert werden, um zu verhindern, dass die Applikation als Unterprozess einer Shell gestartet wird, was Angreifern bei einem Ausbruch zusätzliche Shell-Werkzeuge in die Hand geben würde.

Architektonische Best Practices

Zwei Regeln entscheiden über die professionelle Qualität eines Dockerfiles:

1. **Die Anordnung nach Änderungsfrequenz:** Da jede Befehlszeile eine Schicht erzeugt und bei einer Änderung alle darunterliegenden Schichten den Cache verlieren und neu gebaut werden müssen, gilt zwingend: **Befehle, die sich häufig ändern (wie** **COPY** **von Programmcode), müssen ganz unten stehen**, während seltene Änderungen (Basisimage, Paket-Installationen) ganz oben stehen.
2. **Die Non-Root Ausführung:** Standardmäßig laufen alle Befehle und der finale Prozess als `root`. Da Container sich den Host-Kernel teilen, hat ein Ausbruch fatale systemweite Konsequenzen. Es muss zwingend mit dem Kommando `USER` ein unprivilegierter Account definiert werden.

---

### Flashcards

Welche drei grundlegenden logischen Blöcke definieren den strukturellen Aufbau eines Dockerfiles?
?
Ein Dockerfile ist dreigeteilt in: 1. Das **Baseimage** (`FROM`), 2. **Konfigurationsanpassungen** (wie `RUN`, `ENV`, `COPY`), und 3. den **Einstiegspunkt** (`CMD`).

Warum fordert die Systemarchitektur bei der Erstellung eines Dockerfiles, dass Befehle streng nach ihrer "Änderungsfrequenz" (selten zu häufig) von oben nach unten sortiert werden?::Da Docker eine Schichtenarchitektur (Layer-Caching) nutzt. Ändert sich eine Datei in einer Schicht (z.B. der Programmcode bei einem `COPY` Befehl), werden diese und **alle darauf folgenden Schichten** neu gebaut. Steht eine häufige Änderung oben, wird der gesamte Cache bei jedem Build nutzlos zerstört.

Welches massive Sicherheitsrisiko adressiert der `USER` Befehl im Dockerfile und wie funktioniert er?::In der Standardkonfiguration laufen alle Container-Prozesse als `root` (Administrator). Gelingt ein Container-Escape, hat der Angreifer Vollzugriff auf den Host-Kernel. Der `USER` Befehl stellt sicher, dass alle folgenden Befehle und der finale Applikationsprozess unter einem unprivilegierten Account laufen.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Dockerfile]]
SORT file.mtime DESC
```