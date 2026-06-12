#Note

2026-06-12

Tags: [[Datenbanken]], [[Architektur]], [[Konsistenz]], [[ACID]], [[CAP-Theorem]]
#datenbanken 

---
Der Begriff **Konsistenz (Consistency)** beschreibt ganz allgemein den Zustand einer Datenbank zu einem bestimmten Zeitpunkt. Eine Datenbank gilt als konsistent, wenn sie sich in einem widerspruchsfreien Zustand befindet.

Die exakte Bedeutung dieses "widerspruchsfreien Zustands" unterscheidet sich jedoch radikal, je nachdem, ob wir ein lokales Relationales Datenbanksystem oder ein massiv Verteiltes Datenbanksystem betrachten.

1. Das relationale Gesicht: ACID-Konsistenz (Integrität)

Im klassischen ACID-Prinzip bezieht sich Konsistenz auf die **interne Korrektheit** der Daten gegenüber den vordefinierten Geschäftsregeln (Integritätsregeln).

- **Der Mechanismus:** Die Daten müssen nach jeder Änderung alle definierten Regeln (wie Datentypen, Wertebereiche, NOT NULL) erfüllen. Es muss die korrekte Beziehung zwischen Tabellen sichergestellt sein (referentielle Integrität, z.B. durch gültige Fremdschlüssel).
- **Die Transaktion:** Eine Transaktion überführt die Datenbank von einem gültigen, regelkonformen Zustand in den nächsten.
- **Konsistenz vs. Integrität:** Konsistenz ist der _Zustand_ der Daten (das Ergebnis); Integrität sind die _Regeln und Mechanismen_, um diesen Zustand überhaupt erst zu erzwingen. Eine Datenbank ist konsistent, _weil_ sie die Integritätsbedingungen erfüllt.

2. Das verteilte Gesicht: CAP-Konsistenz (Linearisierbarkeit)

Im Kontext von massiv verteilten NoSQL- und NewSQL-Systemen (das "C" im CAP-Theorem) ändert sich die Bedeutung. Hier geht es nicht primär um Fremdschlüssel, sondern um die **externe Übereinstimmung** aller Datenkopien (Replikate) im gesamten Netzwerk.

- **Der Mechanismus (Linearisierbarkeit):** Alle Knoten sehen zum exakt selben Zeitpunkt exakt dieselben Daten.
- **Die Garantie:** Jeder Lesevorgang (egal auf welchem Server-Knoten) liefert zwingend das Ergebnis des jüngsten Schreibvorgangs oder wirft einen Fehler.
- **Die Illusion:** Das System maskiert die Verteilung und verhält sich nach außen hin strikt so, als gäbe es nur eine einzige Datenkopie (Single System Image). Es gibt keine divergierenden Versionen und keine veralteten Replikate.

---

### Flashcards

Was ist der konzeptionelle Unterschied zwischen den Begriffen "Konsistenz" und "Integrität" in der Datenbankmodellierung?
?
**Konsistenz** ist der widerspruchsfreie Zustand der Daten zu einem bestimmten Zeitpunkt (das Ergebnis). **Integrität** bezeichnet die Regeln und Mechanismen (wie Constraints und Schlüssel), die beim Design der Datenbank festgelegt werden, um diesen konsistenten Zustand überhaupt erst zu sichern. Eine Datenbank ist konsistent, _weil_ sie die Integritätsbedingungen erfüllt.

Offizielle Prüfungsfrage: Unterscheiden Sie die Bedeutung des Begriffs „Consistency“ (Konsistenz) innerhalb des ACID-Prinzips von der Verwendung im CAP-Theorem. (Wiederholungsfrage 3)
?
**ACID-Konsistenz** bezieht sich auf die _Integrität_: Eine Transaktion überführt die Datenbank von einem gültigen Zustand in einen anderen gültigen Zustand unter strikter Einhaltung aller internen Geschäfts- und Integritätsregeln. **CAP-Konsistenz** bezieht sich auf die _Einheitlichkeit (Linearisierbarkeit)_: Jeder Lesevorgang in einem verteilten System liefert zwingend den Wert des jüngsten Schreibvorgangs. Alle Knoten im Netzwerk sehen gleichzeitig exakt dieselben Daten.

Was versteht man unter dem Begriff "Single System Image" im Rahmen der verteilten Konsistenz?::Es bedeutet, dass sich ein massiv verteiltes Datenbanksystem (mit Datenkopien auf hunderten Servern) nach außen hin für den Anwender so verhalten soll, als gäbe es nur eine einzige, sofort aktuelle Datenkopie auf einem lokalen Server.

Warum stellt die CAP-Konsistenz (Linearisierbarkeit) eine so gewaltige Herausforderung für globale Systeme dar, wenn Netzwerkausfälle auftreten?::Wenn ein Teil des Netzwerks ausfällt (Partition Tolerance), können die Replikate nicht mehr synchronisiert werden. Um die strikte CAP-Konsistenz (keine veralteten Daten) zu wahren, muss das System auf den isolierten Knoten gezwungenermaßen alle weiteren Anfragen ablehnen, wodurch die Verfügbarkeit (Availability) geopfert wird.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Konsistenz]]
SORT file.mtime DESC
```