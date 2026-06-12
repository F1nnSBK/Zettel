#Note

2026-06-12

Tags: [[Datenbanken]], [[Transaktionen]], [[Sperrverfahren]], [[Deadlock]]
#datenbanken 

---
Ein **Deadlock (Verklemmung)** ist der kritischste Fehlerzustand bei der Nutzung von pessimistischen Sperrverfahren (Locks). Er tritt auf, wenn mehrere Transaktionen wechselseitig auf die Freigabe von Ressourcen (Datenbanksperren) warten.

Die formale Definition lautet: _Ist die Freigabe einer Sperrung A von einer Sperrung B abhängig, die wiederum von der Freigabe der Sperrung A abhängt, spricht man von einem Deadlock_.

Die Anatomie eines Deadlocks (Beispiel)

Ein Deadlock benötigt immer mindestens zwei Transaktionen, die über Kreuz auf Ressourcen zugreifen wollen.

**Ausgangssituation:** AUTOCOMMIT ist deaktiviert, beide Sessions haben eine Transaktion gestartet.

1. **Transaktion 1 (TA1)** führt ein `UPDATE` auf Artikel `3001` aus. Das DBMS setzt sofort einen Lock auf den Datensatz `3001`.
2. **Transaktion 2 (TA2)** führt ein `UPDATE` auf Artikel `3005` aus. Das DBMS setzt sofort einen Lock auf den Datensatz `3005`.
3. Nun versucht **TA1**, im nächsten Schritt den Artikel `3005` zu ändern. Da dieser von TA2 gesperrt ist, muss TA1 warten.
4. Gleichzeitig versucht **TA2**, im nächsten Schritt den Artikel `3001` zu ändern. Da dieser von TA1 gesperrt ist, muss TA2 ebenfalls warten.

**Das Resultat:** TA1 wartet endlos auf TA2. TA2 wartet endlos auf TA1. Ein klassischer Deadlock.

Die Lösung des Datenbanksystems

Da die Transaktionen sich aus eigener Kraft niemals befreien können, besitzt das DBMS einen Hintergrundprozess (Deadlock-Monitor). Dieser erkennt die kreisförmige Abhängigkeit und wählt eine Transaktion als "Opfer" aus. Diese Opfer-Transaktion wird vom System mit einem harten Fehler abgebrochen und per `ROLLBACK` komplett zurückgerollt, wodurch ihre Sperren abfallen und die andere Transaktion weiterlaufen kann.

Daher ist es in der Applikationsentwicklung (z. B. mit JDBC/JPA) absolut essenziell, Fehler bei Transaktionen abzufangen (Try-Catch) und die Transaktion gegebenenfalls neu zu starten.

---

### Flashcards

Was versteht man unter einem Deadlock (Verklemmung) und wie entsteht dieser Zustand?
?
Ein Deadlock ist eine wechselseitige Blockierung, bei der mehrere Transaktionen endlos auf die Freigabe von Ressourcen warten, die jeweils von der anderen Transaktion gehalten werden. Er entsteht beispielsweise, wenn Transaktion 1 den Datensatz A exklusiv sperrt und auf die Freigabe von Datensatz B wartet, während Transaktion 2 zeitgleich den Datensatz B exklusiv gesperrt hat und auf die Freigabe von Datensatz A wartet.

Welche grundsätzliche Synchronisationsstrategie bringt das architektonische Risiko von Deadlocks mit sich?::Die pessimistische Synchronisation, da sie Konflikte durch das sofortige Setzen von harten Sperren (Locks) zu vermeiden versucht, bevor gelesen oder geschrieben wird.

Was unterscheidet einen Deadlock von einer normalen "Warteschlange" in einer Datenbank?::In einer Warteschlange wartet eine Transaktion auf das Ende einer _anderen_ Transaktion, die ganz normal abläuft und ihre Sperren irgendwann freigibt. Bei einem Deadlock warten _beide_ Transaktionen aufeinander, wodurch ein unendlicher Stillstand entsteht, der ohne Eingriff von außen nie aufgelöst wird.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Deadlock]]
SORT file.mtime DESC
```