
Nennen stets exakt nach den Begriffen in den Folien. Beispiel: Globale Verfügbarkt falsch als Vorteil bei Cloud Computing, stattdessen: Globale Verteilung
NOTE: Bei Cloud Computing Klausur ist genau lesen ganz wichtig.

Grundlagen (Herausforderungen anschauen)
Bei 2 Vorlesungsfolien anschauen und ie Übungsaufgaben genau anschauen, mit den besprochenen Lösungen
Bei 3 ist die Probeklausur repräsentativ Docker code schreiben/optimieren profile Umgebungsvariablen, Spring Boot code profile variablen optimieren



1
a) Server Festungen sind eine Ansammlung von vielen lokalen On Premise Servern, bei denen der Überblick über Konfiguration/Auslastung verloren geht. Das entsteht zb durch händisch angepasste Konfigurationen, die undokumentierte Zustände erzeugen. Deshalb unternimmt die IT alles um ein Neustart der betreffenden Server zu vermeiden.

b) Beim traditionellen On Premise Betrieb wird viel Kapital gebunden, da zuerst einiges investiert werden muss. Dadurch entsteht ein höherer Planungsaufwand, was wiederum dazu führt, dass Dev/Prod Umgebungen eingerichtet werden anstatt von Trial & Error versuchen. Man verhindert leichtsinnige aber in der Summe teure Softwareexperimente.

c) 
1. In der Cloud kann flexibel nach der Auslastung skaliert werden. Beispielsweise kann über horizontale Skalierung eine weitere Instanz bei Lastspitzen hochgefahren werden. Hier greift die Fixkostendegression.
2. Die großen Cloud Anbieter betreiben großen Aufwand im Bereich IT-Security, wodurch man als Kunde entlastet wird.
3. Cloud Computing ist flexbiler in der Planung. Es muss nicht anfang viel Kapital gebunden werden, wodurch Hürden für Projekte sinken.
4. Die Konfiguration in der Cloud ist wesentlich einfacher, da alles über ein User Interface gesteuert werden kann. Bei On Premise Lösungen wird ein ganzen Team nur für den Betrieb benötigt.

d)
	1. Kostenmanagement: Da die Hardware nicht physisch im eigenen Haus steht, ist es einfach, den Bezug zu den Kosten zu verlieren. Man muss aktiv Kostenmanagement/-tracking betreiben. Es könnte sonst dazu kommen, dass mehr ausgegeben wird als zur Verfügung steht, da die Cloud Anbieter theoretisch unbregenzt skalieren.
	2. Keine zentrale IT-Governance: Es braucht klare Regeln wie Ressourcen konfiguriert werden, weil sonst schnell der Überblick von Cloud Ressourcen verloren geht. Zb durch fehlende Naming Conventions
	3. Fehlendes Know How: Die Mitarbeiter müssen erst für den Umgang mit Cloud Computing geschult werden, weil sonst Fehlkonfigurationen oder teure Fehler entstehen können. Zb wenn man eine VM unebnutzt laufen lässt.

e) 

Continuous Integration beschreibt die automatische Durchführung statischer Codeanalyse, Buildskripte, sowie Unit-, Integration- und Systemtests.
Continuous Delivery beschreibt die automatisierte Auslieferung von Software die für das Deployment vorbereitet ist und es baut auf CI auf.
Continuous Deployment ist die automatisierte Inbetriebnahme von aktualisierten Softwareprodukten

f)

Mutable Infrastructure meint die Veränderlichkeit von Software. Es bedeutet, dass Software nach der Inbetriebnahme durch manuelle Änderungen angepasst wird. Traditionelle Vorgehensweise und es ist oft nicht dokumentiert.

2 a) + b)
Anwendung -> SaaS, FaaS
Funktion -> PaaS
Laufzeit
Container -> CaaS
Betriebssystem -> IaaS
Hypervisor
Hardware 

c)
Durch den modularen Aufbau können die unterschiedlichen Schichten bei einem Wartungfall einfach ausgetauscht werden. Klare Aufgabenteilung zwischen Cloud-Nutzer und Cloud-Provider, Trade-off ziwschen Abstraktion und Kontrolle. Gemeinsamkeiten einheitlich Patchen.

