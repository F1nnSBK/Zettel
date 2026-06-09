#Note

2026-06-09

Tags: [[Datenbanksystem]], [[Relationale Datenbank]], [[Datenintegrität]], [[Daten]]
#datenbanken 

---
Das Transaktionsmanagement des DBMS ist die oberste Kontrollinstanz. Es muss Situationen bewältigen, in denen Millionen von Operationen gleichzeitig stattfinden ("concurrent update") oder das System plötzlich abstürzt.

1. Das ACID-Prinzip

Ein Transaktionssystem muss vier fundamentale Eigenschaften garantieren,,,:

1. **Atomicity (Atomarität):** Alles oder Nichts. Eine Transaktion wird entweder vollständig ausgeführt oder (bei einem Fehler) komplett per `ROLLBACK` zurückgerollt, als wäre sie nie passiert.
2. **Consistency (Konsistenz):** Die Datenbank befindet sich vor und nach der Transaktion in einem widerspruchsfreien Zustand. Alle definierten Regeln (z.B. referentielle Integrität, Datentypen) müssen erfüllt sein.
3. **Isolation:** Gleichzeitig ausgeführte Transaktionen dürfen sich nicht gegenseitig beeinflussen. Zwischenergebnisse einer Transaktion sind für andere unsichtbar, bis ein `COMMIT` erfolgt.
4. **Durability (Dauerhaftigkeit):** Wurde eine Transaktion mit `COMMIT` bestätigt, sind die Änderungen permanent und überleben selbst einen sofortigen Stromausfall (Sicherung über Log-Einträge).

5. Transaktionssteuerung in SQL

Standardmäßig arbeiten viele DBMS im **AUTO COMMIT**-Modus,. Das bedeutet, jeder einzelne `UPDATE`- oder `INSERT`-Befehl wird sofort unwiderruflich bestätigt. Um mehrere Befehle zu bündeln, muss Auto Commit deaktiviert und die Transaktion manuell gesteuert werden,:

- `START TRANSACTION;` (Öffnet die Klammer)
- `COMMIT;` (Schließt die Klammer erfolgreich, Daten werden dauerhaft gespeichert)
- `ROLLBACK;` (Bricht ab und verwirft alle Änderungen seit dem Transaktionsstart)

3. Nebenläufigkeitsanomalien (Concurrency-Probleme)

Wenn die _Isolation_ (das "I" in ACID) nicht strikt genug ist, können bei parallelen Zugriffen schwere Fehler entstehen,,:

- **Lost Update (Dirty Write):** Zwei Transaktionen ändern denselben Datensatz. Die zweite überschreibt das Ergebnis der ersten ungeprüft. _Die SQL-Norm verbietet dies absolut!_,,
- **Dirty Read:** Transaktion A liest Daten von Transaktion B, die B aber noch gar nicht mit `COMMIT` bestätigt hat (und vielleicht noch zurückrollt). A rechnet mit "schmutzigen" (ungültigen) Daten,.
- **Non-Repeatable Read:** Transaktion A liest einen Datensatz zweimal. Dazwischen ändert Transaktion B diesen Datensatz und committet. A bekommt beim zweiten Lesen plötzlich ein anderes Ergebnis,.
- **Phantom:** Transaktion A fragt eine Menge an Zeilen ab. Transaktion B fügt eine neue, passende Zeile hinzu und committet. Beim erneuten Lesen sieht A plötzlich eine "Geisterzeile" mehr,.

4. Isolation Levels (Der Kompromiss)

Man kann in SQL definieren, wie stark Transaktionen voneinander abgeschirmt werden,. Ein hohes Level (Serializable) verhindert alle Fehler, macht das System aber extrem langsam. Ein niedriges Level (Read Uncommitted) ist rasend schnell, lässt aber fast alle Anomalien zu.

|Isolation Level|Dirty Read|Non Repeatable Read|Phantom|
|---|---|---|---|
|**READ UNCOMMITTED**|Erlaubt|Erlaubt|Erlaubt|
|**READ COMMITTED**|Verhindert|Erlaubt|Erlaubt|
|**REPEATABLE READ**|Verhindert|Verhindert|Erlaubt|
|**SERIALIZABLE**|Verhindert|Verhindert|Verhindert|
|_(Anmerkung: "Dirty Write / Lost Update" ist in ALLEN Leveln verboten!)_||||

5. Lösungsstrategien & Deadlocks

Um Isolation technisch umzusetzen, gibt es zwei Paradigmen,:

1. **Pessimistische Synchronisation:** Geht von ständigen Konflikten aus. Setzt harte **Sperren (Locks)**, bevor Daten gelesen/geschrieben werden.
    - _Problem:_ Es kann zum **Deadlock (Verklemmung)** kommen. Transaktion 1 sperrt Datensatz A und wartet auf B; Transaktion 2 sperrt B und wartet auf A. Nichts geht mehr,.
