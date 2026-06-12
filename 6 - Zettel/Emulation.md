#Note

2026-06-12

Tags: [[Systemarchitektur]], [[Virtualisierung]], [[Cloud Computing]]
#cloud_computing

---
In der IT-Infrastruktur ist Software traditionell fest an die Befehlssätze einer spezifischen Prozessorarchitektur (z.B. x86) gebunden. Wenn nun ein Paradigmenwechsel der Hardware ansteht (z.B. der Wechsel zu ARM-Prozessoren), steht die Systemarchitektur vor dem Problem massiver Inkompatibilität. Die **Emulation** löst dieses Problem: Sie beschreibt die Nachbildung der **Schnittstellen** eines physischen oder virtuellen Systems.

Der entscheidende Unterschied zur [[Simulation]] ist der Verzicht auf das Berechnen von physikalischen Interna. Eine Emulation übernimmt explizit _nicht_ die internen **Wirkzusammenhänge**. Stattdessen werden angepasste Programmroutinen eingesetzt, die den eingehenden Befehl (Input) funktional so übersetzen, dass auf der neuen Hardware der exakt gleiche Output entsteht. Das absolute Primärziel der Emulation ist die **Praxistauglichkeit**: Sie soll ein System vollständig ersetzen und produktiv ablauffähig machen.

Der Preis der Übersetzung: Performance

Während die **[[Virtualisierung]]** auf derselben Architektur operiert (z.B. x86 auf x86) und deshalb fast native Geschwindigkeiten erreicht, da Befehle nur verwaltet und durchgereicht werden müssen, erfordert die Emulation eine echte **Übersetzung** von fremden Befehlssätzen. Diese Echtzeit-Übersetzung erzeugt massive Performance-Defizite. Die CPU muss nicht nur die eigentliche Anwendung berechnen, sondern zeitgleich permanent als Dolmetscher fungieren.

Trotz dieses massiven Overheads ist die Emulation ein essenzieller Brückenbauer in der IT-Historie. Prominente Praxisbeispiele, die ganze Ökosysteme gerettet haben, sind **Rosetta 2** (das Apple nutzt, um alte x86-Mac-Anwendungen auf neuen ARM-Chips auszuführen) oder das **Windows Subsystem for Linux (WSL 1)**, bei dem Linux-Systembefehle in Windows-Befehle übersetzt und die Ergebnisse zurückgeliefert werden. Auch die **Java Virtual Machine (JVM)** ist im Kern ein Emulator für Java-Bytecode.

---

### Flashcards

Was ist der fundamentale architektonische Unterschied zwischen Emulation und Simulation bezüglich der internen Systemlogik?
?
Die Simulation bildet die internen **Wirkzusammenhänge** eines Systems exakt nach (Zweck: Erkenntnisgewinn, nicht Produktivbetrieb). Die Emulation bildet nur die **Schnittstellen** nach und nutzt angepasste Programmroutinen, um denselben Output zu erzeugen, verzichtet aber auf die Nachbildung interner Wirkzusammenhänge (Zweck: produktiver Praxiseinsatz).

Warum weist die Emulation im Vergleich zur Virtualisierung in der Regel massive Performanceverluste auf?::Weil die Emulation Befehlssätze einer _fremden_ Architektur (z.B. x86 zu ARM) zur Laufzeit rechenintensiv aktiv übersetzen muss, während Virtualisierung auf der _gleichen_ Architektur operiert und Hardware lediglich aufteilt.

Nenne drei konkrete Praxisbeispiele für Emulationslösungen aus der Systemarchitektur.::Rosetta (1 & 2 für macOS), das Windows Subsystem for Linux (WSL1) und die Java Virtual Machine (JVM).

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Emulation]]
SORT file.mtime DESC
```