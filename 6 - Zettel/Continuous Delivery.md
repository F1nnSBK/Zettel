#Note

2026-06-12

Tags: [[Automatisierung]], [[DevOps]], [[Softwareentwicklung]]
#cloud_computing 

---
In historischen Entwicklungsprozessen war der Bau eines auslieferbaren Software-Releases ein hochgradig manueller, fehleranfälliger Vorgang. Entwickler mussten Konfigurationen anpassen, Abhängigkeiten bündeln und Versionsnummern händisch vergeben. **[[Continuous Delivery]]** eliminiert diese Reibung durch kompromisslose Automatisierung. Es baut architektonisch direkt auf der **[[Continuous Integration]]** auf. Sobald der Code getestet und validiert ist, automatisiert Continuous Delivery die Vorbereitung des Deployments: Den Bau der ausgelieferten Artefakte sowie die Generierung der benötigten Deploymentskripte.

Der Kernfokus dieses Paradigmas ist die Fehlervermeidung: Das explizite Ziel ist es, typische **Copy-Paste Fehler**, die beim manuellen Bauen von Artefakten (wie beispielsweise das Setzen einer falschen Versionsnummer) auftreten, vollständig zu verhindern.

Architektonische Vorstufe zum Vollautomatismus

In Cloud-Architekturen ist Continuous Delivery ein unverzichtbares Bindeglied. Systeme, die massive **[[Horizontale Skalierung]]** nutzen, verlangen nach standardisierten, verlässlichen Images oder Binärdateien. Continuous Delivery garantiert, dass das generierte Artefakt zu 100% reproduzierbar ist.

Der architektonische Zustand nach erfolgreicher Continuous Delivery ist ein "Release-bereites" Artefakt. Es liegt fertig auf Halde. Der einzige Grund, warum dieses Artefakt zu diesem Zeitpunkt nicht in der Produktion läuft, ist eine bewusste, organisatorische Entscheidung (meist ein manueller "Knopfdruck" zur Freigabe). Erst wenn auch dieser letzte manuelle Schritt durch Automatisierung ersetzt wird – das Artefakt also ohne Verzögerung sofort in Betrieb genommen wird – spricht man von der finalen Stufe: dem **[[Continuous Deployment]]**.

---

### Flashcards

Welches ganz konkrete, operative Problem löst Continuous Delivery laut Systemdefinition und wie tut es das?
?
Continuous Delivery löst das Problem menschlicher Fehler (insbesondere Copy-Paste-Fehler wie falsche Versionsnummern), die beim manuellen Zusammenbauen von Software entstehen. Es tut dies, indem es den Bau der ausgelieferten Artefakte sowie der benötigten Deploymentskripte vollautomatisiert.

Welche zwingende Voraussetzung muss erfüllt sein, bevor Continuous Delivery greifen kann?::Die [[Continuous Integration]] (CI) muss erfolgreich durchlaufen sein, da Continuous Delivery direkt darauf aufbaut.

Was ist der funktionale Unterschied zwischen Continuous Delivery und Continuous Deployment?::Continuous Delivery automatisiert die Auslieferung (Vorbereitung des Deployments/Bau des Artefakts), während Continuous Deployment darauf aufbaut und auch die tatsächliche Inbetriebnahme der aktualisierten Softwareversion vollautomatisiert durchführt.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Continuous Delivery]]
SORT file.mtime DESC
```