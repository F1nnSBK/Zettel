#Note

2026-06-12

Tags: [[Virtualisierung]], [[Speichermanagement]], [[Docker]], [[Systemarchitektur]]
#cloud_computing

---
In der Architektur von Docker besteht ein fundamentales Spannungsfeld: Ein [[Docker Image]] ist eine statische, strikt schreibgeschützte (read-only) Beschreibung der Systemumgebung. Eine aktive Applikation in einem [[Docker Container]] muss zur Laufzeit jedoch zwingend Zustand erzeugen – beispielsweise beim Schreiben von Log-Dateien, beim Speichern von temporären Caches oder beim Anpassen von Konfigurationen. Wenn das Dateisystem schreibgeschützt ist, wäre ein produktiver Applikationsbetrieb unmöglich.

Die Mechanik der temporären Schreibschicht

Um diesen Konflikt zu lösen, nutzt Docker das **Copy-On-Write (CoW)** Prinzip. Anstatt die Unveränderbarkeit des Images aufzuweichen, erhält jeder gestartete Container zusätzlich zum read-only Dateisystem eine eigene **temporäre, beschreibbare Dateiablage (Read/Write-Layer)**.

Die namensgebende Mechanik greift exakt in dem Moment, in dem der Container-Prozess versucht, eine bestehende Datei zu verändern:

1. Da das System im Ursprungs-Image nur lesbar ist, können dort keine Änderungen vorgenommen werden.
2. Die betroffene Datei wird aus dem schreibgeschützten Image in die temporär beschreibbare Schicht kopiert ("Copy").
3. Die Modifikation ("Write") findet ausschließlich an dieser angefertigten Kopie innerhalb der beschreibbaren Schicht statt. Das originale Docker Image wird niemals angetastet und bleibt absolut makellos.

Architektonische Konsequenz: Radikale Flüchtigkeit

Das Copy-On-Write Prinzip ist der technische Garant für die Zustandslosigkeit (Statelessness) in der Prozessvirtualisierung. Die architektonisch wichtigste Eigenschaft dieser Technik ist ihre Flüchtigkeit: **Nach dem Beenden des Docker Containers wird die gesamte beschreibbare Schicht restlos gelöscht**.

Alle Änderungen, die während der Laufzeit an Dateien vorgenommen wurden, sind nicht permanent. Dies ermöglicht es Cloud-Systemen, hunderte Klone desselben Images fehlerfrei parallel auszuführen, erzwingt jedoch gleichzeitig, dass persistente Daten (wie Datenbankeinträge) architektonisch zwingend aus dem Container ausgelagert werden müssen (z.B. über Cloud-Volumes oder externe Datenbanken).

---

### Flashcards

Welches fundamentale Problem bei der Ausführung von Docker Containern wird durch das Copy-On-Write Prinzip architektonisch gelöst?
?
Docker Images sind als Basis strikt schreibgeschützt (read-only), während Applikationen zur Laufzeit Dateien schreiben müssen (z.B. Logs). Copy-On-Write löst dies, indem es dem Container eine temporäre Schreibschicht zuweist, in die Dateien vor ihrer Änderung kopiert werden, ohne das Basis-Image zu modifizieren.

Was passiert beim Copy-On-Write Prinzip mit der Originaldatei des Docker Images, wenn eine Anwendung im Container diese Datei zu ändern versucht?::Die Originaldatei im Image bleibt absolut unangetastet. Die Datei wird zunächst in die beschreibbare Schicht (Read/Write-Layer) des Containers kopiert, und die Änderungen werden ausschließlich an dieser Kopie vorgenommen.

Warum garantiert das Copy-On-Write Prinzip die radikale Zustandslosigkeit (Statelessness) eines Docker Containers am Ende seines Lebenszyklus?::Weil die temporäre, beschreibbare Schicht, in der alle Modifikationen durch Copy-On-Write gespeichert wurden, nach dem Beenden des Containers unwiderruflich gelöscht wird. Alle Dateiänderungen gehen somit verloren.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Copy-On-Write]]
SORT file.mtime DESC
```