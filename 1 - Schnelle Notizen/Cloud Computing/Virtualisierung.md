**Grundlagen**
Virtualisierung -> isolierte Ausführungsumgebungen bauen
Dadurch werden Beeinträchtigungen durch Abstürze andere Anwendungen verhindert.
Das nennt sich *Entkopplungsschicht* (Virtualization Layer) 

| Simulation                                               | Emulation                                                                 | Virtualisierung                                 |
| -------------------------------------------------------- | ------------------------------------------------------------------------- | ----------------------------------------------- |
| Vollständige Nachbildung eines<br>Systems durch Software | Stellt gleiche Funktionen<br>aber ohne, die interne Logik<br>zu verwenden | Dient der Entkopplung<br>von Hard- und Software |
| z.B. Flugsimulator                                       | z.B. WSL1, JVM                                                            | z.B. VirtualBox, KVM                            |

**Vorteile**

	Isolation der Anwendung (Sandboxing)
	Einsatz verschiedener Programmiersprachen
	Vermeidung ungewollter Seiteneffekte
	
	Multiplizität von Systemen
	Betrieb von Alt- und Neu-System
	Ausnutzen von Effekten zur Fixkostendegression
	
	Portabilität der Systemkonfiguration
	Prüfung von Hardwareanforderungen im Vorfeld

**Klassisch**
Anwendung: Umsetzung spezifischer Funktionalität
|
Betriebssystem (OS): Stellt die Laufzeitumgebung samt Bibliotheken und grafischen Komponenten bereit
|
Kernel: Grundlegende Softwareschicht eines Betriebssystem
|
Umfasst die physischen Geräte


**Voll-Virtualisierung** (z.b. Hyper-V, VMWare)
Virtuelle Maschinen: Eigener virtueller Computer (Kernel, OS und Anwendung)
|
| Weitergabe einer generischen CPU (Hardware)
|
Hypervisor: Entkoppelt die Ausführung der virtuellen Maschinen von der Hardware indem er die Ressourcenzugriffe verwaltet und Befehle übersetzt (Bare-Metal Hypervisor)
|
Kernel: Grundlegende Softwareschicht eines Betriebssystem
|
Umfasst die physischen Geräte


**Hosted-Hypervisor** (z.b. Parallels)
Virtuelle Maschinen: Eigener virtueller Computer (Kernel, OS und Anwendung)
|
| Weitergabe einer generischen CPU (Hardware)
|
Hypervisor: Entkoppelt die Ausführung der virtuellen Maschinen von der Hardware indem er die Ressourcenzugriffe verwaltet und Befehle übersetzt (Bare-Metal Hypervisor)
App: Ausführung spezifischer Funktionen
|
Host-OS
|
Kernel: Grundlegende Softwareschicht eines Betriebssystem
|
Umfasst die physischen Geräte


**Para-Virtualisierung**
Virtuelle Maschinen (Host & Gast): 
	Host: Eigener virtueller Computer (Kernel, OS und Anwendung)
	Gast: virtueller Computer, der den nativen Treiber vom Host mitverwendet
|
| Weitergabe einer generischen CPU (Hardware)
|
Hypervisor: Entkoppelt die Ausführung der virtuellen Maschinen von der Hardware indem er die Ressourcenzugriffe verwaltet und Befehle übersetzt (Bare-Metal Hypervisor)
|
Umfasst die physischen Geräte


**Prozess-Virtualisierung**
Container: Anwendung und notwendige Bibliotheken
|
Container Managementsystem
App
|
Host-OS
|
Kernel: Grundlegende Softwareschicht eines Betriebssystem
	cgroup: Vorgabe vin klaren Hardwarekontigenten
	namespaces: Kompartimentierung der Container-Anwendung in der Sichtbarkeit
|
Umfasst die physischen Geräte

**Aufgabe 3**
a) Voll-Virtualisierung: Gut für Anwendungen mit hohem Sicherheitsrisiko (potenzieller Gefährdung), Schlecht für das Verwendung auf ohnehin schon schwacher Hardware, Portabilität (einfache Austauschbarkeit), gut für eine Monolith-Architektur, starke Isolation der virtualisierten Gäste, Einsatz im Entwicklungsprozess ist umständlich, Heterogene Betriebssystemlandschaft
Prozessvirtualisierung: Gut für performante Virtualisierung von einzelnen Anwendungen, Angreifbar (da keine wirkliche Virtualisierung stattfindet), gut für eine Microservice Architektur

Vorteile der Voll-Virtualisierung sind die Nachteile der Prozessvirtualisierung und umgekehrt

b) Die Prozessvirtualisierung wird durch die Voll-Virtualisierung nochmal vollständig entkoppelt, VMs haben oft schwächere Hardwarekonfigurationen, was aber für die Prozessvirtualisierung kein Problem darstellt

c) Bei der Prozessvirtualisierung wird nur eine Anwendung mit ihren benötigten Bibliotheken gekapselt, es gibt praktisch kaum Overhead. Bei der Voll-Virtualisierung wird ein ganzen Betriebssystem in die entkoppelte VM installiert, das führt zu einer Menge an Overhead und ist aufwendig zu bereinigen z.B. eine Taschenrechnerapp, unnötige Treiber für Eingabegeräte, Ausgabegeräte, etc.

d) Die Prozessvirtualisierung lässt sich schnell einrichten, da sie im Falle von Docker vorgefertigte Templates (Images) verwendet, von denen es zu fast jeder Anwendung eine optimierte Version gibt. Durch die Kapselung aller Anwendungen in ihre eignen Container, erreicht man ein hohes Level an Ausfallsicherheit und Flexibilität, wird mehr Kapazität benötigt, kann nach belieben einfach mehrere Container zu oder abgeschaltet werden --> freie Skalierung