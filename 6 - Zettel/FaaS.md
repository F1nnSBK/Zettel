#Note

2026-06-12

Tags: [[Cloud Computing]], [[Servicemodelle]], [[Systemarchitektur]], [[Serverless]]
#cloud_computing

---
**Function as a Service (FaaS)** treibt die Abstraktion der Systemarchitektur noch einen Schritt weiter als [[PaaS]]. Während der Entwickler bei PaaS noch die vollständige Kontrolle über die Logik seiner Anwendung besitzt, stellt der Cloud-Provider bei FaaS bereits **elementare Funktionsblöcke** (wie beispielsweise Schnittstellen zur Bilderkennung, Dokumentenverarbeitung oder Spracherkennung) schlüsselfertig zur Verfügung.

Der Softwareentwickler programmiert nur noch einen Teil der Endanwendung selbst und stützt sich für die restliche komplexe Funktionalität auf die vorgefertigten Lösungen des Cloud-Anbieters. Die Hoheit über das Hosting, die Hardware-Ressourcen (CPU, RAM, Speicher), den Netzwerkverkehr und das konkrete Laufzeitverhalten wird hierbei restlos an den Provider abgegeben.

Die Bus-Analogie (Einzelfahrt)

Um die Charakteristik von FaaS greifbar zu machen, eignet sich in der Transport-Metapher die **Nutzung des Busses (Einzelfahrt)**. Der Kunde ist hierbei nur noch Beifahrer und hat absolut keine Mitsprache bei der Wahl des eingesetzten Fahrzeugs oder dessen Ausführung. Er muss sich an fest vorgegebene Fahrzeiten und Haltepunkte (die vorgegebenen Programmiersprachen und Schnittstellen) richten. Um an sein Endziel zu gelangen, muss er gegebenenfalls mehrere Busstrecken kombinieren (das Verketten einzelner Funktionen). Das Fahrzeug bleibt Fremdeigentum der Verkehrsgesellschaft, welche auch die komplette ausgelagerte Wartung übernimmt. Abgerechnet wird On-Demand.

Trade-off: Entwicklungsgeschwindigkeit vs. Maximaler Lock-In

Der massive architektonische Vorteil von FaaS liegt in der enormen Entwicklungsgeschwindigkeit: Komplexe Anwendungsfälle lassen sich mit extrem begrenzten Mitteln in kürzester Zeit umsetzen, da teure Eigenentwicklungen vermieden werden.

Der architektonische Preis dafür ist ein **sehr starker Lock-In Effekt**. Der Kunde muss seine Architektur zwingend an die vom Provider vorgegebenen Programmiersprachen und den stark variierenden Funktionsumfang der Schnittstellen anpassen. Da jegliches Wissen über das Hosting entfällt und der Code eng an proprietäre Funktionen gebunden ist, wird ein Wechsel zu einem anderen Cloud-Provider de facto unmöglich, ohne die Anwendung von Grund auf neu zu schreiben.

---

### Flashcards

Was stellt der Cloud-Provider bei Function as a Service (FaaS) konkret zur Verfügung und wie verändert dies die Aufgabe des Softwareentwicklers?
?
Der Provider stellt **elementare Funktionsblöcke** (wie z.B. Audio- oder Bilderkennungs-Schnittstellen) bereit. Der Entwickler programmiert nur noch einen Teil der Anwendung selbst und stützt sich für die komplexe Logik auf diese fertigen Funktionen, wobei er sämtliche Kontrolle über Hosting, Hardware und Laufzeit abgibt.

Welche Transport-Analogie beschreibt das FaaS-Modell am treffendsten und welche Restriktionen gehen damit einher?::Die Analogie der **Busfahrt (Einzelfahrt)**. Der Kunde ist reiner Beifahrer ohne Mitsprache bei der Fahrzeugwahl oder Ausführung. Er muss sich an vorgegebene Haltepunkte und Zeiten halten (vorgegebene Schnittstellen/Sprachen) und eventuell mehrere Linien kombinieren (Funktionen verketten), wobei der Bus fremdgewartet wird.

Warum erzeugt die Nutzung von Function as a Service (FaaS) einen extrem starken Vendor Lock-in (Anbieterbindung)?::Weil der Entwickler seine Architektur tief mit den proprietären und anbieterspezifischen Programmierschnittstellen und Funktionsblöcken des Providers verzahnt. Ein Umzug zu einem anderen Provider ist kaum möglich, da sich die angebotenen Funktionsumfänge und APIs der Cloud-Anbieter gravierend voneinander unterscheiden.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[FaaS]]
SORT file.mtime DESC
```