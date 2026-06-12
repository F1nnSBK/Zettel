#Note

2026-06-12

Tags: [[Cloud Computing]], [[Skalierung]], [[Systemarchitektur]]
#cloud_computing 

---
Die **Vertikale Skalierung**, auch **Scale-Up** genannt, klassifiziert jene Form der Leistungssteigerung, bei der keine zusätzlichen Rechner in das System integriert, sondern Hardwarekomponenten der bestehenden Maschine durch leistungsstärkere Alternativen ausgetauscht oder ergänzt werden. Typische Beispiele hierfür sind die Erhöhung des Arbeitsspeichers (RAM) oder der Austausch des Prozessors (CPU). Ein Beispiel für einen exponentiellen Skalierungsfaktor bei der vertikalen Skalierung ist der Austausch einer traditionellen Festplatte durch eine SSD, da hierdurch jeder einzelne Speicherzugriff innerhalb der Anwendung beschleunigt wird.

Der größte und verlockendste Vorteil dieser Methode für Entwickler liegt auf der Hand: **Die Anwendung muss für derartige Leistungssteigerungen nicht architektonisch angepasst werden**. Monolithische Legacy-Anwendungen können einfach auf eine größere virtuelle oder physische Maschine umgezogen werden und profitieren sofort von der gesteigerten Rechenkraft.

Die harten architektonischen Grenzen

Trotz der Einfachheit bringt die vertikale Skalierung signifikante, oft geschäftskritische Nachteile mit sich, die sie für massiv wachsende, moderne Cloud-Applikationen untauglich machen:

1. **Zwang zur Systemunterbrechung (Downtime):** Um Hardware auszutauschen oder eine virtuelle Maschine auf ein größeres Leistungsprofil ("larger instance size") umzustellen, muss das System fast immer gestoppt werden. Diese Unterbrechungen ("Usually disruptive") sind für hochverfügbare Systeme inakzeptabel.
2. **Die physikalische Decke:** Skalierung durch Hardware-Upgrades ist nur bis zu einer gewissen absoluten Grenze möglich. Irgendwann ist der leistungsstärkste Prozessor oder das Mainboard mit dem maximalen RAM-Fassungsvermögen erreicht. An diesem Punkt diktiert die Rechnerarchitektur das harte Ende des Wachstums.

Im Cloud Computing ist vertikale Skalierung zwar wesentlich schneller durchführbar als im [[On-Premise]]-Betrieb, da Ressourcen per API getauscht werden können, doch die Limitierungen durch Downtimes und physikalische Obergrenzen bleiben bestehen. Daher zwingen hyper-skalierende Systeme Architekten letztendlich immer zur [[Horizontale Skalierung]].

---

### Flashcards

Warum gilt die vertikale Skalierung (Scale-Up) als einfachster, aber gleichzeitig am stärksten limitierter Weg zur Leistungssteigerung einer Anwendung?
?
Sie ist am einfachsten, weil sie keinerlei architektonische Anpassungen am Code der Anwendung erfordert; die Hardware wird schlichtweg aufgerüstet (z.B. mehr RAM, stärkere CPU). Sie ist jedoch stark limitiert, da für das Aufrüsten zwingend eine Systemunterbrechung (Downtime) in Kauf genommen werden muss und das Wachstum durch harte physikalische Hardwaregrenzen (die Rechnerarchitektur) gedeckelt ist.

Welchen entscheidenden Vorteil hat Scale-Up (vertikale Skalierung) gegenüber Scale-Out (horizontale Skalierung) aus Sicht der Softwareentwicklung?::Es sind absolute keine Änderungen an der Anwendungsarchitektur erforderlich; die Software muss im Gegensatz zu Scale-Out keine verteilte Lastverteilung unterstützen.

Was ist ein konkretes Beispiel für einen exponentiellen Skalierungsfaktor bei vertikaler Skalierung?::Der Austausch einer klassischen Festplatte durch eine SSD, da dadurch jeder Speicherzugriff der Anwendung unmittelbar beschleunigt wird.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Vertikale Skalierung]]
SORT file.mtime DESC
```