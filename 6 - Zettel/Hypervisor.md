#Note

2026-06-12

Tags: [[Virtualisierung]], [[Systemarchitektur]], [[Cloud Computing]]
#cloud_computing

---
In traditionellen Systemarchitekturen kommuniziert ein Betriebssystem (über seinen Kernel) direkt mit der Hardware. Die **Voll-Virtualisierung** erfordert jedoch eine Instanz, die diese 1:1-Beziehung aufbricht und den Hardware-Zugriff orchestriert: den **Hypervisor**.

Der Hypervisor ist die zentrale Abstraktionsschicht. Da Gast-Betriebssysteme in einer Voll-Virtualisierung nicht angepasst werden (sie "glauben", allein auf der Hardware zu laufen), greifen sie blindlings auf vermeintliche Hardware zu. Der Hypervisor **fängt sämtliche Hardwarebefehle ab** (Interception) und modifiziert diese zur Laufzeit, sodass die Befehle konfliktfrei und streng isoliert auf die tatsächliche physische Hardware gemappt werden. Um die erheblichen Latenzen dieser Dolmetscher-Arbeit zu reduzieren, ist moderne Systemarchitektur zwingend auf **Hardware-Virtualisierung (wie z.B. den CPU-Befehlssatz VT-x)** angewiesen, was den Leistungsverlust auf ca. 5% bis 10% drückt.

Architektonische Klassifizierung: Typ I vs. Typ II

Um Hypervisor-Konzepte in Systemlandschaften bewerten zu können, muss ihre Ausführungsebene präzise differenziert werden:

1. **Bare-Metal Hypervisor (Typ I):** Dieser Hypervisor sitzt architektonisch **direkt über der blanken Hardware**, ohne ein vollständiges Betriebssystem als Basis. Er ist ein extrem schlanker Spezialist, der meist keine grafische Oberfläche (GUI) besitzt und über Weboberflächen administriert wird.
2. **Architektonischer Vorteil:** Er erzielt maximale **Performance** (Aufrufe gehen direkt an die Hardware) und ein Höchstmaß an **Sicherheit**. Da auf der Host-Ebene keine anderen Programme (wie Office-Anwendungen oder Browser) laufen, ist das Risiko, über Drittsoftware Malware einzuschleusen, extrem minimiert. Prominente Vertreter sind VMWare ESX-i und Hyper-V.
3. **Hosted Hypervisor (Typ II):** Dieser Hypervisor wird wie eine reguläre Applikation **auf einem vollwertigen Betriebssystem (Host-OS)** installiert.
4. **Architektonischer Trade-off:** Jeder Hardware-Aufruf einer VM muss vom Hypervisor übersetzt und dann _zusätzlich_ an das Host-OS weitergereicht werden, was erhebliche **Performancedefizite** erzeugt. Zudem ist das **Sicherheitsrisiko (Angriffsfläche)** massiv erhöht, da alle nebenläufigen Applikationen auf dem Host-OS potenziell Schadsoftware einführen könnten. Der einzige architektonische Vorteil ist die **Multifunktionalität** (z.B. Entwicklungsarbeit und VM-Betrieb auf demselben Rechner). Bekannte Beispiele sind VirtualBox, Parallels oder VMWare Workstation.

---

### Flashcards

Was ist der fundamentale architektonische Unterschied zwischen einem Typ-I (Bare-Metal) und einem Typ-II (Hosted) Hypervisor hinsichtlich Performance und Sicherheit?
?
Ein **Typ-I-Hypervisor** sitzt direkt auf der nackten Hardware. Er bietet maximale Performance (direkte Hardwareaufrufe) und extrem hohe Sicherheit, da keine Angriffsfläche durch weitere Software auf Host-Ebene existiert. Ein **Typ-II-Hypervisor** läuft als reguläre Applikation auf einem vollständigen Host-OS. Das kostet Performance (zusätzliche Übersetzungsschicht durch das Host-OS) und senkt die Sicherheit drastisch, da andere Host-Applikationen Malware einschleusen können.

Wie löst der Hypervisor das Problem des Hardwarezugriffs unmodifizierter Gast-Betriebssysteme bei der Voll-Virtualisierung?::Er fängt sämtliche unmodifizierten Hardwarebefehle der virtuellen Maschinen ab, modifiziert sie zur Laufzeit und stellt sicher, dass jede VM konfliktfrei nur ihr zugewiesenes Ressourcenkontingent nutzt.

Welche Hardware-Technologie ist unverzichtbar, um den prinzipbedingten Leistungsverlust der Befehlsübersetzung durch den Hypervisor auf etwa 5% bis 10% zu drücken?::Die Nutzung von CPUs, die **Hardware-Virtualisierung** (z.B. den Befehlssatz **VT-x**) auf Chipebene unterstützen.



---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Hypervisor]]
SORT file.mtime DESC
```