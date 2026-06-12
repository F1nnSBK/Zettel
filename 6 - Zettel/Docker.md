#Note

2026-06-12

Tags: [[Virtualisierung]], [[Container]], [[DevOps]]
#cloud_computing

---
Vor der Erfindung von Docker war der Betrieb von Softwareanwendungen stark von der darunterliegenden Infrastruktur abhängig. Entwickler und Administratoren kämpften mit Inkompatibilitäten und dem manuellen, fehleranfälligen Aufsetzen von Laufzeitumgebungen. Das architektonische Leitbild von Docker ist der **Standardcontainer der Frachtschifffahrt**. Vor dessen Einführung war das manuelle Be- und Entladen von Schiffen extrem aufwendig, unsicher und durch den Flaschenhals der Hafenbrücken nicht planbar. Der physische Standardcontainer standardisierte die weltweite Logistik-Infrastruktur radikal.

Docker wendet exakt dieses Paradigma auf die Softwarearchitektur an. Es ist Docker völlig egal, welche Programmiersprache oder Anwendung verwendet wird: Die Software wird mitsamt all ihren Bibliotheken und Abhängigkeiten in ein standardisiertes, portables Abbild (das [[Docker Image]]) gepackt. Die Infrastruktur (der Server) muss nur noch in der Lage sein, "Docker" auszuführen.

Architektonische Trennung: Client und Daemon

Ein massiver Architekturvorteil von Docker ist die Trennung von Steuerung und Ausführung. Docker ist kein monolithischer Block, sondern besteht primär aus zwei Komponenten:

1. **Der Docker-Client:** Ein reines Kommandozeilen-Werkzeug (CLI). Seine einzige Aufgabe ist es, Benutzerbefehle (wie `docker container run`) entgegenzunehmen, zu übersetzen und weiterzuleiten.
2. **Der Docker-Daemon:** Der eigentliche Server-Dienst (Background-Worker), der auf dem Host läuft. Er nimmt Befehle vom Client über eine **REST-Schnittstelle** entgegen und führt die schwere Arbeit aus: Er erstellt Netzwerke, lädt Images aus Registries herunter und orchestriert die Erstellung der Linux-Container.

Der Workflow: Build, Ship, Run

Das Docker-Ökosystem digitalisiert den kompletten Lebenszyklus einer Applikation:

- **Build:** Über ein deklaratives Skript (das [[Dockerfile]]) wird ein individuelles, schreibgeschütztes Abbild gebaut.
- **Ship:** Dieses Abbild wird in eine **Docker-Registry** (z.B. den öffentlichen Docker Hub) hochgeladen. Dort fungiert es nach dem "Image-from-the-shelf"-Prinzip als sofort abrufbares Artefakt.
- **Run:** Der Docker-Daemon lädt das Image und erzeugt daraus über die Prozessvirtualisierung (`cgroups`, `namespaces`) eine isolierte, lauffähige Kopie: den [[Container]]. Dieser Workflow ermöglicht eine rasante **[[Horizontale Skalierung]]**, da hunderte Container aus demselben Image parallel instanziiert werden können.

---

### Flashcards

Was ist das historische "Frachtcontainer-Paradigma", das die architektonische Grundidee von Docker bildet?
?
Vor der Einführung von Standardcontainern in der Schifffahrt war das manuelle Be- und Entladen von Facht extrem langsam, gefährlich und unplanbar. Docker überträgt diesen radikalen Standardisierungs-Erfolg auf Software: Egal welche Sprache oder Umgebung, die Anwendung wird in einen einheitlichen "Container" (Image) gepackt, wodurch die gesamte Infrastruktur nur noch auf das Starten dieses Standards optimiert sein muss.

Aus welchen zwei zentralen Komponenten ist die Docker-Architektur aufgebaut und wie kommunizieren sie?::Aus dem **Docker-Client** (Kommandozeile zur Eingabe) und dem **Docker-Daemon** (Server-Dienst zur Ausführung). Der Client sendet die Befehle über eine **REST-Schnittstelle** an den Daemon, der die tatsächliche Erstellung und Verwaltung der Container übernimmt.

Welche Rolle spielt die "Docker Registry" im sogenannten "Build, Ship, Run"-Workflow von Docker?::Die Registry (wie z.B. Docker Hub) dient als zentraler Ablageort zum Speichern und Verteilen der gebauten Docker Images ("Ship"). Sie ermöglicht das Paradigma eines "Image-from-the-shelf", bei dem fertige Laufzeitumgebungen weltweit geteilt und sofort bezogen ("Run") werden können.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Docker]]
SORT file.mtime DESC
```