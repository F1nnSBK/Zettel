#Note

2026-06-12

Tags: [[Datenbanken]], [[Transaktionen]], [[Sperrverfahren]], [[Locks]], [[Concurrency]]
#datenbanken

---
Um Nebenläufigkeitsanomalien (wie Lost Updates oder Phantome) zu verhindern und die Grundregel der Concurrency abzusichern, müssen Datenbanken den parallelen Zugriff synchronisieren. Das Ziel dieser Synchronisation ist die **Serialisierung**: Das Endergebnis mehrerer gleichzeitig ausgeführter Transaktionen muss exakt so aussehen, als wären die Transaktionen brav nacheinander (seriell) abgelaufen.

Hierfür gibt es zwei architektonische Hauptstrategien:

1. Pessimistische Synchronisation (Der Standard)

- **Grundannahme:** Das System geht davon aus, dass Konflikte _ständig_ auftreten.
- **Strategie (Locks):** Es werden harte Sperren (Locks) gesetzt, _bevor_ Daten gelesen oder geschrieben werden. Zu jeder Relation existiert ein Lock. Möchte eine Transaktion auf eine Tabelle zugreifen, holt sie sich den Lock. Ist dieser bereits belegt, muss die Transaktion in einer Warteschlange warten.
- **Vorteil / Nachteil:** Es ist extrem sicher und verhindert Konflikte zuverlässig. Der große Nachteil sind blockierende Wartezeiten und die Gefahr von Deadlocks.

2. Optimistische Synchronisation

- **Grundannahme:** Das System geht davon aus, dass Konflikte _selten_ auftreten.
- **Strategie (Validierung):** Transaktionen laufen völlig frei und ohne jede Sperre ab. Erst ganz am Ende (beim `COMMIT`) wird validiert, ob in der Zwischenzeit eine andere Transaktion dieselben Daten geändert hat.
- **Vorteil / Nachteil:** Ermöglicht bei wenig Konflikten eine überragende Parallelität und Performance. Der Nachteil: Bei einem Konflikt muss die Transaktion komplett zurückgerollt (`ROLLBACK`) und neu gestartet werden, was sich bei hoher Last gefährlich aufschaukeln kann.

--------------------------------------------------------------------------------

Deep Dive: Deadlocks und 2PL in der pessimistischen Strategie

**A. Der Deadlock (Verklemmung)** Ein Deadlock ist das Worst-Case-Szenario der pessimistischen Sperrverwaltung. Er entsteht, wenn mehrere Transaktionen wechselseitig auf die Freigabe von Ressourcen (Locks) warten, die jeweils von der anderen Transaktion gehalten werden.

- _Beispiel:_ Transaktion 1 sperrt Datensatz 3001 und will danach 3005 sperren. Gleichzeitig hat Transaktion 2 den Datensatz 3005 gesperrt und wartet auf die Freigabe von 3001. Nichts geht mehr, das System steht still.

**B. Das Zweiphasen-Sperrprotokoll (2PL)** Das wichtigste formale Sperrverfahren zur Umsetzung der Isolation (I in ACID) ist das 2PL (Two-Phase Locking). Es ist die Grundlage aller pessimistischen Locking-Verfahren und garantiert mathematisch die Serialisierbarkeit von Transaktionen. Es schreibt zwingend vor, dass jede Transaktion in zwei strikt getrennten Phasen abläuft:

1. **Wachstumsphase (Growing Phase):** Die Transaktion darf neue Sperren anfordern, aber noch keine einzige Sperre freigeben.
2. **Schrumpfphase (Shrinking Phase):** Die Transaktion darf Sperren freigeben, darf dann aber absolut _keine neuen Sperren_ mehr anfordern.

--------------------------------------------------------------------------------

Flashcards

Vergleichen Sie die optimistische mit der pessimistischen Synchronisationsstrategie hinsichtlich ihrer Grundannahmen über Konflikte und der Sperren.
?
Die **pessimistische Strategie** geht von häufigen Konflikten aus; daher werden sofort harte Sperren (Locks) gesetzt, bevor Daten gelesen oder geschrieben werden. Die **optimistische Strategie** geht von seltenen Konflikten aus; Transaktionen laufen ohne Sperren ab. Erst ganz am Ende (bei der Validierung zum COMMIT) wird auf Konflikte geprüft.

Was ist der Hauptnachteil der optimistischen Synchronisationsstrategie bei Systemen mit sehr hohen gleichzeitigen Zugriffszahlen?::Bei einem erkannten Konflikt am Ende der Transaktion muss diese komplett abgebrochen (ROLLBACK) und neu gestartet werden. Bei hoher Last kann sich dies aufschaukeln und zu massiven Performance-Einbrüchen führen.

Was versteht man im Kontext der pessimistischen Synchronisation unter einem "Deadlock" (Verklemmung) und wie entsteht dieser Zustand?::Ein Deadlock ist eine wechselseitige Blockierung, bei der mehrere Transaktionen endlos auf die Freigabe von Ressourcen (Locks) warten, die jeweils von der anderen Transaktion gehalten werden (z. B. TA1 sperrt A und wartet auf B; TA2 sperrt B und wartet auf A).

Was ist das Ziel und die Funktion des Zweiphasen-Sperrprotokolls (2PL)?::Es ist der Mechanismus zur Umsetzung der Isolation (I in ACID) und die Grundlage pessimistischer Locking-Verfahren. Es garantiert die Serialisierbarkeit von parallelen Transaktionen.

Erklären Sie die zwei Phasen des Zweiphasen-Sperrprotokolls (2PL).
?
1. **Wachstumsphase (Growing Phase):** Die Transaktion darf neue Sperren anfordern, aber noch keine einzige Sperre wieder freigeben.
2. **Schrumpfphase (Shrinking Phase):** Die Transaktion darf Sperren freigeben, darf ab diesem Zeitpunkt aber keine neuen Sperren mehr anfordern.

Unterscheiden Sie das Zweiphasen-Sperrprotokoll (2PL) vom Zweiphasen-Commit-Protokoll (2PC) hinsichtlich ihrer jeweiligen Zielsetzung innerhalb der ACID-Kriterien.
?
Das **2PL (Two-Phase Locking)** dient der Umsetzung der **Isolation (I)** und garantiert die Serialisierbarkeit von Transaktionen durch geregelte Sperr- und Freigabephasen. Das **2PC (Two-Phase Commit)** dient der Umsetzung der **Atomarität (A)** in verteilten Systemen und koordiniert den gemeinsamen Abschluss (COMMIT oder ABORT) einer Transaktion über mehrere Server-Knoten hinweg.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Sperrverfahren]]
SORT file.mtime DESC
```