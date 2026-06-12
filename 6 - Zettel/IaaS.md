#Note

2026-06-12

Tags: [[Cloud Computing]], [[Systemarchitektur]], [[Virtualisierung]], [[Servicemodelle]]
#cloud_computing

---
Innerhalb der Cloud-Servicemodelle stellt **Infrastructure as a Service (IaaS)** die niedrigste und grundlegendste Abstraktionsebene dar. Anstatt Server physisch im eigenen Keller zu betreiben ([[On-Premise]]), mietet das Unternehmen logische Hardwareressourcen über das Internet. Der Cloud-Provider abstrahiert hierbei die Ebenen der **Hardware** und des **Hypervisors**.

Der entscheidende architektonische Schnittpunkt liegt beim **Betriebssystem**: Der Provider stellt die virtuelle Maschine zur Verfügung und garantiert vertraglich (über SLAs) deren Verfügbarkeit, aber der Kunde ist vollständig frei darin, welches Betriebssystem er wählt, welche Programme er installiert und wie er das System konfiguriert. Der Kunde kann sogar bereits bestehende eigene VMs (Images) direkt zum Provider hochladen.

Die Leasing-Analogie

Um die architektonischen Implikationen von IaaS greifbar zu machen, eignet sich in der Transport-Metapher das **Leasing eines Autos**. Beim Autokauf (On-Premise) trägt man die maximale Investition und das volle Risiko. Beim Leasing (IaaS) wählt der Fahrer (Kunde) aus einer moderaten Auswahl an Konfigurationen und zahlt eine monatliche, nutzungsabhängige Rate. Das Auto (der Server) geht jedoch nie in das Eigentum des Fahrers über; es bleibt Fremdeigentum. Fällt der Motor physisch aus, ist die Leasinggesellschaft (Provider) für den Austausch verantwortlich.

Trade-offs: Flexibilität vs. Administrativer Overhead

Der massive Vorteil von IaaS ist der Wegfall gigantischer Anfangsinvestitionen (CapEx) bei gleichzeitiger Möglichkeit, Hardwareressourcen extrem flexibel und grenzenlos zu skalieren.

Der architektonische Preis für diese maximale Freiheit ist jedoch der hohe **Wartungsaufwand**. Da der Kunde die volle Kontrolle ab dem Betriebssystem innehat, ist er auch zwingend für sämtliche OS-Updates, Sicherheitspatches und Laufzeitumgebungen verantwortlich. IaaS löst das Problem der physischen Hardwarebeschaffung, befreit IT-Abteilungen aber nicht von der Pflicht, sichere und stabile Serverumgebungen zu administrieren.

---

### Flashcards

Was stellt der Cloud-Provider bei Infrastructure as a Service (IaaS) konkret zur Verfügung und auf welcher Architekturebene beginnt die Verantwortung des Kunden?
?
Der Cloud-Provider stellt logische Hardwareressourcen zur Verfügung und abstrahiert die physische Hardware sowie den Hypervisor. Die Verantwortung des Kunden beginnt beim **Betriebssystem**; er muss dieses selbst auswählen, konfigurieren, mit Programmen bestücken und fortlaufend patchen.

Welche reale Transport-Analogie beschreibt das IaaS-Modell am besten und warum?::Die Analogie des **Auto-Leasings**. Der Kunde zahlt eine monatliche Rate und kann das Auto (den Server) nutzen, ohne die hohen initialen Kaufkosten zu tragen. Das Auto bleibt jedoch Fremdeigentum, und fundamentale physische Hardware-Wartungen übernimmt die Leasinggesellschaft (der Provider).

Wie sichert der Cloud-Provider bei IaaS die Verlässlichkeit der gebuchten Hardware-Ressourcen ab?::Durch sogenannte **Service Level Agreements (SLAs)**, in denen der Provider dem Kunden vertraglich eine konkrete Verfügbarkeit (Uptime) der Hardwareressourcen zusichert.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[IaaS]]
SORT file.mtime DESC
```