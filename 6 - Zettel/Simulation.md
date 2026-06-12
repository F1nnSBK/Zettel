#Note

2026-06-12

Tags: [[Systemarchitektur]], [[Testing]], [[Cloud Computing]]
#cloud_computing

---
In der Systemarchitektur und im Cloud Computing wird oft pauschal von der "Nachbildung" von Systemen gesprochen. Es ist architektonisch jedoch von entscheidender Bedeutung, das Ziel dieser Nachbildung zu definieren. Die **Simulation** bezeichnet die vollständige, detaillierte Nachbildung eines physisch existierenden Systems durch Software.

Der fundamentale Unterschied zu anderen Abstraktionsebenen liegt in der Zweckbindung: **Das Ziel einer Simulation liegt ausdrücklich nicht im Praxiseinsatz, sondern im Erkenntnisgewinn**. Es geht nicht darum, den Code einer Anwendung möglichst performant laufen zu lassen, sondern die **internen Wirkzusammenhänge** der Systemkomponenten unter kontrollierten Bedingungen zu beobachten und zu studieren.

Mechanik: Die Berechnung der Realität

Während ein Hypervisor bei der [[Virtualisierung]] Hardware-Aufrufe intelligent durchreicht und koordiniert, um native Performance zu erreichen, muss eine Simulation das Verhalten jeder Komponente mathematisch und logisch berechnen.

Ein klassisches Beispiel ist der **Flugsimulator**: Das Cockpit eines Flugzeugs wird samt aller Instrumente, Schalter und Steuerungslogiken exakt in Software nachgebaut. Der Zweck ist nicht, dass die Software "abhebt" oder echte produktive Logistik-Aufgaben übernimmt, sondern dass angehende Piloten gefahrlos trainieren können. Weitere typische Beispiele aus der IT-Praxis sind Wetterberechnungssysteme oder der iPhone Simulator unter macOS, in dem das Verhalten der Hardware-Sensorik (wie GPS-Bewegungen oder Touch-Gesten) für Entwicklerzwecke algorithmisch erzeugt wird.

Abgrenzungstrinität: Simulation vs. Emulation vs. Virtualisierung

Um massive Architekturfehler zu vermeiden, muss die Simulation zwingend von ihren verwandten Konzepten abgegrenzt werden:

1. **Simulation:** Bildet die _Wirkzusammenhänge_ eines Systems zum Zwecke des Erkenntnisgewinns ab. Es gibt keine produktive Ausführung von Fremdsoftware auf Hardwareebene.
2. **[[Emulation]]:** Stellt die gleichen _Funktionen_ bzw. Schnittstellen nach (z.B. Befehlssätze eines fremden Prozessors), ohne die interne physikalische Logik zwingend zu übernehmen. Sie ist praxistauglich und soll ein System (z.B. x86-Software auf ARM-Chips via Rosetta 2) ersetzen und ablauffähig machen.
3. **[[Virtualisierung]]:** Dient lediglich der _Entkopplung_ von Soft- und Hardware auf der _gleichen_ Architektur (x86 auf x86), um die geteilte Nutzung von Hardwareressourcen fast ohne Performancedefizite zu ermöglichen.

---

### Flashcards

Was ist der fundamentale architektonische Unterschied in der Zielsetzung zwischen einer Simulation auf der einen und einer Emulation bzw. Virtualisierung auf der anderen Seite?
?
Das primäre architektonische Ziel einer Simulation ist der reine **Erkenntnisgewinn** durch die exakte algorithmische Nachbildung interner Wirkzusammenhänge (z.B. Trainingszwecke im Flugsimulator). Sie ist explizit nicht für den produktiven Praxiseinsatz oder das effiziente Hosten von Software gedacht. Emulation und Virtualisierung zielen hingegen darauf ab, Software für den tatsächlichen, produktiven Betrieb ausführbar zu machen bzw. Hardware ressourceneffizient zu teilen.

Was genau wird bei einer Simulation technisch in der Software nachgebildet?::Es werden die vollständigen **internen Wirkzusammenhänge** und das physikalische/logische Verhalten der einzelnen Systemkomponenten exakt nachgebaut.

Nenne drei klassische Beispiele für den Einsatz von Simulationen.::Flugsimulatoren, komplexe Wetterberechnungen und der iPhone Simulator unter macOS zur App-Entwicklung.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Simulation]]
SORT file.mtime DESC
```