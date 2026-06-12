#Note

2026-06-12

Tags: [[Datenbanken]], [[NoSQL]], [[Redis]], [[In-Memory]], [[Caching]]
#datenbanken 

---
**Redis** wurde 2009 von Salvatore Sanfilippo entwickelt und steht für **RE**mote **DI**ctionary **S**erver. Da das System Daten primär im Arbeitsspeicher (RAM) hält, bietet es konstante Zugriffszeiten (O(1)) und ist extrem leistungsstark. Es wird klassischerweise für Session-Management, High-Speed-Lookups und Real-Time Analytics eingesetzt.

Datentypen und Strikte Typsicherheit

Im Gegensatz zu einem "dummen" Key-Value-Store, der nur Text kennt, unterstützt Redis native Datenstrukturen:

- **Strings:** Der Basis-Typ für Text oder Zahlen. _(Befehle:_ _SET__,_ _GET__,_ _INCR__)_.
- **Hashes:** Maps von Feldern zu Werten. Perfekt, um strukturierte Objekte (wie einen ganzen User) unter einem einzigen Key abzuspeichern. _(Befehle:_ _HSET__,_ _HGET__,_ _HGETALL__)_.
- **Lists / Sets / Streams:** Für Warteschlangen, eindeutige Mengen und Event-Logs.

_Achtung:_ Redis erzwingt Typsicherheit auf Key-Ebene! Wendet man `GET` (einen String-Befehl) auf einen Schlüssel an, der einen Hash enthält, wirft Redis sofort einen **WRONGTYPE-Error**.

Strings vs. Hashes (Das Java-Problem)

Wenn wir ein User-Objekt (Vorname, Nachname, E-Mail) speichern wollen, gibt es zwei Wege:

1. **Das String-Modell:** Wir legen drei flache Keys an (`user:1:vorname`, `user:1:nachname`). Um den User in Java zu laden, müssen wir drei einzelne `jedis.get()`-Befehle über das Netzwerk an Redis schicken.
2. **Das Hash-Modell (Best Practice):** Wir speichern alle Attribute als Felder innerhalb eines einzigen Hash-Keys (`user:1`). In Java (`Jedis`) können wir nun den gesamten User mit einem einzigen Netzwerkaufruf (`jedis.hgetAll()`) abholen. Jedis wandelt die Antwort automatisch in eine bequeme `java.util.Map` um.

Ausfallsicherheit (Persistenz)

Da der RAM bei einem Stromausfall gelöscht wird, schützt sich Redis durch zwei Mechanismen vor Datenverlust:

1. **RDB (Redis Database):** Das System erstellt zyklisch kompakte Komplett-Schnappschüsse (Point-in-Time Recovery) der Daten und legt sie auf der Festplatte ab.
2. **AOF (Append Only File):** Protokolliert nach dem Journaling-Prinzip fortlaufend jede einzelne Schreiboperation. Bietet maximale Sicherheit gegen Abstürze.

---

### Flashcards

Wie lässt sich im Schlüsselraum (Key Space) einer Key-Value-Datenbank trotz technischer Flachheit eine Hierarchie simulieren?
?
Durch die Konvention, spezielle Trennzeichen (wie z. B. Doppelpunkte) direkt in den Schlüsseln zu verwenden (z. B. `User:1001:Name`). Dies macht logische Hierarchien für den Anwendungs-Entwickler sichtbar, obwohl die Datenbank diese Schlüssel technisch nur als isolierte, flache Strings betrachtet und die Logik selbst gar nicht "versteht".

Was ist der entscheidende Vorteil von In-Memory-Datenbanken wie Redis und wie wird dennoch Persistenz gewährleistet?
?
Der entscheidende Vorteil ist die extreme Zugriffsgeschwindigkeit (Antwortzeiten im Mikrosekunden-Bereich), da Daten direkt im schnellen RAM (Arbeitsspeicher) gehalten werden. Persistenz wird gewährleistet durch **RDB** (zyklische, kompakte Schnappschüsse/Snapshots auf die Festplatte) und **AOF** (ein Append-Only-File, das jede Schreiboperation fortlaufend protokolliert / Journaling).

Warum ist das Speichern eines strukturierten Objekts als Redis Hash wesentlich einfacher und performanter als das Speichern über mehrere separate Strings?
?
Weil bei einem Redis-Hash alle Daten, die logisch zusammengehören (z. B. Vorname, Nachname, E-Mail eines Users), als Felder gebündelt unter einem einzigen Hauptschlüssel gespeichert werden. Dadurch kann das komplette Objekt mit einem einzigen Befehl (z. B. `HGETALL`) extrem schnell über das Netzwerk ausgelesen werden, anstatt viele einzelne, langsame `GET`-Aufrufe für separate Strings machen zu müssen.

Was passiert in Redis, wenn man den Basis-Befehl `GET` auf einen Schlüssel anwendet, hinter dem physisch ein Hash-Datentyp gespeichert ist?::Redis wirft einen Laufzeitfehler (den sogenannten WRONGTYPE-Error), da das System eine strenge Typsicherheit auf Key-Ebene erzwingt. Für Hashes müssen zwingend typspezifische Befehle wie `HGET` oder `HGETALL` genutzt werden.

Was besagt das "O(1)"-Prinzip bei den Zugriffszeiten eines Key-Value-Stores?::Es bedeutet, dass die Zugriffszeit ("Time Complexity") absolut konstant bleibt. Es ist für das System performancetechnisch völlig egal, ob sich 100 Datensätze oder 100 Milliarden Datensätze in der Datenbank befinden – der Zugriff dauert immer exakt gleich lang.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Redis]]
SORT file.mtime DESC
```