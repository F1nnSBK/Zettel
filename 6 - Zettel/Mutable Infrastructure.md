#Note

2026-06-12

Tags: [[Infrastrukturmanagement]], [[Systemarchitektur]], [[Cloud Computing]]
#cloud_computing

---
**Mutable Infrastructure** (veränderbare Infrastruktur) repräsentiert die traditionelle Vorgehensweise des IT-Betriebs. In diesem Modell wird ein Server einmalig aufgesetzt und nach seinem Deployment fortlaufend händisch verändert. Administratoren loggen sich über Jahre hinweg auf den laufenden Systemen ein, spielen manuell Updates ein, öffnen neue Ports oder justieren Backup-Routinen. Der Server wird wie ein "Haustier" gepflegt und am Leben gehalten. Das oberste Ziel dieses Paradigmas ist eine ununterbrochene Uptime der exakt selben Maschine.

Der Architektonische Ruin: Schneeflocken und Serverfestungen

Das fatale architektonische Problem der **Mutable Infrastructure** ist die schleichende Entkopplung von der ursprünglichen Konfiguration. Zwar ist die Dokumentation manueller Eingriffe theoretisch vorgeschrieben, in der Praxis wird sie aufgrund von Zeitdruck und Dringlichkeit (z.B. bei kritischen Patches) fast immer vernachlässigt.

Daraus resultieren zwei gravierende Anti-Patterns:

1. **Der [[Schneeflocken-Effekt]]**: Wie Schneeflocken sehen die Server auf den ersten Blick identisch aus, sind aber im Detail durch abweichende, undokumentierte Änderungen völlig einzigartig. Es entsteht ein **undokumentierter Zustand**, der automatisiertes Skalieren unmöglich macht, da kein fehlerfreies Blueprint mehr existiert.
2. **Die Serverfestung**: Da niemand mehr genau weiß, welche Abhängigkeiten, Bibliotheken und manuellen Hacks auf einem System laufen, mutiert der Server zur "Festung". Administratoren unternehmen alles Erdenkliche, um einen Neustart (Reboot) zu verhindern, da das Wiederanlaufen des Systems ein massives und unkalkulierbares Risiko darstellt.

Der Weg aus der Krise

Cloud Computing erzwingt den radikalen Bruch mit diesem Paradigma. Aufgrund der Notwendigkeit, massiv [[Horizontale Skalierung]] zu betreiben, erfordert modernes Infrastrukturmanagement zwingend den Übergang zur **[[Immutable Infrastructure]]**. Der Grundgedanke dabei ist drastisch: Man startet lieber ein System neu, das erst sechs Minuten online ist, anstatt eines panisch am Leben zu erhalten, das seit sechs Jahren keinen Reboot mehr gesehen hat. Werkzeuge wie Ansible, Puppet, Docker oder Kubernetes ersetzen die händische Veränderung durch puren Code, wodurch es de facto keine nicht-codierten Infrastrukturveränderungen mehr gibt.

---

### Flashcards

Warum führt das Paradigma der Mutable Infrastructure architektonisch unausweichlich zum "Schneeflocken-Effekt" und zu "Serverfestungen"?
?
Da bei Mutable Infrastructure Server nach dem Deployment händisch verändert werden (z.B. durch Updates oder neue Ports), und diese Änderungen aus Zeitmangel oft nicht dokumentiert werden, entstehen undokumentierte Systemzustände. Jeder Server wird zu einem einzigartigen Unikat (Schneeflocke). Da die exakte Konfiguration niemandem mehr vollständig bekannt ist, fürchten Administratoren jeden Neustart – die Systeme werden zu unantastbaren "Serverfestungen".

Was ist der fundamentale Unterschied zwischen **Mutable** und **Immutable Infrastructure** hinsichtlich der Konfigurationsänderung?::Bei der traditionellen **Mutable Infrastructure** werden Systeme nach dem Deployment händisch im laufenden Betrieb modifiziert. Bei der neuen **Immutable Infrastructure** finden sämtliche Infrastrukturkonfigurationen ausschließlich als Code statt; es gibt keine manuellen, nicht-codierten Veränderungen mehr am laufenden System.

Welcher fundamentale Umdenkprozess (Mindset-Shift) ist nötig, um die Angst vor Neustarts, die bei Mutable Infrastructure vorherrscht, in Cloud-Umgebungen zu überwinden?::Administratoren müssen verinnerlichen, dass es wesentlich sicherer ist, ein aus Code reproduzierbares System neu zu starten, das erst 6 Minuten online ist, als krampfhaft ein manuell gepatchtes System zu verteidigen, das seit 6 Jahren ohne Reboot läuft.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Mutable Infrastructure]]
SORT file.mtime DESC
```