2. **Optimistische Synchronisation:** Geht davon aus, dass Konflikte selten sind. Es wird ohne Sperren gearbeitet. Erst beim `COMMIT` wird validiert.
    - _Problem:_ Bei einem Konflikt muss eine Transaktion hart per `ROLLBACK` abgebrochen und neu gestartet werden,.

--------------------------------------------------------------------------------

### Flashcards

Was ist eine Transaktion im Kontext eines Datenbanksystems, und welche vier fundamentalen ACID-Eigenschaften muss jedes Transaktionssystem garantieren?
?
Eine Transaktion ist eine logische Einheit von Datenbankanweisungen, die die Datenbank von einem konsistenten Zustand in einen neuen konsistenten Zustand überführt. Die ACID-Eigenschaften sind: **Atomicity (Atomarität):** Vollständig ausgeführt oder gar nicht (Rollback bei Fehler),. **Consistency (Konsistenz):** Einhaltung aller definierten Regeln vor und nach der Transaktion. **Isolation:** Gleichzeitige Transaktionen beeinflussen sich nicht gegenseitig (Zwischenergebnisse sind unsichtbar). **Durability (Dauerhaftigkeit):** Änderungen sind nach dem Commit dauerhaft gespeichert (selbst bei Systemabstürzen).

Wie verhält sich ein Datenbanksystem im Auto-Commit-Modus und unter welchen Umständen muss dieser Mechanismus unterbunden werden?
?
Im Auto-Commit-Modus führt das DBMS nach jeder einzelnen INSERT-, UPDATE- oder DELETE-Anweisung automatisch ein COMMIT durch,. Dies muss deaktiviert werden, wenn mehrere Änderungen als eine zusammenhängende logische Einheit (Transaktion) betrachtet werden sollen.

Erklären Sie das "Lost Update" (Dirty Write) Problem. Warum nimmt es eine Sonderstellung bei den Nebenläufigkeitsanomalien ein?
?
Das Problem tritt auf, wenn zwei Transaktionen (TA1 und TA2) gleichzeitig denselben Datensatz lesen, modifizieren und nacheinander zurückschreiben. Die zweite Transaktion überschreibt das Ergebnis der ersten ungeprüft, der Update der ersten geht verloren. Es nimmt eine Sonderstellung ein, da es von der SQL-Norm in **allen** Isolation Leveln grundsätzlich verboten ist,.

Erklären Sie die drei wichtigsten Concurrency-Probleme (neben Lost Update), die bei unzureichender Isolation auftreten können.
?
**Dirty Read:** Transaktion A liest Daten, die von Transaktion B geändert, aber noch nicht (oder nie) committet wurden. **Non Repeatable Read:** Transaktion A liest einen Datensatz zweimal. Beim zweiten Mal ist das Ergebnis anders, da Transaktion B ihn dazwischen geändert und committet hat. **Phantom:** Transaktion A wiederholt eine Bereichsabfrage und plötzlich tauchen neue Zeilen auf, die Transaktion B in der Zwischenzeit eingefügt und committet hat.

Welches spezifische Problem wird im Level SERIALIZABLE verhindert, das im Level REPEATABLE READ noch auftreten kann?::Im Level SERIALIZABLE werden Phantome verhindert, was im Level REPEATABLE READ noch erlaubt ist,.

Beschreiben Sie die grundlegenden Unterschiede zwischen der Pessimistischen und der Optimistischen Concurrency-Strategie hinsichtlich ihrer Konflikthandhabung.
?
**Pessimistisch:** Geht von häufigen Konflikten aus. Verwendet harte Sperren (Locks), bevor gelesen oder geschrieben wird,. Nachteil: Führt zu Wartezeiten und möglichen Deadlocks. **Optimistisch:** Geht von seltenen Konflikten aus und arbeitet ohne Sperren. Die Konfliktprüfung erfolgt erst am Ende bei der Validierung,. Nachteil: Bei Konflikten muss die Transaktion komplett zurückgerollt (ROLLBACK) und neu gestartet werden.

Was versteht man unter einem Deadlock (Verklemmung) und wie entsteht dieser Zustand?::Ein Deadlock ist eine wechselseitige Blockierung. Er entsteht, wenn mehrere Transaktionen auf die Freigabe von Ressourcen warten, die jeweils von der anderen Transaktion gehalten werden (z.B. Transaktion 1 sperrt Datensatz A und wartet auf B; Transaktion 2 sperrt B und wartet auf A).

Was ist der Unterschied zwischen dem Zweiphasen-Sperrprotokoll (2PL) und dem Zweiphasen-Commit-Protokoll (2PC) in Bezug auf die ACID-Kriterien?
?
**2PL (Two-Phase Locking):** Setzt die **Isolation (I)** um und garantiert die Serialisierbarkeit von Transaktionen durch Sperrphasen,. **2PC (Two-Phase Commit):** Setzt die **Atomarität (A)** in verteilten Systemen um und koordiniert den gemeinsamen Abschluss (Commit/Abort) über mehrere Server-Knoten hinweg,.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Transaktion]]
SORT file.mtime DESC
```