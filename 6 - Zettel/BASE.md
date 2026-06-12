#Note

2026-06-12

Tags: [[Datenbanken]], [[Verteilte Systeme]], [[BASE]], [[NoSQL]], [[CAP-Theorem]]
#datenbanken 

---
Das **BASE-Modell** ist das fundamentale Konsistenzmodell für moderne NoSQL-Datenbanken. Da globale Webanwendungen (Web 2.0 / Big Data) Millionen von Nutzern gleichzeitig bedienen müssen, ist eine ständige Verfügbarkeit oft viel kritischer als die absolute, sofortige Wahrheit (Konsistenz).

Das Akronym **BASE** steht für drei Kernkonzepte:

1. **B**asically **A**vailable (Grundsätzliche Verfügbarkeit): Das System garantiert eine grundlegende Verfügbarkeit und antwortet auf Anfragen selbst dann, wenn es zu Teilausfällen im Cluster oder Netzwerkpartitionen kommt.
2. **S**oft State (Weicher/Fließender Zustand): Im Gegensatz zur strengen ACID-Regeltreue akzeptiert das System, dass sich Daten zeitweilig in einem inkonsistenten Übergangszustand befinden. Replikate auf verschiedenen Servern dürfen zwischenzeitlich unterschiedliche Versionen desselben Datensatzes halten.
3. **E**ventually Consistent (Verzögerte Konsistenz): Schreibaktionen werden nicht sofort synchron auf alle Knoten gezwungen. Das System sichert lediglich zu: Wenn keine neuen Schreibvorgänge mehr stattfinden, werden alle Aktualisierungen nach und nach im Knotennetz verteilt, bis das System nach einer gewissen Zeit _irgendwann_ von selbst wieder einen durchgehend konsistenten Zustand erreicht.

Der direkte Vergleich: ACID vs. BASE

|Merkmal|ACID (Klassisch Relational)|BASE (Modern NoSQL)|
|---|---|---|
|**Konsistenz**|Hat oberste Priorität. Strikte Konsistenz sofort nach der Transaktion (strong consistency).|Wird verzögert etabliert (weak/eventual consistency).|
|**Synchronisation**|Meist pessimistische Sperrprotokolle (Locks).|Meist optimistische Synchronisationsverfahren (Konfliktauflösung im Nachhinein).|
|**Fokus**|Verfügbarkeit bei überschaubaren Datenmengen.|Hohe Verfügbarkeit und Ausfalltoleranz bei massiv verteilter Datenhaltung.|
|**Struktur**|Integritätsregeln im Schema (z. B. Fremdschlüssel) erzwungen.|Schemafreiheit, kein explizites Schema.|

---

### Flashcards

Wofür steht das Akronym BASE im Kontext verteilter Datenbanksysteme?::Es steht für **B**asically **A**vailable, **S**oft state, **E**ventually consistent.

Offizielle Prüfungsfrage (9): Vergleichen Sie das ACID-Prinzip mit dem BASE-Modell hinsichtlich der Konsistenzgarantien.
?
**ACID** garantiert eine sofortige, strikte Konsistenz (Strong Consistency) direkt nach dem Abschluss jeder einzelnen Transaktion. **BASE** akzeptiert hingegen einen vorübergehend inkonsistenten Zustand (den sogenannten „Soft State“), um eine höhere Verfügbarkeit und massive Skalierbarkeit zu erreichen. Die Konsistenz wird hier erst verzögert etabliert (Weak Consistency).

Offizielle Prüfungsfrage (10): Was versteht man unter „Eventual Consistency“ (verzögerte Konsistenz) in verteilten Systemen?
?
Das System garantiert nicht die sofortige Sichtbarkeit eines Schreibvorgangs auf allen Server-Knoten gleichzeitig. Es wird lediglich garantiert, dass bei Ausbleiben neuer Updates die Aktualisierungen nach und nach verteilt werden und _irgendwann_ („eventually“) alle Kopien im Netzwerk denselben Wert aufweisen.

Wie unterscheiden sich ACID und BASE in Bezug auf ihre Synchronisationsstrategien bei gleichzeitigen Datenzugriffen?::ACID verwendet in der Regel **pessimistische Synchronisationsverfahren** mit strengen Sperrprotokollen (Locks), um Konflikte im Vorfeld zu vermeiden. BASE nutzt meist **optimistische Synchronisationsverfahren** und löst Konflikte (z.B. durch Differenzierungsoptionen) erst im Nachhinein auf.

Erklären Sie den Begriff "Soft State" im BASE-Modell.::Er beschreibt, dass sich Daten in einem verteilten System zeitweilig in einem fließenden, inkonsistenten Übergangszustand befinden dürfen, in dem die Replikate noch nicht vollständig synchronisiert sind.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[BASE]]
SORT file.mtime DESC
```