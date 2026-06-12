#Note

2026-06-12

Tags: [[Datenbanken]], [[Architektur]], [[Verteilte Systeme]], [[CAP-Theorem]], [[BASE]]
#datenbanken 

---
Ein **Verteiltes Datenbanksystem** speichert Daten nicht mehr auf einem einzelnen Server, sondern verteilt sie auf mehrere Rechner (Nodes) in einem Netzwerk. Das Ziel: Bessere Skalierbarkeit, höhere Ausfallsicherheit und Lastenverteilung.

Das Distributed Data Management System (DDBMS) sorgt dabei für die **Verteilungstransparenz**: Der Anwender interagiert mit der Datenbank, ohne zu wissen, auf welchem Kontinent sein Datensatz gerade liegt.

1. Datenverteilung: Wie kommen die Daten auf die Server?

Es gibt zwei grundlegende Mechanismen, um Daten im Cluster anzuordnen:

- **Fragmentierung (Aufteilung):**
    - _Horizontal:_ Die Tabelle wird zeilenweise aufgeteilt (Kunden A-M auf Server 1, Kunden N-Z auf Server 2). Dies ist der häufigste Fall.
    - _Vertikal:_ Die Tabelle wird spaltenweise aufgeteilt. Wichtig: Der Primärschlüssel muss in jedem Fragment redundant vorhanden sein, damit man die Zeile später wieder zusammensetzen kann.
    - _Sharding:_ Ist die physische Verteilung dieser horizontalen Fragmente auf verschiedene Knoten.
- **Replikation (Spiegelung):** Daten werden redundant auf mehrere Server kopiert, um die Ausfallsicherheit und die Leseperformance zu erhöhen.

2. Das CAP-Theorem (Die physikalische Grenze)

Bei massiv verteilten Systemen stößt das klassische ACID-Prinzip an seine Grenzen. Das CAP-Theorem besagt, dass ein verteiltes System nur maximal zwei der folgenden drei Eigenschaften gleichzeitig garantieren kann:

- **C (Consistency - Konsistenz):** Alle Knoten sehen zum exakt selben Zeitpunkt exakt dieselben Daten. Jeder Lesevorgang liefert den Wert des jüngsten Schreibvorgangs.
- **A (Availability - Verfügbarkeit):** Das System beantwortet jede Anfrage, auch wenn Knoten ausfallen.
- **P (Partition Tolerance - Ausfalltoleranz):** Das System funktioniert weiter, auch wenn das Netzwerk zwischen den Server-Knoten reißt.

**Der Konflikt:** Da Netzwerkausfälle (P) in globalen Systemen unumgänglich sind, muss man sich im Fehlerfall zwingend zwischen **C** und **A** entscheiden. Entscheidet man sich für die Verfügbarkeit (A), riskiert man, dem User veraltete Daten zu liefern (man opfert C).

3. Das BASE-Modell (Die neue Realität)

Um massiv zu skalieren, nutzen viele moderne (NoSQL-)Datenbanken das BASE-Modell als direkten Gegenentwurf zu ACID:

- **B**asically **A**vailable: Das System garantiert grundlegende Verfügbarkeit, selbst bei Teilausfällen.
- **S**oft State: Das System akzeptiert, dass sich Daten zeitweilig in einem inkonsistenten Übergangszustand befinden.
- **E**ventually Consistent (Verzögerte Konsistenz): Das System sichert lediglich zu, dass irgendwann alle Kopien denselben Wert aufweisen, wenn keine neuen Schreibvorgänge mehr stattfinden.

---

### Flashcards

Wann gilt eine Datenbank als verteilte Datenbank?
?
Eine verteilte Datenbank besteht aus einer logisch zusammengehörigen Datenbank (einem einzigen logischen Datenbankschema), deren Daten jedoch physisch in Fragmente zerlegt und auf mehrere, über ein Netzwerk verbundene Rechner (Nodes) verteilt sind.

Erklären Sie den Unterschied zwischen horizontaler und vertikaler Fragmentierung.
?
**Horizontal:** Die Tabelle wird nach Zeilen (Datensätzen) aufgeteilt. **Vertikal:** Die Tabelle wird nach Spalten (Attributen) aufgeteilt. Dabei ist zwingend erforderlich, dass der Primärschlüssel in jedem vertikalen Fragment vorhanden ist, um die Datenrelation wiederherstellen zu können.

Unterscheiden Sie die Bedeutung des Begriffs „Consistency“ (Konsistenz) innerhalb des ACID-Prinzips von der Verwendung im CAP-Theorem.
?
Die **ACID-Konsistenz** bezieht sich auf die _Integrität_: Eine Transaktion überführt die Datenbank unter Einhaltung aller definierten Geschäftsregeln (z.B. referenzielle Integrität) von einem gültigen Zustand in den nächsten. Die **CAP-Konsistenz** bezieht sich auf die _Einheitlichkeit (Linearisierbarkeit)_: Alle Knoten sehen gleichzeitig dieselben Daten, und jeder Lesevorgang liefert zwingend den Wert des jüngsten Schreibvorgangs.

Benennen und beschreiben Sie kurz die drei Komponenten des CAP-Theorems.
?
1. **Consistency (C):** Alle Knoten sehen gleichzeitig dieselben Daten (jeder Lesevorgang liefert das jüngste Update).
2. **Availability (A):** Jede Anfrage an das System wird beantwortet (auch bei Ausfall einzelner Knoten).
3. **Partition Tolerance (P):** Das System funktioniert weiterhin, auch wenn das Netzwerk zwischen den Knoten unterbrochen ist (Netzwerkpartitionierung).

Warum kann ein verteiltes System im Falle einer Netzwerkpartitionierung nicht gleichzeitig konsistent (C) und verfügbar (A) sein? Welche Auswirkung hat die Wahl von "A"?
?
Wenn das Netzwerk getrennt ist (P), können die Knoten nicht mehr miteinander kommunizieren, um Daten zu synchronisieren. Will das System konsistent bleiben (C), muss es Anfragen ablehnen, bis die Netzverbindung wieder steht (es verliert A). Will das System hochverfügbar bleiben (A), muss es Anfragen beantworten, riskiert dabei aber zwangsläufig, veraltete oder inkonsistente Daten auszuliefern (es verliert C).

Vergleichen Sie das ACID-Prinzip mit dem BASE-Modell hinsichtlich der Konsistenzgarantien.
?
**ACID** garantiert eine sofortige, strikte Konsistenz direkt nach Abschluss jeder einzelnen Transaktion. **BASE** akzeptiert einen vorübergehend inkonsistenten Übergangszustand ("Soft State"), um eine höhere Verfügbarkeit und massive Skalierbarkeit zu erreichen. Die Konsistenz wird hier erst verzögert etabliert ("weak consistency").

Was versteht man unter „Eventual Consistency“ (verzögerte Konsistenz) in verteilten Systemen?
?
Es bedeutet, dass Schreibaktionen nicht unmittelbar auf allen Knoten gleichzeitig durchgeführt werden müssen. Das System garantiert lediglich, dass bei Ausbleiben neuer Updates _irgendwann_ ("eventually") alle Replikate im Knotennetz denselben Wert aufweisen und konsistent sind.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Verteilte Datenbank]]
SORT file.mtime DESC
```