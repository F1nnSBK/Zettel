#Note

2026-06-12

Tags: [[Cloud Computing]], [[Systemarchitektur]], [[Bereitstellungsmodelle]], [[Infrastruktur]]
#cloud_computing

---
Das Bereitstellungsmodell der **Hybrid Cloud** ist der architektonische Kompromiss aus maximaler Kontrolle und maximaler Skalierbarkeit. Es beschreibt die kombinierte, parallel laufende Nutzung einer [[Private Cloud]] und einer [[Public Cloud]] zur Ressourcenbereitstellung.

Damit diese Kombination nicht in einem administrativen Chaos endet, kommt zwingend eine **einheitliche Verwaltungssoftware** (wie z.B. für "Federated Application Management") zum Einsatz. Die Brillanz dieses Architekturansatzes liegt in der Abstraktion: Die Verwaltungssoftware verschleiert für den Endnutzer völlig, ob die angeforderten virtuellen Ressourcen lokal im eigenen Rechenzentrum oder aus der Public Cloud zur Verfügung gestellt werden. Über diese zentrale Management-Schicht lassen sich zudem unternehmensweite Governance- und Sicherheitskonzepte einheitlich durchsetzen.

Das Einsatzszenario: Skalierung trifft Datensouveränität

Die Hybrid Cloud spielt ihre Stärken primär bei Softwareprojekten aus, die zwei scheinbar widersprüchliche Anforderungen haben: Einerseits den **Schutz hochsensibler Daten** und andererseits den **Bedarf an kurzfristiger, massiver Skalierung**.

Ein klassisches Beispiel ist ein E-Commerce Unternehmen: Die kritischen Kundendatenbanken und Kernsysteme verbleiben sicher in der lokalen Private Cloud. Kommt es nun am "Black Friday" zu einem rasanten Anstieg der Nutzerzahlen, lagert das System die ressourcenintensiven, aber weniger datenschutzkritischen Web-Frontend-Prozesse dynamisch in die Public Cloud aus. So wird die Integration bestehender On-Premise IT-Infrastruktur mit den massiven Skalierungsvorteilen der Public Cloud realisiert.

Der Trade-off: Geringerer Lock-in, aber maximale Komplexität

Gegenüber einer reinen Private Cloud verringert sich in einer hybriden Umgebung der relative Wartungsaufwand und die Abstraktion der Infrastruktur steigt, da große Teile des skalierenden Betriebs an den Public-Cloud-Anbieter ausgelagert werden. Zudem sinkt durch die übergreifende Verwaltung und die Streuung der Workloads die generelle Gefahr eines Vendor Lock-In Effekts.

Der architektonische Preis für diese Flexibilität ist jedoch extrem hoch:

1. **Verantwortungsdualität:** Das Unternehmen muss weiterhin die Beschaffung und Wartung des lokalen Betriebs stemmen, ist aber _zusätzlich_ für die komplexe Konfiguration der Public Cloud Infrastruktur verantwortlich.
2. **Hohe Konfigurationskomplexität:** Die nahtlose Netzwerk- und Datenintegration zwischen lokaler Hardware und Public Cloud ist fehleranfällig und architektonisch hoch anspruchsvoll.
3. **Doppelte Kostenstruktur:** Letztendlich müssen die hohen Gesamtkosten für den dauerhaften Betrieb beider Umgebungen (Private und Public) parallel getragen werden.

---

### Flashcards

Was ist das fundamentale Konzept einer Hybrid Cloud und wie wird diese technische Trennung für den Endanwender unsichtbar gemacht?
?
Die Hybrid Cloud kombiniert die Nutzung einer Private Cloud und einer Public Cloud. Dies wird über eine einheitliche Verwaltungssoftware orchestriert, welche für den Nutzer komplett verschleiert, aus welcher der beiden Umgebungen die Ressourcen tatsächlich bereitgestellt werden.

Für welches spezifische architektonische Problem (Einsatzgebiet) ist die Hybrid Cloud die ideale Lösung?::Für Projekte, die den strengen Schutz sensibler Daten (über die lokale Private Cloud) garantieren müssen, aber gleichzeitig auf kurzfristige, massive Skalierung bei Lastspitzen (über die Public Cloud) angewiesen sind.

Welche zwei massiven wirtschaftlichen und technischen Trade-offs entstehen durch den Betrieb einer Hybrid Cloud?::Es entsteht eine sehr **hohe Konfigurationskomplexität** bei der Einrichtung der Systeme und es müssen **hohe Gesamtkosten** getragen werden, da das Unternehmen die Betriebskosten für die eigene Private Cloud und die genutzte Public Cloud parallel finanzieren muss.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Hybrid Cloud]]
SORT file.mtime DESC
```