d) 
Die Analogie passt zum Container-as-a-Service Modell, die Auswahl deds konkreten Containers/Autos liegt bei einem selbst und sie selbst bedient/verwaltet. Es wird nicht die reine Funktion gemietet (vgl Taxi). Die Infrastruktur geht nicht in da Eigentum über.

e)
+- Nutzung der vorhandenen Infrastruktur
+- Kosteneffizienz der On Premise Infrastruktur wird gesteigert, da die Cloud-Komponente die Funktionalität erweitert
-- Erhöhter Verwaltungsaufwand
-- Hohe Gesamtkosten
-- Konsistenz 

f)
Bei Edge Computing geht es darum, die Datenverarbeitung und der Ort der Datenerhebung so nah wie möglich zusammenzubringen, wodurch eine effizientere Datenverarbeitung erfolgt. Bei einer Private Cloud geht es weniger um Effizienz und Performance, sondern um Sicherheit und Verarbeitung vertraulicher Daten, die zu sensibel für das Internet sind.

EC hat einen spzeifischen Anwendungsfall (zb Defekterkennung) wäährend PC einen universellen Anwedungsfall hat.



3
a)
1. `FROM javaee/springdemo:latest`
2. `ENV Spring.profiles.active=prod`
3. `RUN mkdir app/`
4. `WORKDIR app/`
5. `COPY . .`
6. `EXPOSE 8080`
7. `CMD ["java", "-jar", "app.jar"]`

b) 
3 Der Ordner app/ muss nicht explizit erstellt werden, der WORKDIR Befehl erstellt ihn automatisch, wenn es ihn noch nicht gibt.
5 I.d.R müssen nie alle Dateien in den Container kopiert werden, eine gezielte Auswahl hier kann helfen, den Container schlank zu halten. Das heißt er hat nur die Dateien, die er zwingend benötigt.
1 `latest` ist eine potenzielle Sicherheitslücke 
1 Offizielles Image verwenden
Vor Zeile 2 nicht priviligierten Use anlegen und auf diesen wechseln

c)
Zeile 2 in `RestController`: Die `CustomerRestControllerImpl` ist für das Profil `dev` aktiv, im Docker Container in Zeile 2 setzen wird aber `Spring.profiles.active=prod`. Das heißt, die Implementation steht uns im `prod` Profil nicht zur Verfügung.

d)
Variable in Dockerfile zB zwischen Zeile 2 & 3 setzen:
`specialNames=Check,Siri,CoolAid`
Direkt über Zeile 4 in Spring Boot nutzen wir eine Value Injection mit `@Value` um unsere Umgebungsvariable auszulesen:
`@Value("${specialNames}")`

e)
`docker image build -t exam:1 .`

f)
`docker image history exam:1`

g)
Wenn wir ein neues Image bauen mit dem gleichen Tag, wird das Image mit diesem Tag `exam:1` in der aktuellen Docker Registry nicht überschrieben und es wird mit dem alten Image weitergearbeitet. Bzw. hat man jetzt 2 Container mit dem gleichen Tag aber unterschiedliche Versionen mit eben unterschiedlichen Hashes. Das konkrete Problem heißt Version Hell. Man löst das Problem durch eine eindeutige Versionierung.

Fettes Problem mit Autoscaling


h)
Man kann die BuildId oder Datum verwenden um Unique Tags zu erzeugen. Die BuildId ist dabei absolut Unique, beim Datum muss beachtet werden, nicht mehr als 1 Basisimage pro Tag zu pushen, sonst müsste man mit den Timestamps ggf. arbeiten.


i)
Jeder Container hat eine beschreibbare Schicht, die zur Laufzeit des Containers erstellt wird und nach der Laufzeit auch wieder gelöscht. Das Dateisystem im Container ist `read-only` wenn eine Datei verändert wird, wird diese zuerst in die beschreibbare Schicht kopiert und ort verändert.
