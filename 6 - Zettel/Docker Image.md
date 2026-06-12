#Note

2026-06-12

Tags: [[Virtualisierung]], [[Docker]], [[Systemarchitektur]]
#cloud_computing

---
Während traditionelle VMs eine riesige Binärdatei für ihr Image verwenden, ist das **[[Docker Image]]** das elegante architektonische Herzstück der Prozessvirtualisierung. Es ist eine **unveränderbare (Read-Only) Beschreibung** der gesamten Laufzeitumgebung und des auszuführenden Prozesses.

Die präziseste architektonische Metapher hierfür ist ein **Kuchenrezept**. Das Image selbst ist niemals ausführbar – es ist reiner Zustand. Erst durch den Befehl `docker container run` liest der Docker-Daemon dieses Rezept und erschafft daraus beliebig viele, isolierte Klone (die Kuchen): die **[[Container]]**. Jede Manipulation zur Laufzeit findet ausschließlich im temporären Dateisystem des Containers statt (Copy-On-Write); das zugrundeliegende Image bleibt auf ewig unangetastet.

Die Magie der Schichtenarchitektur (Layers)

Das fundamentale Konstruktionsprinzip eines Docker Images ist seine **Schichtenarchitektur**. Ein Image ist kein monolithischer Block, sondern wird schrittweise Schicht für Schicht (Layer) aus den Befehlen eines [[Dockerfile]] aufgebaut.

Diese Architektur löst immense Effizienzprobleme im Cloud Computing:

1. **Deduplikation:** Jede Schicht wird isoliert berechnet und mit einer kryptografischen Prüfsumme (Checksum) versehen. Nutzen zehn verschiedene Images dieselbe Basis-Schicht (z.B. Ubuntu-Basis und Java-Installation), wird diese Schicht physisch **nur ein einziges Mal gespeichert** und über Netzwerke übertragen.
2. **Build-Cache:** Wenn ein Image neu gebaut wird, vergleicht Docker die Schichten von oben nach unten. Ändert sich der Anwendungs-Code ganz unten im Skript, werden nur diese und die _darauf aufbauenden_ Schichten neu generiert. Alles darüber wird blitzschnell aus dem Cache geladen. _Architectural Imperative:_ Dies zwingt Entwickler dazu, **Befehle nach ihrer Änderungsfrequenz zu sortieren**. Seltene Änderungen (wie OS-Updates) müssen zwingend oben stehen, hochfrequente Änderungen (wie das Kopieren von Applikations-Code) ganz unten. Wer diese Regel bricht, vernichtet den gesamten Effizienzvorteil der Schichtenbildung.

Tagging und die Illusion der Aktualität

Images werden über **Tags** identifiziert und adressiert, welche als Verweise auf einen konkreten Versionsstand fungieren. Ein Tag besteht strukturell aus Registry, User, Imagename und Version.

Das kritischste Architektur-Risiko in diesem Zusammenhang ist das implizite Tag **latest**. Wird bei einem Build oder Pull keine Version angegeben, setzt Docker blindlings `latest`. Entgegen der Intuition bedeutet `latest` **nicht** "die aktuellste Version", sondern lediglich "die unbekannte Standardversion". Wer in Produktionssystemen das `latest`-Tag konsumiert, erzeugt unvorhersehbare, nicht-deterministische Deployments (es könnten plötzliche Breaking Changes enthalten sein) und eliminiert die Möglichkeit eines kontrollierten Rollbacks auf eine verlässliche Vorversion. Stattdessen sind für Basisimages zwingend _Stable Tags_ (z.B. `1.2.1`) und für eigene Artefakte _Unique Tags_ (z.B. BuildID oder Datum) zu verwenden.

---

### Flashcards

Warum ist die Reihenfolge der Instruktionen in einem Dockerfile von absolut kritischer Bedeutung für die Bauzeit und den Speicherbedarf eines Docker Images?
?
Docker Images basieren auf einer strikten Schichtenarchitektur, bei der jede Zeile eine eigene, gehashte Schicht erzeugt. Ändert sich in einer Instruktion etwas, wird ihre Prüfsumme ungültig und diese Schicht sowie **alle darauf folgenden Schichten** müssen zwingend neu gebaut werden. Befehle, die sich häufig ändern (wie Anwendungs-Code), müssen daher ganz unten im Dockerfile stehen, während selten geänderte Befehle (Basis-Abhängigkeiten) oben stehen müssen, um den Build-Cache nicht bei jedem Durchlauf zu zerstören.

Was ist der funktionale und konzeptionelle Unterschied zwischen einem Docker Image und einem Docker Container?::Das **Docker Image** ist die starre, unveränderbare und nicht-ausführbare Schablone (das "Rezept", Read-Only). Der **Docker Container** ist die auf Basis des Images gestartete, flüchtige Laufzeit-Repräsentation, in der Prozesse ablaufen und temporäre Dateiänderungen stattfinden.

Warum muss das Tag `latest` beim Bau und Betrieb von Cloud-Architekturen strikt vermieden werden?::`latest` garantiert nicht die aktuellste Version, sondern ist lediglich ein Fallback-Standardwert, der auf eine "unbekannte" Version zeigt. Seine Nutzung verhindert deterministische Deployments, verschleiert Änderungen im Baseimage und macht gezielte Rollbacks auf definierte Alt-Versionen unmöglich.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Docker Image]]
SORT file.mtime DESC
```