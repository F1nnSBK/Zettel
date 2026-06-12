#Note

2026-06-12

Tags: [[Virtualisierung]], [[Container]], [[Linux]]
#cloud_computing

---
In der Ära der [[Voll-Virtualisierung]] wurde die Prozessisolation durch schwerfällige Gast-Betriebssysteme und den [[Hypervisor]] physisch und hart durchgesetzt. Mit dem Aufstieg der **[[Prozessvirtualisierung]]** und dem Wegfall des Hypervisors musste diese Isolation auf die Kernelebene des Host-Betriebssystems (Linux) verlagert werden. Dies wird durch **namespaces** realisiert.

Ein Namespace zieht logische Wände innerhalb des Host-Kernels. Er regelt präzise, welche Hardwareressourcen, Mount-Points, Netzwerkschnittstellen oder Prozessbäume ein Prozess überhaupt wahrnehmen kann. Die architektonische Brillanz liegt in der Illusion: Startet man eine Anwendung in einem isolierten PID-Namespace (Process ID Namespace), sieht dieser Prozess sich selbst als PID 1 (den absoluten Ursprungsprozess des Systems) und hat keinerlei Kenntnis von den abertausenden anderen Prozessen, die physisch auf demselben Host-OS laufen.

Die Trinität der Container-Technologie

In der modernen Systemarchitektur bilden Namespaces nie eine isolierte Lösung, sondern sind Teil einer existenziellen Symbiose für das [[Container]]-Management (wie Docker):

1. **Das Dateisystem:** Ein unveränderbares [[Docker Image]] bildet das Fundament, gepaart mit einer flüchtigen [[Copy-On-Write]] Schicht.
2. **Die Nutzungsgrenze:** **[[cgroups]]** definieren als harter Türsteher, _wie viel_ CPU, RAM oder I/O ein Prozess physisch konsumieren darf.
3. **Die Sichtbarkeitsgrenze:** **Namespaces** definieren, _was_ ein Prozess sehen und manipulieren darf (z.B. Beschränkung der Sichtbarkeit nur auf die eigenen Kindprozesse).

Die Schwäche der Kernel-Level-Isolation

Der gewaltige Performance-Vorteil von Namespaces – die nahezu native Anwendungsgeschwindigkeit und minimale Speicherbelegung durch den fehlenden Hypervisor-Overhead – hat einen harten architektonischen Preis. Die Isolation (Sichtbarkeit) findet rein logisch im Kernel des Hosts statt. Ein fataler Nachteil ist hierbei, dass trotz aller Zugriffseinschränkungen durch Namespaces die Containerprozesse oft noch die unmaskierte, physische Hardware "sehen" können. Gelingt einem Angreifer ein Ausbruch aus dem Container (z.B. weil der Prozess fälschlicherweise als `root` gestartet wurde), heben sich die logischen Wände der Namespaces auf und das gesamte System ist kompromittiert.

---

### Flashcards

Was ist die exakte architektonische Aufgabe von `namespaces` im Kontext der Prozessvirtualisierung?
?
Sie dienen der Einschränkung der **Sichtbarkeit** für Prozesse im geteilten Betriebssystem-Kernel. Sie regeln, welche anderen Prozesse oder Ressourcen (wie z.B. Hardware oder benachbarte Container) ein Prozess "sehen" darf; so wird ihm beispielsweise nur die Sicht auf seine eigenen Kindprozesse gestattet, wodurch die Illusion eines isolierten Systems entsteht.

Anhand welches fundamentalen Gegensatzpaares lassen sich die Funktionen von `cgroups` und `namespaces` zur Container-Erstellung präzise abgrenzen?::`cgroups` regeln zwingend die **Nutzung** (Wie viel RAM/CPU darf konsumiert werden?), während `namespaces` die **Sichtbarkeit** (Was darf der Prozess sehen?) regulieren.

Welcher sicherheitskritische Trade-off entsteht durch die Nutzung von Namespaces im Vergleich zur Voll-Virtualisierung?::Da die Isolation lediglich logisch im geteilten Host-Kernel stattfindet, sehen Containerprozesse oft noch die unmaskierte physische Hardware. Bei einem geglückten Ausbruch (Container Escape) aus dem Namespace ist der gesamte Host-Kernel und somit alle anderen Container kompromittiert.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[namespaces]]
SORT file.mtime DESC
```