#Note

2026-06-12

Tags: [[Datenbanken]], [[Verteilte Systeme]], [[Transaktionen]], [[2PC]], [[Architektur]]
#datenbanken

---
Das **Zweiphasen-Commit-Protokoll (2PC)** wird benötigt, wenn eine Transaktion über mehrere Server-Knoten läuft. Es koordiniert den gemeinsamen Abschluss (Commit oder Abort) über alle beteiligten Systeme hinweg und sichert so die **Atomarität im verteilten Fall (A in ACID)** ab.

Wichtig für die Architektur und Prüfungen: 2PC hat absolut nichts mit der Isolation oder der Sperrung von Daten zu tun.

Der Ablauf in 2 Phasen

Ein dedizierter "Koordinator" leitet den Prozess über das Netzwerk:

1. **Die Prepare-Phase (Vorbereitungsphase):** Der Koordinator fragt alle beteiligten Server-Knoten, ob sie die Transaktion vorbereiten und garantieren können, sie dauerhaft auszuführen. Die Knoten prüfen ihre lokalen Bedingungen (z.B. ob Constraints verletzt sind oder der Speicherplatz reicht). Können sie es garantieren, antworten sie dem Koordinator mit "PREPARED".
2. **Die Commit-Phase (Entscheidungsphase):** Der Koordinator sammelt die Antworten.
    - Haben _alle_ Knoten mit "PREPARED" geantwortet, schickt der Koordinator den Befehl `COMMIT` an alle. Die Daten werden endgültig geschrieben.
    - Hat auch nur ein _einziger_ Knoten mit einem Fehler geantwortet (oder gab es einen Netzwerk-Timeout), schickt der Koordinator sofort ein `ROLLBACK` an alle.

Dieser Mechanismus sorgt dafür, dass die verteilte Transaktion atomar abgeschlossen wird – alle Knoten committen gemeinsam oder gar nicht.

---

### Flashcards

Was ist die primäre Zielsetzung des Zweiphasen-Commit-Protokolls (2PC) in einer verteilten Datenbank?::Es dient als Mechanismus zur Umsetzung der Atomarität im verteilten Fall (A in ACID). Es garantiert, dass eine Transaktion über mehrere Knoten hinweg als eine unteilbare, atomare Einheit gemeinsam committet oder gemeinsam abgebrochen wird.

Beschreiben Sie den Ablauf der "Prepare-Phase" (Phase 1) im Zweiphasen-Commit-Protokoll.::Der Koordinator fragt alle beteiligten Knoten, ob sie die Transaktion vorbereiten und dauerhaft ausführen können. Die Knoten prüfen ihre internen Bedingungen und antworten dem Koordinator.

Wie entscheidet der Koordinator im 2PC in der "Commit-Phase" (Phase 2), ob die Transaktion final gespeichert wird?::Der Koordinator entscheidet basierend auf den Antworten aus Phase 1: Nur wenn _alle_ Knoten die Bereitschaft gemeldet haben, weist er alle an, gemeinsam zu committen. Andernfalls (bei auch nur einem Fehler) weist er alle an, die Transaktion gemeinsam abzubrechen (ROLLBACK).

Offizielle Prüfungsfrage 7: Unterscheiden Sie das Zweiphasen-Sperrprotokoll (2PL) vom Zweiphasen-Commit-Protokoll (2PC) hinsichtlich ihrer jeweiligen Zielsetzung innerhalb der ACID-Kriterien.
?
- **2PL (Two-Phase Locking):** Dient der Umsetzung der **Isolation (I)** und garantiert durch das Setzen von lokalen Sperren die Serialisierbarkeit von parallelen Transaktionen.
- **2PC (Two-Phase Commit):** Dient der Umsetzung der **Atomarität (A)** in verteilten Systemen und koordiniert den gemeinsamen Abschluss (COMMIT oder ABORT) einer Transaktion über mehrere Server-Knoten hinweg.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[2PC]]
SORT file.mtime DESC
```