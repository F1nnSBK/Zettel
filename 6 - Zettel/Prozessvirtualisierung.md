#Note

2026-06-12

Tags: [[Virtualisierung]], [[Container]], [[Systemarchitektur]]
#cloud_computing

---
Die **Prozessvirtualisierung** markiert die radikalste Abkehr von der klassischen Virtualisierungsarchitektur. Während bei der [[Voll-Virtualisierung]] ein [[Hypervisor]] zwischengeschaltet wird, um Hardware für ein monströses, vollständiges Gast-Betriebssystem zu emulieren, verzichtet die Prozessvirtualisierung vollständig auf den Hypervisor und das Gast-OS.

Ein Container bündelt **nur die zwingend benötigten Abhängigkeiten** (Bibliotheken, Binaries) und den Anwendungscode. Anstatt einen eigenen Betriebssystem-Kernel hochzufahren, teilen sich alle Container den Kernel des zugrundeliegenden Host-Betriebssystems. Die Anwendung startet sofort, was die trägen Boot-Sequenzen herkömmlicher Virtueller Maschinen eliminiert. Bekannte Implementierungen dieses Paradigmas sind **Docker**, Cri-o und BSD-Jails.

Die architektonische Magie: cgroups und namespaces

Da der Hypervisor fehlt, muss die Isolation der Anwendungen anderweitig garantiert werden. Hierfür nutzt die Prozessvirtualisierung zwei fundamentale Funktionen des (Linux-)Kernels:

1. **[[cgroups]] (Control Groups):** Diese Funktion reguliert die _Ressourcennutzung_. Sie definiert harte Grenzen, wie viel CPU, RAM oder Netzwerk-I/O ein einzelner Container-Prozess maximal konsumieren darf.
2. **[[namespaces]]:** Diese Funktion reguliert die _Sichtbarkeit_. Sie schirmt Container logisch voneinander ab, sodass ein Container-Prozess nur seine eigenen Kindprozesse, nicht aber die Prozesse benachbarter Container sehen kann.

Trade-offs: Extreme Effizienz vs. Aufgeweichte Isolation

Dieser Paradigmenwechsel bringt gigantische Gewinne für die moderne Cloud-Infrastruktur, erfordert aber architektonische Kompromisse:

- **Der Effizienz-Gewinn:** Da Hardwareressourcen nicht (wie bei VMs) starr reserviert, sondern nur bei tatsächlichem Bedarf allokiert werden, ist die Auslastung extrem effizient. Durch den Verzicht auf das Gast-OS schrumpft die Imagegröße auf winzige **50 bis 500 MB** (im Vergleich zu 3-4 GB bei VMs). Zudem entfällt der Dolmetscher-Overhead des Hypervisors, wodurch Container **nahezu native Anwendungsgeschwindigkeiten** erreichen. All dies macht Container zum ultimativen Werkzeug für rasante **[[Horizontale Skalierung]]**.
- **Das Isolations-Defizit:** Der architektonische Preis für diese Effizienz ist eine geschwächte Isolation. Da sich alle Container den Host-Kernel teilen, kann bei einem erfolgreichen Angriff (Container Escape) potenziell der gesamte Host kompromittiert werden. Zudem existiert eine harte technologische Grenze: In Containern können nur Laufzeitumgebungen betrieben werden, die zum Host-Kernel kompatibel sind – man kann also keinen Windows-Container nativ auf einem Linux-Kernel betreiben. Im Gegensatz zu virtuellen Maschinen sehen die Container-Prozesse zudem die unmaskierte, physische Hardware.

---

### Flashcards

Wie löst die Prozessvirtualisierung architektonisch das Problem der Prozess-Isolation, da sie vollständig auf einen Hypervisor verzichtet?
?
Sie stützt sich auf zwei native Funktionen des Betriebssystem-Kernels (insb. Linux): **cgroups** (Control Groups) werden eingesetzt, um harte Limits für den Konsum physischer Ressourcen (CPU, RAM) pro Container zu setzen. **Namespaces** werden genutzt, um die logische Sichtbarkeit einzuschränken, sodass ein Container keine benachbarten Prozesse sehen oder manipulieren kann.

Was ist der fundamentale architektonische Nachteil (Trade-off) der Prozessvirtualisierung im Vergleich zur Voll-Virtualisierung hinsichtlich der Isolation und Kompatibilität?::Da Container keinen eigenen Kernel mitbringen, sondern sich den Kernel des Host-Betriebssystems teilen müssen, ist die Sicherheits-Isolation schwächer (Risiko von Container Escapes). Zudem können nur Gast-Systeme virtualisiert werden, die denselben Kernel-Typ (z.B. Linux auf Linux) wie das Host-OS verwenden.

Warum eignet sich die Prozessvirtualisierung signifikant besser für dynamische Horizontale Skalierung in Cloud-Systemen als virtuelle Maschinen?::Container enthalten kein vollwertiges Gast-Betriebssystem, wodurch ihre Imagegröße auf minimale 50-500 MB schrumpft. Dadurch entfällt das träge Booten des Betriebssystems; der Applikationsstart erfolgt sofort, und Hardware-Ressourcen werden nur bei echtem Bedarf belegt.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Prozessvirtualisierung]]
SORT file.mtime DESC
```