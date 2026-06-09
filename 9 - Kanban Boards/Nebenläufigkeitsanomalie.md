#Note

2026-06-09

Tags: [[Datenbanksystem]], [[Relationale Datenbank]], [[Datenintegrität]]
#datenbanken 

---
**Nebenläufigkeitsanomalien (Concurrency-Probleme)** sind direkte Verletzungen der Isolation. Sie treten auf, wenn Millionen von Nutzern, Systemen oder Prozessen gleichzeitig auf denselben Datenbestand zugreifen ("concurrent update") und das Datenbankmanagementsystem (DBMS) diese Zugriffe nicht strikt genug voneinander abschirmt.

Die SQL-Norm (SQL 2003) definiert exakt vier Arten von Anomalien, die beim Datenbankentwurf berücksichtigt werden müssen:

1. Dirty Write (Verlorengegangene Änderung / Lost Update)

Dieses Problem nimmt eine **Sonderstellung** ein, da es vom SQL-Standard in _allen_ Isolationsstufen absolut verboten ist und vom DBMS zwingend verhindert werden muss.

- **Das Problem:** Zwei Transaktionen (TA1 und TA2) lesen gleichzeitig denselben Datensatz, modifizieren ihn und schreiben ihn anschließend nacheinander zurück.
- **Der Fehler:** Da die zweite Transaktion das Ergebnis der ersten ohne erneute Prüfung einfach überschreibt, geht das Update der ersten Transaktion komplett verloren.

2. Dirty Read (Lesen "schmutziger" Daten)

Problem der Abhängigkeit von noch nicht abgeschlossenen Transaktionen.

- **Das Problem:** Transaktion A liest Daten, die von einer parallel laufenden Transaktion B geändert, aber noch nicht durch `COMMIT` dauerhaft festgeschrieben wurden.
- **Der Fehler:** Sollte Transaktion B diese Änderung später durch ein `ROLLBACK` wieder zurücknehmen (verwerfen), hat Transaktion A mit völlig ungültigen Daten gearbeitet, die so in der Datenbank nie offiziell existiert haben. Dies führt zu massiven Inkonsistenzen in der Anwendungslogik.

3. Non-Repeatable Read (Nicht wiederholbares Lesen)

Dieses Problem betrifft die Integrität von Daten innerhalb _einer einzigen_ Transaktion.

- **Das Problem:** Transaktion A liest einen spezifischen Datensatz. Bevor Transaktion A beendet ist, ändert eine andere Transaktion B genau diesen Datensatz und schließt mit `COMMIT` ab.
- **Der Fehler:** Führt Transaktion A nun einen wiederholten Lesezugriff auf denselben Inhalt durch, erhält sie plötzlich ein völlig anderes Ergebnis als beim ersten Mal. Die Ergebnisse sind nicht stabil (non-repeatable).

4. Phantom (Phantomproblem)

Während der "Non-Repeatable Read" existierende Zeilen betrifft, geht es beim Phantom um _neue_ oder gelöschte Zeilen.

- **Das Problem:** Transaktion A führt eine Abfrage aus, die auf einer Menge von Zeilen basiert (z.B. eine Bereichsabfrage `WHERE alter > 30` oder ein `SELECT COUNT(*)`). Währenddessen fügt Transaktion B neue Zeilen ein, die genau auf dieses Kriterium passen, und committet.
- **Der Fehler:** Wenn Transaktion A die identische Abfrage wiederholt, tauchen plötzlich neue "Geisterzeilen" (Phantome) auf, die beim vorherigen Lesen noch nicht vorhanden waren.

**Die Lösung:** Um diese vier Nebenläufigkeitsanomalien zu kontrollieren, muss man den [[Isolation Level]] der Datenbank konfigurieren. Das höchste Level (`SERIALIZABLE`) verhindert alle vier Anomalien, reduziert aber durch harte Sperren (Locks) die Parallelität und Performance drastisch.

--------------------------------------------------------------------------------

### Flashcards

Beschreiben Sie das „Problem der verlorengegangenen Änderung“ (Lost Update / Dirty Write) und warum es bei den Anomalien eine Sonderstellung einnimmt.
?
Ein Lost Update tritt auf, wenn zwei Transaktionen gleichzeitig denselben Datensatz lesen, ihn modifizieren und anschließend nacheinander zurückschreiben. Die zweite Transaktion überschreibt das Ergebnis der ersten ungeprüft, wodurch das erste Update unwiderruflich verloren geht. Es nimmt eine Sonderstellung ein, da es laut SQL-Norm in **allen** Isolation Leveln grundsätzlich streng verboten ist.

Was versteht man unter einem "Dirty Read" (Lesen schmutziger Daten)?
?
Ein Dirty Read beschreibt die Abhängigkeit von noch nicht abgeschlossenen Transaktionen. Transaktion A liest Daten, die von Transaktion B geändert, aber noch nicht durch `COMMIT` festgeschrieben wurden. Wenn Transaktion B anschließend ein `ROLLBACK` ausführt, hat Transaktion A mit ungültigen Daten gearbeitet, die in der Datenbank offiziell nie existiert haben.

Erklären Sie den genauen Unterschied zwischen einem "Non Repeatable Read" und dem "Phantomproblem".
?
Beide Anomalien treten auf, wenn sich Daten zwischen zwei Lesevorgängen derselben Transaktion ändern, weil eine andere Transaktion in der Zwischenzeit ein `COMMIT` durchgeführt hat. **Non Repeatable Read:** Betrifft das Verändern eines _existierenden_ Datensatzes. Der Wert der Zeile hat sich geändert. **Phantom:** Betrifft Bereichsabfragen. Es tauchen völlig _neue Zeilen_ auf (Phantome), die von der anderen Transaktion neu eingefügt wurden.

Welches spezifische Problem wird im Isolations-Level `SERIALIZABLE` verhindert, das im Level `REPEATABLE READ` noch auftreten kann?::Im Level `SERIALIZABLE` werden **Phantome** (das Auftauchen neuer Zeilen bei wiederholten Abfragen) verhindert, was im Level `REPEATABLE READ` noch explizit erlaubt ist.

Warum wählt man in der Praxis für Datenbanken nicht immer pauschal das sicherste Isolations-Level (`SERIALIZABLE`), um alle Nebenläufigkeitsanomalien auszuschließen?::Weil das Verhindern aller Anomalien (besonders von Phantomen) strengste Sperrmechanismen erfordert, die zu massiven Wartezeiten führen. Ein hohes Isolations-Level minimiert zwar die Fehler, reduziert aber die allgemeine Parallelität und Performance des Systems erheblich.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Nebenläufigkeitsanomalie]]
SORT file.mtime DESC
```