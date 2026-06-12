#Note

2026-06-12

Tags: [[Datenbanken]], [[NoSQL]], [[MongoDB]], [[BSON]], [[JSON]]
#datenbanken 

---
Um zu verstehen, warum MongoDB nicht einfach Text-JSON auf die Festplatte schreibt, müssen wir die Unterschiede der beiden Formate betrachten:

Das Problem mit JSON (JavaScript Object Notation)

JSON ist der absolute Standard für Web-APIs. Es speichert Daten in simplen `Key:Value`-Paaren (z.B. `"alter": 30`) und nutzt geschweifte Klammern `{}` für Objekte.

- **Nachteil 1 (Performance):** JSON ist reiner Text. Um herauszufinden, ob in einem riesigen Dokument das Feld "Status" existiert, muss die Datenbank den gesamten Text Zeichen für Zeichen von links nach rechts scannen (Parsen). Das ist extrem rechenintensiv.
- **Nachteil 2 (Datentypen):** JSON kennt nur rudimentäre Typen (String, Number, Boolean, Array, Object, Null). Es gibt z. B. keinen Datentyp für ein echtes Datum oder für Binärdaten.

Die Lösung: BSON (Binary JSON)

MongoDB nutzt BSON, um diese Schwächen zu beheben. Es ist eine **binäre Repräsentation** der JSON-Daten.

**1. Performance durch Indizierung** Da BSON maschinennah und binär gespeichert wird, kann MongoDB das Dokument rasend schnell parsen und Felder extrem effizient indizieren. Die Datenbank kann direkt zu den relevanten Bytes im RAM springen, ohne Text lesen zu müssen.

**2. Erweiterte Datentypen** BSON erweitert den rudimentären JSON-Standard um entscheidende, typisierte Datentypen:

- **High-Precision Date:** Für echte Datums- und Zeitstempel.
- **IEEE 754 Decimal128:** Hochpräzise Dezimalzahlen (essenziell für Finanzdaten, da normale JSON-Floats zu Rundungsfehlern neigen).
- **BinData:** Um binäre Daten abzuspeichern.
- **ObjectId:** Die von MongoDB automatisch generierte, eindeutige ID (`_id`), die jedem Dokument zwingend zugewiesen wird.

---

### Flashcards

Welches Format nutzt MongoDB intern zur Speicherung und was ist der Unterschied zum klassischen JSON?
?
MongoDB nutzt **BSON** (Binary JSON). Der Unterschied ist, dass BSON eine binäre Repräsentation ist. Das macht es maschinell wesentlich effizienter zu verarbeiten (schnelleres Parsen/Indizieren) und es unterstützt zusätzliche, maschinennahe Datentypen (wie z.B. Date, BinData oder IEEE 754 High-Precision Dezimalzahlen), die dem klassischen, rein textbasierten JSON fehlen.

Was ist JSON und warum ist es für den Datenaustausch so beliebt?::JSON (JavaScript Object Notation) ist ein textbasiertes, für Menschen leicht lesbares Datenaustauschformat, das auf Schlüssel-Wert-Paaren aufbaut. Es ist sprachunabhängig und hat XML weitgehend als Standard für strukturierte Daten abgelöst.

Warum generiert MongoDB bei der Speicherung von Dokumenten häufig automatisch eine `ObjectId`?::Weil jedes Dokument in MongoDB zwingend einen eindeutigen Primärschlüssel (im Feld `_id`) benötigt. Gibt der Entwickler beim Einfügen (Insert) keinen Schlüssel mit, erstellt MongoDB vollautomatisch eine BSON-ObjectId, um die Eindeutigkeit sicherzustellen.

Welchen grundlegenden Performance-Vorteil bietet BSON gegenüber JSON bei Suchanfragen in der Datenbank?::Da JSON reiner Text ist, müsste eine Datenbank den String zeilenweise parsen, um ein Attribut zu finden. Das binäre BSON-Format hingegen ist auf maschinelle Verarbeitung optimiert und ermöglicht es der Datenbank, Längeninformationen zu nutzen, um Felder extrem schnell zu finden und zu indizieren.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[BSON]]
SORT file.mtime DESC
```