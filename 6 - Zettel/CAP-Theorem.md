#Note

2026-06-12

Tags: [[Konsistenz]], [[Datenbanken]], [[Verteilte Systeme]], [[CAP-Theorem]], [[Architektur]], [[Big Data]]
#datenbanken 

---
Das **CAP-Theorem** definiert die absoluten physikalischen Schranken für verteilte Datenbanken. Im Jahr 2000 stellte Eric Brewer (Universität Berkeley) die Vermutung auf, dass drei spezifische Eigenschaften in massiv verteilten Rechnersystemen nicht gleichzeitig gelten können. Diese Vermutung wurde später von Wissenschaftlern des MIT mathematisch bewiesen und als Theorem etabliert.

Die 3 Eigenschaften (Das CAP-Dreieck)

1. **C (Consistency - Konsistenz):** Alle Knoten sehen gleichzeitig exakt dieselben Daten. Jeder Lesevorgang liefert zwingend das Ergebnis des jüngsten Schreibvorgangs (Linearisierbarkeit).
2. **A (Availability - Verfügbarkeit):** Alle Anfragen an das System werden stets beantwortet, auch bei Ausfall einzelner Knoten.
3. **P (Partition Tolerance - Ausfalltoleranz):** Das System arbeitet auch dann weiter, wenn Knoten nicht mehr miteinander kommunizieren können (z.B. durch eine Netzwerktrennung).

Der physikalische Konflikt (Die Entscheidung)

Da es in der Praxis unmöglich ist, ein Netzwerk aufzubauen, das niemals ausfällt, muss man die Ausfalltoleranz (P) in verteilten Systemen als gegeben annehmen. Gemäß dem CAP-Theorem müssen Systeme also im Falle eines Fehlers zwischen strikter Konsistenz (C) und hoher Verfügbarkeit (A) wählen.

- **Szenario:** Ein Cluster besteht aus Node 1 und Node 2. Die Netzwerkleitung dazwischen reißt ab (Partitionierung). Ein Nutzer ändert sein Passwort auf Node 1. Was macht das System, wenn nun eine Anfrage auf Node 2 nach dem Passwort fragt?
    - **Entscheidung für Konsistenz (CP):** Node 2 muss die Antwort verweigern (Fehlermeldung), da er weiß, dass er nicht mit Node 1 abgleichen kann, ob sein Wert noch aktuell ist. _Verfügbarkeit wird geopfert._
    - **Entscheidung für Verfügbarkeit (AP):** Node 2 liefert sofort das alte, ihm bekannte Passwort aus. Der Nutzer erhält eine Antwort, aber sie ist falsch. _Konsistenz wird geopfert._

**Die Konsequenz für moderne Web-Architekturen:** Für globale Webanwendungen ist Verfügbarkeit (A) oft viel kritischer als sofortige Konsistenz (C). Nutzer erwarten eine sofortige Antwort, auch wenn Daten eines Knotens noch nicht final aktualisiert sind. Dies führt zum Aufstieg von NoSQL-Datenbanken und dem [[BASE]].

---

### Flashcards

Unterscheiden Sie die Bedeutung des Begriffs „Consistency“ (Konsistenz) innerhalb des ACID-Prinzips von der Verwendung im CAP-Theorem.
?
[[ACID]]-Konsistenz bezieht sich auf die **Integrität**: Eine Transaktion überführt die Datenbank von einem gültigen Zustand in einen anderen gültigen Zustand unter Einhaltung aller definierten Regeln. CAP-Konsistenz bezieht sich auf die **Einheitlichkeit (Linearisierbarkeit)**: Alle Knoten sehen gleichzeitig dieselben Daten, und jeder Lesevorgang liefert zwingend den Wert des jüngsten Schreibvorgangs.

Benennen und beschreiben Sie kurz die drei Komponenten des CAP-Theorems.
?
1. **Consistency (C):** Alle Knoten sehen gleichzeitig dieselben Daten.
2. **Availability (A):** Jede Anfrage an das System wird beantwortet.
3. **Partition Tolerance (P):** Das System funktioniert trotz Netzwerkausfällen weiter.

Warum kann ein verteiltes System im Falle einer Netzwerkpartitionierung nicht gleichzeitig konsistent (C) und verfügbar (A) sein?
?
Bei einer Netzwerktrennung (P) können Knoten nicht miteinander kommunizieren und sich synchronisieren. Will man die Konsistenz (C) wahren, muss man Anfragen ablehnen (kein A), bis die Daten wieder synchron sind. Will man hochverfügbar bleiben (A), riskiert man zwangsläufig, veraltete oder unterschiedliche Daten auszuliefern (kein C).

Konsistenz im Partitionierungsfall: Ein verteiltes System entscheidet sich bei einer Netzwerkpartitionierung (P) für Verfügbarkeit (A). Welche Auswirkung hat dies auf die CAP-Konsistenz der gelesenen Daten?
?
Wenn sich ein System für Verfügbarkeit (A) entscheidet, wird die strikte Konsistenz aufgegeben. Das System liefert dem Benutzer möglicherweise einen veralteten oder inkonsistenten Datenstand aus, da die Replikation (der Datenabgleich) zwischen den getrennten Knoten zu diesem Zeitpunkt nicht garantiert werden kann.



---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[CAP-Theorem]]
SORT file.mtime DESC
```