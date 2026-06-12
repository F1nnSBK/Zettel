#Note

2026-06-12

Tags: [[Cloud Computing]], [[Systemarchitektur]], [[Bereitstellungsmodelle]]
#cloud_computing

---
Die **Public Cloud** ist die bekannteste und am weitesten verbreitete Bereitstellungsform des Cloud Computings. Bei diesem Modell teilt sich ein Unternehmen die gigantische, weltweit verteilte Infrastruktur eines Providers (wie AWS, Azure, Google Cloud) mit der breiten Öffentlichkeit.

Der fundamentale architektonische Unterschied zum lokalen Betrieb liegt in der massiven Abgabe von Verantwortung: Das Unternehmen überträgt große Teile der klassischen Betriebsaufgaben und der Hardware-Wartung vollständig an den Cloud-Anbieter. Von allen Bereitstellungsmodellen besitzt die Public Cloud somit den **geringsten Wartungsaufwand** und zeitgleich die **höchste Abstraktion** von der eingesetzten Infrastruktur.

Die Hebelwirkung: Skalierung und Skaleneffekte

Die Nutzung einer Public Cloud ist besonders für Projekte mit vielen Unsicherheiten, global verteilten Nutzern oder dem Bedarf an hoch-innovativen Funktionen prädestiniert. Sie ermöglicht es Unternehmen, architektonische Vorteile zu realisieren, die im Eigenbetrieb unmöglich wären:

1. **Volles Skalierungspotenzial:** Ressourcen können extrem dynamisch hoch- und heruntergefahren werden.
2. **Globale Infrastruktur:** Die Applikationen können mit minimalen Latenzen weltweit bereitgestellt werden.
3. **Wirtschaftlichkeit:** Es greift die Fixkostenvariabilisierung, gepaart mit den massiven Skaleneffekten, die der Provider an die Kunden weitergeben kann.

Der Preis: Kontrollverlust und [[Lock-In]]

Dieser immense Gewinn an Agilität und Wartungsfreiheit erfordert einen harten Kompromiss in der Systemarchitektur. Der Kunde hat nur eine **eingeschränkte Kontrolle** und extrem begrenzte Einblicke in die tatsächlich verwendete Soft- und Hardware des Providers. Das kritischste Architekturrisiko ist die **Gefahr eines Lock-In Effekts**. Da der Betrieb der eigenen Anwendungen und Prozesse zunehmend an die spezifischen Beschaffenheiten, proprietären Schnittstellen und innovativen Leistungen des Public-Cloud-Anbieters angepasst wird, wird ein späterer Umzug zu einem Konkurrenten oder zurück in eine On-Premise-Umgebung technisch extrem komplex und teuer.

---

### Flashcards

Was ist das definierende Hauptmerkmal der Public Cloud hinsichtlich ihrer Zielgruppe und der Betriebsverantwortung?
?
Eine Public Cloud nutzt einen Anbieter, der seine virtuellen IT-Ressourcen der **breiten Öffentlichkeit** anbietet. Der Kunde gibt hierbei die klassische Verantwortung für **Betriebsaufgaben** und die Wartung der zugrundeliegenden Infrastruktur fast vollständig an den Provider ab.

Welche vier zentralen architektonischen und ökonomischen Vorteile können durch den Einsatz einer Public Cloud realisiert werden?
?
1. **Fixkostenvariabilisierung** (Umwandlung von festen in nutzungsabhängige Kosten).
2. Nutzung massiver **Skaleneffekte** des Providers.
3. Zugriff auf eine **globale IT-Infrastruktur** zur Minimierung von Latenzen.
4. **Volles Skalierungspotenzial** für die dynamische Anpassung an Lastspitzen.

Welches fundamentale Architektur-Risiko (Trade-off) entsteht durch die Auslagerung von Systemen in die Public Cloud?
?
Die stark **eingeschränkte Kontrolle** über die verwendete Hard- und Software. Da Anwendungen zunehmend an die spezifischen Dienste und Schnittstellen des Providers angepasst werden, entsteht eine massive Gefahr für einen **Lock-In Effekt**, der spätere Providerwechsel drastisch erschwert.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Public Cloud]]
SORT file.mtime DESC
```