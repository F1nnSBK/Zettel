#Note

2026-06-09

Tags: [[Datenbanksystem]], [[Relationale Datenbank]], [[Datenintegrität]]
#datenbanken

---
Der **Isolation Level** ist die wichtigste Konfigurationseinheit zur Steuerung der Concurrency (Nebenläufigkeit) in einer relationalen Datenbank.

Der Trade-off: Performance vs. Konsistenz

Um ein höheres Isolationslevel zu gewährleisten (und damit mehr Fehler auszuschließen), muss die Datenbank strengere Sperr- und Versionsmechanismen (Locking/Versioning) anwenden. Dies führt unweigerlich zu mehr Wartezeiten für andere Transaktionen und einem höheren System-Overhead.

- **Niedriges Level:** Maximiert die Parallelität (viele Transaktionen laufen gleichzeitig), lässt aber Anomalien zu.
- **Hohes Level:** Minimiert Fehler, bremst das System aber aus.

Die 4 Isolationsstufen nach SQL-Norm

Die SQL-Norm (SQL 2003) definiert vier Stufen. Wichtig: Der "Dirty Write" (Lost Update) ist in _allen_ Stufen ausnahmslos verboten.

|Isolation Level|Dirty Read|Non-Repeatable Read|Phantom|
|---|---|---|---|
|**READ UNCOMMITTED**|Erlaubt|Erlaubt|Erlaubt|
|**READ COMMITTED**|Verhindert|Erlaubt|Erlaubt|
|**REPEATABLE READ**|Verhindert|Verhindert|Erlaubt|
|**SERIALIZABLE**|Verhindert|Verhindert|Verhindert|
|_(Vgl. E. Schicker, Datenbanken und SQL, S.301 /__)_||||

Deep Dive in die Praxis: REPEATABLE READ

In der Isolationsstufe `READ COMMITTED` (dem Standard vieler Systeme) kann es passieren, dass man innerhalb derselben Transaktion zweimal denselben Datensatz liest und unterschiedliche Werte erhält, weil ein anderer Nutzer dazwischen ein `COMMIT` durchgeführt hat.

Wechselt man auf **REPEATABLE READ**, verhindert das System dies. Das Ziel ist es, dass eine Auswertung immer exakt das gleiche Ergebnis liefert.

- _Mechanismus:_ Wenn Transaktion A im Level `REPEATABLE READ` startet und Transaktion B nebenbei Daten ändert und mit `COMMIT` bestätigt, hat dies **keine Auswirkung** auf Transaktion A.
- _Sichtbarkeit:_ Transaktion A sieht die Änderungen von B erst dann, wenn Transaktion A selbst mit `COMMIT` beendet und danach eine neue Abfrage gestartet wird. Somit wird garantiert, dass Transaktion A immer mit einem in sich konsistenten Datenbestand arbeitet.

---

### Flashcards

Was ist der fundamentale Trade-off (Kompromiss) bei der Wahl eines Isolation Levels in einer relationalen Datenbank?::Die Wahl eines niedrigen Levels maximiert die Performance und Parallelität, lässt aber Datenanomalien zu. Die Wahl eines hohen Levels verhindert Anomalien, erfordert aber strenge Sperrmechanismen, die das System durch Wartezeiten und Overhead drastisch ausbremsen.

Welche vier Isolationsstufen definiert die SQL-Norm (SQL 2003)?::1. Read Uncommitted, 2. Read Committed, 3. Repeatable Read, 4. Serializable.

Welche der Nebenläufigkeitsanomalien wird selbst auf der niedrigsten und unsichersten Stufe (`READ UNCOMMITTED`) von der SQL-Norm strengstens verboten?::Der Dirty Write (das Problem der verlorengegangenen Änderung / Lost Update).

Welches spezifische Problem wird im Level `SERIALIZABLE` verhindert, das im Level `REPEATABLE READ` noch auftreten kann?
?
Im Level `SERIALIZABLE` werden **Phantome** verhindert. Phantome entstehen, wenn bei einer wiederholten Bereichsabfrage neue Zeilen auftauchen, die eine andere Transaktion in der Zwischenzeit eingefügt hat. Im `REPEATABLE READ` ist dies noch erlaubt.
<!--SR:!2026-06-10,0,230-->

Wie verhält sich eine Transaktion auf der Stufe `REPEATABLE READ`, wenn eine parallel laufende Transaktion in der Zwischenzeit einen Datensatz ändert und mit `COMMIT` bestätigt?::Die Änderung der parallelen Transaktion bleibt für die aktuelle Transaktion absolut unsichtbar. Selbst nach dem fremden `COMMIT` liefert ein erneuter Lesezugriff exakt den gleichen Wert wie zu Beginn, bis die eigene Transaktion beendet wird.

Wie sorgt das DBMS technisch dafür, dass höhere Isolationsstufen garantiert werden können?::Es wendet strengere Sperr- und Versionsmechanismen (Locking und Versioning) an, was Transaktionen zwingt, sich in Warteschlangen einzureihen.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Isolation Level]]
SORT file.mtime DESC
```