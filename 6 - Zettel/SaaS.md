#Note

2026-06-12

Tags: [[Cloud Computing]], [[Servicemodelle]], [[Systemarchitektur]], [[Softwareentwicklung]]
#cloud_computing

---
Innerhalb der Cloud-Schichtenarchitektur markiert **Software as a Service (SaaS)** die absolute Endstufe der Abstraktion und somit den maximalen Kontrollverlust für den Nutzer. Bei SaaS wird die gesamte Anwendung vom Cloud-Anbieter entwickelt, gehostet und operativ betrieben. Der Nutzer bekommt keinerlei Einblicke in den Aufbau der verwendeten Software, das Betriebssystem oder die zugrundeliegende Hardwareausstattung. Der Kunde konsumiert lediglich die fertigen Anwendungsfunktionen über eine Schnittstelle oder den Webbrowser.

Der Trade-off: Wartungsfreiheit gegen Vendor Lock-in

Dieser radikale Kontrollverlust hat zwei gegensätzliche Effekte auf die Systemarchitektur eines Unternehmens:

- **Maximale Wartungsfreiheit:** Das Unternehmen muss sich um keinerlei Betriebsaufgaben wie Patching, Skalierung, Failover oder Hardware-Upgrades kümmern, da all diese Verpflichtungen vollständig an den Provider ausgelagert sind.
- **Maximaler Lock-in Effekt:** Da der Funktionsumfang vom Anbieter fest vorgegeben ist und nur sehr oberflächlich konfiguriert werden kann, besteht ein extremer Vendor Lock-in. Die Portabilität der Anwendung zu einem anderen Cloud-Anbieter ist de facto nicht gegeben, da SaaS-Produkte meist proprietäre Differenzierungsmerkmale der jeweiligen Provider darstellen.

Die Analogie: Die Bus-Dauerkarte

Um die architektonischen Implikationen von SaaS zu veranschaulichen, eignet sich in der Transport-Metapher die **Fahrt in einem Bus mit Dauerkarte**. Der Kunde ist hierbei reiner Beifahrer und hat keine Mitsprache bei der Ausführung, der Streckenführung oder der Fahrzeugklasse. Er zahlt eine monatliche Abrechnungsgebühr für ein Fahrzeug, das Fremdeigentum bleibt und dessen ausgelagerte Wartung vom Verkehrsbetrieb (dem Provider) übernommen wird.

---

### Flashcards

Was ist das definierende Hauptmerkmal von Software as a Service (SaaS) hinsichtlich der Verantwortungsverteilung zwischen Cloud-Provider und Kunde?
?
Bei SaaS entwickelt, hostet und betreibt der Cloud-Provider die gesamte Anwendung vollständig in Eigenregie. Der Kunde hat keinen Einfluss auf den Betrieb, verwaltet keine Infrastruktur und konsumiert die Software lediglich als fertiges Endprodukt.

Warum birgt das SaaS-Servicemodell von allen Cloud-Modellen die größte Gefahr für einen Vendor Lock-in?::Weil die Anwendung und ihr Betriebszustand vollständig an einen proprietären Anbieter gebunden sind. Der Funktionsumfang ist fest vorgegeben, und eine Portabilität der Applikation (ein Umzug zu einem anderen Provider) ist de facto nicht möglich, da die SaaS-Anwendungen spezifische Differenzierungsmerkmale der Anbieter sind.

Mit welcher Transport-Analogie lässt sich das SaaS-Modell am besten beschreiben und welche Eigenschaften gehen damit einher?::Mit einer **Dauerkarte für den Bus**. Der Kunde ist reiner Beifahrer, nutzt ein fremdes Transportmittel (Fremdeigentum) gegen eine monatliche Abrechnung und hat keinerlei Mitspracherecht an der Ausführung oder Konfiguration des Fahrzeugs.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[SaaS]]
SORT file.mtime DESC
```