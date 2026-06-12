#Note

2026-06-12

Tags: [[Datenbanken]], [[NoSQL]], [[Redis]], [[Architektur]], [[In-Memory]]
#datenbanken 

---
Ein **Key-Value Store** ist die einfachste Form der NoSQL-Datenbanken. Er nutzt ein Zuweisung:UniqueKey→Value Modell ohne jegliches Vorab-Schema. Typische Anwendungsfälle sind extrem schnelle, leselastige Workloads wie Session-Management, High-Speed-Lookups und Caching.

Das prominenteste System auf dem Markt ist **Redis** (REmote DIctionary Server).

Strukturierung durch Namespacing (Flachheit)

Technisch sind alle Keys in diesem System absolut gleichberechtigt auf der obersten Ebene (Flachheit). Die Datenbank versteht keine Hierarchien. Um trotzdem logische Zusammenhänge für den Entwickler abzubilden, nutzt man **Namespacing durch Trennzeichen (oft Doppelpunkte)**: `SET User:U17:email "max@dhbw.de"`. _Wichtig:_ Die Datenbank versteht diese Hierarchie nicht, sie existiert rein in der Anwendungslogik.

Strings vs. Hashes (Der Performance-Trick)

In Redis gibt es zwei Ansätze, um ein "Objekt" (z.B. einen Benutzer mit Vorname, Nachname und Email) zu speichern:

1. **Das flache String-Modell:** Man legt drei völlig unabhängige Keys an (`User:1:vorname`, `User:1:nachname`, `User:1:email`). Das Problem: Man muss drei langsame Netzwerk-Anfragen (`GET`) an die Datenbank schicken, um den User zu laden.
2. **Das Hash-Modell (Best Practice):** Redis bietet den nativen Datentyp _Hash_ (eine Art Unter-Map/Container). Man speichert alle Felder unter einem einzigen Hauptschlüssel (`User:1`). Über den Befehl `HGETALL` kann man das komplette User-Objekt mit einem einzigen Netzwerkaufruf extrem performant laden. Redis zwingt hier zu Typsicherheit auf Key-Ebene: Versucht man ein Hash-Feld mit einem String-Befehl zu lesen, wirft Redis einen Fehler.

Persistenz in der In-Memory-Welt

Da Redis primär im flüchtigen RAM operiert, um Antwortzeiten im Mikrosekunden-Bereich zu liefern, droht bei einem Stromausfall der komplette Datenverlust. Redis löst dieses Problem über zwei Mechanismen:

1. **RDB (Redis Database):** Das System macht in zyklischen Abständen kompakte Komplett-Schnappschüsse (Snapshots) des RAMs und legt sie auf der Festplatte ab.
2. **AOF (Append Only File):** Für absolute Sicherheit protokolliert Redis jede einzelne Schreiboperation nach dem [[Journaling]]-Prinzip fortlaufend in eine Datei.

---

### Flashcards

Namensräume: Wie lässt sich im Schlüsselraum (Key Space) einer Key-Value Datenbank trotz technischer Flachheit eine Hierarchie simulieren?
?
Durch die Konvention, spezielle Trennzeichen (meistens Doppelpunkte, z.B. `User:1001:Name`) direkt in den Schlüsseln zu verwenden. Dies macht logische Hierarchien für den Entwickler sichtbar, obwohl die Datenbank diese Schlüssel technisch nur als isolierte, flache Strings betrachtet.

In-Memory: Was ist der entscheidende Vorteil von In-Memory-Datenbanken wie Redis und wie wird dennoch Persistenz (Ausfallsicherheit) gewährleistet?
?
Der Vorteil liegt in der extremen Zugriffsgeschwindigkeit (Antwortzeiten im Mikrosekunden-Bereich / konstante Zugriffszeit O(1)), da Berechnungen und Datenhaltung direkt im schnellen RAM erfolgen. Persistenz wird dennoch durch zwei Mechanismen gesichert: **RDB** (zyklische Snapshots/Schnappschüsse auf die Festplatte) und **AOF** (ein Append-Only-File Journal, das jede Änderung protokolliert).

Effizienz: Warum ist das Speichern eines strukturierten Objekts als Redis Hash wesentlich einfacher und performanter als das Speichern über mehrere separate Strings?
?
Weil Hashes (als Datenstruktur) alle Attribute eines Objekts (z.B. Vorname, Nachname, Email) logisch unter einem einzigen Hauptschlüssel bündeln. Dadurch kann das gesamte Objekt mit einem einzigen Netzwerk-Befehl (`HGETALL`) geladen werden, während beim String-Modell unzählige, langsame Einzel-`GET`-Aufrufe nötig wären.

Warum ist die Zugriffszeit bei einem simplen Key-Value-Store massiv skalierbar und völlig unabhängig von der Gesamtgröße der Datenbank?::Weil die Datenbank aufgrund des simplen Schlüssel-Wert-Mappings konstante Zugriffszeiten (O(1)) bietet. Es ist für das System völlig irrelevant, ob es 100 oder 100 Milliarden Datensätze durchsucht, es findet den Wert direkt.

Was passiert in Redis, wenn man den String-Befehl `GET` auf einen Schlüssel anwendet, hinter dem physisch ein Hash-Datentyp gespeichert ist?::Redis wirft einen Laufzeitfehler (WRONGTYPE-Error), da es eine strenge Typsicherheit auf Key-Ebene erzwingt. Für Hashes müssten typspezifische Befehle wie `HGET` oder `HGETALL` genutzt werden.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Key-Value Store]]
SORT file.mtime DESC
```