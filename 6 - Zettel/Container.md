#Note

2026-06-12

Tags: [[Virtualisierung]], [[Docker Ökosystem]], [[Systemarchitektur]]
#cloud_computing

---
In der Welt der Systemarchitektur ist ein **Container** (insbesondere der De-facto-Standard **Docker Container**) die logische **Laufzeit-Repräsentation** eines statischen Bauplans. Während ein [[Docker Image]] lediglich eine starre, schreibgeschützte (Read-Only) Beschreibung der Laufzeitumgebung und der Abhängigkeiten ist, erweckt der Container dieses Image zum Leben.

Der architektonische Kern eines Containers ist seine **Zustandslosigkeit (Statelessness)**. Was immer in einem Container an Daten generiert oder modifiziert wird, ist nicht permanent. Ein Container ist kein Server, den man pflegt ([[Mutable Infrastructure]]), sondern ein flüchtiger Prozess, der für eine Aufgabe gestartet und danach zerstört wird.

Das Copy-On-Write Prinzip

Da das zugrundeliegende Image streng read-only ist, benötigt der Container einen Mechanismus, um zur Laufzeit Dateianpassungen (z.B. Logfiles schreiben oder Konfigurationen anpassen) vornehmen zu können. Hierfür erhält jeder Container beim Start eine **temporäre, beschreibbare Schicht (Read/Write-Layer)**, die wie eine transparente Folie über das Image gelegt wird.

Sobald ein Container eine bestehende Datei des Images verändern muss, greift das **[[Copy-On-Write]]**-Prinzip: Die Datei wird vom schreibgeschützten Image in die beschreibbare temporäre Schicht kopiert und erst _dort_ modifiziert. Das Original im Image bleibt unangetastet. **Nach Beenden des Containers wird diese gesamte beschreibbare Schicht unwiderruflich gelöscht**.

Architektonische Überlegenheit durch Kernel-Sharing

Im Gegensatz zur klassischen virtuellen Maschine (VM) bringt der Container kein vollständiges Gast-Betriebssystem mit. Er verlässt sich auf die [[Prozessvirtualisierung]] und nutzt über `cgroups` (Ressourcenlimitierung) und `namespaces` (Sichtbarkeitsisolation) direkt den Kernel des Host-Betriebssystems.

Daraus resultieren massive architektonische Hebel für moderne Cloud-Systeme:

1. **Unübertroffene Skalierbarkeit:** Durch das Fehlen des monströsen Gast-OS-Overheads entfällt der träge Boot-Vorgang. Ein Container startet in Millisekunden direkt auf Applikationsebene.
2. **Minimale Hardwarebindung:** Da Container keine vollständige Hardware durch einen [[Hypervisor]] emulieren, beanspruchen sie Hardwareressourcen nur bei tatsächlichem Bedarf und belegen sie nicht starr im Voraus.
3. **Sicherheitsrisiko durch geteilten Kernel:** Diese Leichtgewichtigkeit wird durch eine geschwächte Isolation erkauft. Ein Container-Prozess ist de facto ein nativer Prozess auf dem Host. Wird ein Container fahrlässig in der Standardkonfiguration als `root` (Administrator) ausgeführt, kann ein erfolgreicher Angriff (Container Escape) direkt die Kontrolle über das gesamte Host-System und alle benachbarten Container erlangen.

---

Flashcards

Wie funktioniert das Speichermanagement für Dateiänderungen zur Laufzeit eines Docker-Containers, wenn das zugrunde liegende Image "Read-Only" ist?
?
Durch das **Copy-On-Write** Prinzip. Der Container erhält eine temporäre, beschreibbare Schicht (r/w Layer) über dem Image. Soll eine Datei geändert werden, wird sie erst in diese Schicht kopiert und dort modifiziert. Wird der Container gestoppt, wird diese gesamte Schreibschicht unwiderruflich gelöscht.

Welcher fundamentale Umstand sorgt dafür, dass ein Container in Millisekunden startet, während eine klassische Virtuelle Maschine (VM) Minuten benötigt?::Ein Container beinhaltet kein eigenes Gast-Betriebssystem und muss daher keinen langsamen OS-Bootvorgang durchlaufen. Er startet lediglich den Applikationsprozess auf dem bereits laufenden Host-Kernel.

Warum ist die Standardausführung eines Docker-Containers aus Perspektive der Systemarchitektur ein massives Sicherheitsrisiko?::In der Standardkonfiguration werden Container-Prozesse unter dem `root` (Admin) Account ausgeführt. Da Container sich den Host-Kernel teilen, kann ein Ausbruch (Container Escape) dem Angreifer sofort Admin-Rechte über den gesamten physischen Host verschaffen.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Container]]
SORT file.mtime DESC
```