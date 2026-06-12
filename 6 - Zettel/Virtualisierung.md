#Note

2026-06-12

Tags: [[Systemarchitektur]], [[Cloud Computing]], [[Infrastruktur]]
#cloud_computing

---
Traditionelle Systemarchitekturen waren strikt vertikal gekoppelt: Eine Anwendung lief auf einem Betriebssystem, welches fest an eine spezifische physische Hardware gebunden war. **Virtualisierung** durchbricht dieses starre Paradigma durch die systematische Entkopplung der Ausführungsumgebung von der physischen Hardware. Durch eine Virtualisierungssoftware werden abstrakte Repräsentationen der physischen Hardware erzeugt. Das Resultat ist, dass mehrere isolierte Ausführungsumgebungen gleichzeitig auf derselben Maschine operieren können, ohne dass es beim Zugriff auf CPU oder RAM zu Konflikten kommt.

Architektonische Abgrenzung: Simulation vs. Emulation vs. Virtualisierung

Um Virtualisierung architektonisch sauber einzuordnen, muss sie von ähnlichen Konzepten abgegrenzt werden:

1. **Simulation:** Das _vollständige Nachbilden_ der internen Wirkzusammenhänge eines Systems (z.B. Flugsimulator) primär zum Erkenntnisgewinn, nicht für den produktiven Betrieb.
2. **Emulation:** Das Nachbilden von Hardwareschnittstellen, um Software für eine _fremde_ Architektur (z.B. x86-Software auf ARM-Chips via Rosetta 2) ausführbar zu machen. Hierbei werden Befehle aktiv und ressourcenintensiv übersetzt.
3. **Virtualisierung:** Arbeitet auf der _gleichen_ Komponentenarchitektur (x86 auf x86). Es geht nicht um Übersetzung der Befehlssätze, sondern um die Entkopplung und das konfliktfreie Teilen der Hardware. Das Ergebnis ist eine nahezu native Performance mit drastisch geringeren Verlusten als bei der Emulation.

Die drei architektonischen Säulen der Virtualisierung

Die Einführung von Virtualisierung liefert in der Systemarchitektur drei fundamentale operative Hebel:

- **Isolation der Anwendungen:** Laufzeitfehler, Bibliothekskonflikte und Abstürze (Seiten-Effekte) werden durch striktes Sandboxing auf die jeweilige virtuelle Umgebung begrenzt. Die Host-Hardware und benachbarte Instanzen bleiben geschützt.
- **Multiplizität von Systemen:** Die Fähigkeit, Alt- und Neu-Systeme parallel auf derselben Hardware zu betreiben, maximiert die Auslastung der physischen Ressourcen drastisch und führt zu einer massiven Fixkostendegression (Kosten für Strom, Hardware und Personal werden auf viele Systeme verteilt).
- **Portabilität der Systemkonfiguration:** Da die Umgebung nur noch als Software-Abbild existiert, kann das gesamte System blitzschnell auf neue Hardware umgezogen, kopiert oder für identische Dev/Prod-Umgebungen dupliziert werden.

Trotz all dieser massiven Abstraktionsvorteile bleibt eine architektonische Konstante bestehen: **Virtualisierung überwindet keine physikalischen Grenzen**. Die maximal verfügbare Leistung der virtuellen Maschinen wird letztendlich immer durch die harte physikalische Realität der darunterliegenden Hardware (Limit von CPU, RAM, IOPS) gedeckelt.

---

### Flashcards

Was ist der fundamentale architektonische Unterschied zwischen Emulation und Virtualisierung?
?
Die Emulation übersetzt Befehle einer fremden Architektur (z.B. x86 zu ARM), was massive Performanceverluste bedeutet. Virtualisierung hingegen operiert auf der exakt gleichen Architektur (z.B. x86 auf x86) und dient lediglich der Entkopplung und dem konfliktfreien Teilen der Hardware, wodurch nahezu native Geschwindigkeiten erreicht werden.

Welche drei architektonischen Hauptvorteile bietet der Einsatz von Virtualisierung beim Betrieb von Software?::1. **Isolation** (Eindämmung von Laufzeitfehlern/Konflikten), 2. **Multiplizität** (parallele Auslastung der Hardware zur Kostensenkung), 3. **Portabilität** (hardwareunabhängiger Umzug und Duplikation der Systeme).

Hebt Virtualisierung die Leistungsbeschränkungen der IT-Infrastruktur auf?::Nein. Obwohl Virtualisierung von der Hardware abstrahiert, wirken sich die harten physikalischen Leistungsgrenzen (CPU, RAM, Speicherkapazität) der physischen Maschine direkt auf das Maximum der virtuellen Ausführungsumgebungen aus.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Virtualisierung]]
SORT file.mtime DESC
```