#Note

2026-06-12

Tags: [[Infrastruktur]], [[Hosting]], [[Systemarchitektur]]
#cloud_computing

---
Das Paradigma der Eigenverantwortung

Das **On-Premise**-Modell ist der traditionelle Gegenentwurf zum [[Cloud Computing]]. Bei diesem Nutzungsmodell kauft der Kunde die Hard- und Software und betreibt diese vollständig in der eigenen IT-Infrastruktur. Der architektonische Kern dieses Modells ist die **Eigentümerschaft**: Das Unternehmen ist nicht nur Nutzer, sondern auch Betreiber. Dies ermöglicht **tiefe Anpassungen** auf Hardwareebene (z.B. spezifische Grafikkartenauswahl, dedizierte Speichersysteme),. Die Kehrseite dieses Paradigmas ist das **Ausfallrisiko**: Der Kunde trägt die volle Verantwortung für Patches, den Livegang und Hardware-Defekte,.

Architektonische Schmerzpunkte und Trade-offs

In der Systemarchitektur zeigt On-Premise signifikante Reibungsverluste bei der Skalierbarkeit und Agilität. Die Skalierung ist primär **vertikal** oder durch sehr träge **horizontale Skalierung** limitiert, da neue Server erst beschafft, geliefert und integriert werden müssen (Bereitstellungszeiten von 2-6 Monaten).

Zwei fundamentale Probleme prägen den On-Premise-Betrieb:

1. **Der Schneeflocken-Effekt (Serverfestungen):** Infrastruktur wird nach dem Deployment händisch verändert (Updates, Port-Freigaben). Da diese manuellen Änderungen oft nicht als Code automatisiert dokumentiert werden (fehlende [[Immutable Infrastructure]]), entstehen singuläre, nicht reproduzierbare Konfigurationen ("Schneeflocken"). Kommt es zum Ausfall, ist ein sicherer Wiederanlauf massiv gefährdet,.
2. **Hemmung von Innovation:** Wegen der **hohen Kapitalbindung** und des Ausfallrisikos werden oft keine Software-Experimente gewagt. Der Status Quo wird "verteidigt", und Updates werden nur dann durchgeführt, wenn sie absolut unvermeidbar sind. Es kommt zu einem [[Vendor Lock-In]] bei Hardwareherstellern, um Beschaffungskosten zu drücken.

Berechtigung in modernen Architekturen

Trotz der Nachteile bleibt On-Premise architektonisch relevant für extreme Edge-Cases. Dazu gehören **Airgap-Umgebungen**, bei denen IT-Infrastruktur physisch von externen Netzwerken getrennt sein muss (z.B. Militär, kritische Produktionsanlagen). Auch bei Szenarien, die durchgehend maximal vorhersagbare, extrem hohe Lasten ohne Varianz aufweisen, kann der Kauf von Hardware betriebswirtschaftlich günstiger sein als die Miete in der Cloud, sofern das Personal für den Betrieb vorhanden ist.

---

### Flashcards

Warum führt der traditionelle On-Premise-Betrieb architektonisch häufig zum sogenannten "Schneeflocken-Effekt" (Serverfestungen) und warum ist das kritisch?
?
Beim traditionellen On-Premise-Betrieb werden Änderungen (Patches, neue Ports) oft manuell auf den Servern durchgeführt und unzureichend dokumentiert. Dadurch entstehen einzigartige Konfigurationen ("Schneeflocken"), die nicht per Code (wie bei Infrastructure-as-Code) reproduzierbar sind. Bei einem Ausfall ist der sichere Wiederanlauf kaum zu garantieren,.

Was sind die massivsten wirtschaftlichen und agilen Nachteile des On-Premise-Modells?::Hohe Startinvestitionen (Kapitalbindung), sehr lange Bereitstellungszeiten (2-6 Monate für neue Hardware) und das Tragen des vollen Ausfallrisikos,.

Für welches spezifische Sicherheits-Szenario bleibt On-Premise ein oft unverzichtbares Architekturmuster?::Für sogenannte "Airgap"-Umgebungen, in denen Infrastruktur physisch komplett vom Internet getrennt betrieben werden muss, um höchste Datensouveränität und Isolation zu gewährleisten.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[On-Premise]]
SORT file.mtime DESC
```