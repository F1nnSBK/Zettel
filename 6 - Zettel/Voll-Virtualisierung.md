#Note

2026-06-12

Tags: [[Virtualisierung]], [[Systemarchitektur]], [[Cloud Computing]]
#cloud_computing

---
Der architektonische Kern der **Voll-Virtualisierung** ist die perfekte Täuschung. Eine physische Maschine wird durch eine Abstraktionsschicht in mehrere autarke, logische Repräsentationen – die Virtuellen Maschinen (VMs) – unterteilt. Der geniale architektonische Schachzug hierbei ist, dass das **Gast-Betriebssystem (Gast-OS) nicht modifiziert werden muss**. Es "glaubt", alleinigen und direkten Zugriff auf Festplatten, Netzwerk und Prozessoren zu haben.

Ermöglicht wird dies durch den [[Hypervisor]]. Er fungiert als unsichtbarer Diktator, der jeden einzelnen Hardware-Aufruf des Gast-OS abfängt (Interception) und so modifiziert, dass die VM ihr zugewiesenes Ressourcenkontingent niemals überschreitet. Um die immensen Latenzen dieser ständigen Dolmetscher-Arbeit aufzufangen, ist die Voll-Virtualisierung zwingend auf **Hardware-Virtualisierung** (wie den CPU-Befehlssatz **VT-x**) angewiesen, was den Leistungsverlust auf ein erträgliches Maß von etwa 5% bis 10% drückt.

Architektonische Ineffizienz durch harte Isolation

Während die absolute Isolation zwischen den VMs und die Entkopplung vom Host-Betriebssystem massiv zur Systemsicherheit beitragen, bezahlt die Systemarchitektur dafür einen extrem hohen Preis an Ineffizienz.

Zwei fundamentale Skalierungs-Bremsen prägen die Voll-Virtualisierung:

1. **Ineffiziente Ressourcenbindung:** Ressourcen (CPU, RAM) werden für die virtuelle Maschine fest allokiert. Wenn eine VM mit 16 GB RAM konfiguriert ist, sind diese 16 GB auf dem physischen Host blockiert – völlig unabhängig davon, ob die Applikation im Gast-OS gerade unter Volllast rechnet oder komplett im Leerlauf ist.
2. **Gigantischer Overhead (Fat Images):** Jede VM ist ein komplettes Universum. Sie enthält das volle Gast-Betriebssystem, sämtliche Kernel-Abhängigkeiten und erst ganz oben die eigentliche Anwendung. Dadurch entstehen monströse **Imagegrößen von 3 bis 4 GB**.

Das Ende der horizontalen Skalierbarkeit

In der modernen Cloud-Architektur, die auf massives Autoscaling und [[Horizontale Skalierung]] setzt, wird die Voll-Virtualisierung zum Flaschenhals. Wenn ein System bei einer Lastspitze sofort 50 neue Knoten benötigt, ist die Voll-Virtualisierung ungeeignet: Das Kopieren von 4-GB-Images über das Netzwerk dauert zu lange, und das träge Hochfahren eines kompletten Betriebssystems (Boot-Sequenz), bevor die eigentliche Applikation überhaupt startet, vernichtet jede Echtzeit-Agilität. Für extrem dynamische Workloads wurde sie daher weitestgehend von der leichtgewichtigen [[Prozessvirtualisierung]] (Containern) abgelöst.

---

### Flashcards

Warum ist die Voll-Virtualisierung architektonisch extrem ineffizient hinsichtlich der Speicher- und Prozessornutzung des physischen Hosts?
?
Weil zugewiesene logische Ressourcen (wie CPU und RAM) vom Hypervisor für die virtuelle Maschine hart reserviert und belegt werden, völlig unabhängig davon, ob die eigentliche Gast-Anwendung diese Ressourcen im Moment tatsächlich benötigt oder im Leerlauf ist.

Welchen massiven Vorteil bietet die Voll-Virtualisierung für Legacy-Systeme im Vergleich zur Para-Virtualisierung oder zu Containern?::Das eingesetzte Gast-Betriebssystem muss in keiner Weise modifiziert oder angepasst werden, da der Hypervisor ihm den direkten Hardwarezugriff auf der gleichen Prozessorarchitektur perfekt vorgaukelt.

Warum eignet sich die Voll-Virtualisierung nur sehr schlecht für rasante, massiv [[Horizontale Skalierung]] in der Cloud?::Wegen des enormen Overheads: Die Images sind riesig (3-4 GB, da sie ein volles OS enthalten), und vor jedem Applikationsstart muss das System erst träge das komplette Gast-Betriebssystem hochfahren.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Voll-Virtualisierung]]
SORT file.mtime DESC
```