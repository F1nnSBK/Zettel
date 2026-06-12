#Note

2026-06-12

Tags: [[Datenbanken]], [[Big Data]], [[NoSQL]], [[Architektur]]
#datenbanken

---
**Big Data** ist das Resultat der massiven Digitalisierung. Das weltweit generierte Datenvolumen wächst exponentiell (Prognosen gehen von fast 400 Zettabyte im Jahr 2028 aus). Klassische relationale Datenbanken sind für diese Art der Last nicht gebaut.

Um die Herausforderungen von Big Data zu kategorisieren, nutzt man die **6 V's**:

Die technologischen Treiber (Die 3 V's)

Diese drei Dimensionen sind der Hauptgrund, warum NoSQL-Datenbanken überhaupt erfunden wurden:

1. **Volume (Menge):** Die schiere Menge an produzierten Daten. Relationale Systeme lassen sich nicht endlos vertikal skalieren; Big Data erfordert zwingend horizontale Skalierbarkeit über verteilte Knoten.
2. **Velocity (Geschwindigkeit):** Die Geschwindigkeit der Datengenerierung und -verarbeitung (Echtzeitverarbeitung).
3. **Variety (Vielfalt):** Unterschiedliche Datentypen und -quellen. Daten liegen nicht mehr nur strukturiert in Tabellen vor, sondern halbstrukturiert (JSON, XML) oder völlig unstrukturiert (Bilder, E-Mails). NoSQL bietet hier die nötige Schema-Flexibilität.

Die qualitativen Treiber (Die neuen 3 V's)

Da das reine Sammeln von Daten keinen Wert an sich darstellt, wurden die Kriterien erweitert: 4. **Veracity (Richtigkeit):** Die Richtigkeit bzw. Echtheit der Daten. Sind die gesammelten Sensordaten verlässlich?. 5. **Validity (Gültigkeit):** Die Prüfung der Datenqualität und die generelle Aussagekraft der Daten. 6. **Value (Wert):** Der eigentliche wirtschaftliche Wert der Daten für ein Unternehmen, der erst durch eigene Analysen (Data Science, Business Intelligence) geschöpft wird.

---

Flashcards

Was ist der Kerngedanke hinter dem Begriff "Big Data" in Bezug auf klassische Softwarewerkzeuge?
?
Big Data beschreibt Datenmengen, die aufgrund der fortschreitenden Digitalisierung so groß, so schnelllebig und so heterogen sind, dass sie mit herkömmlichen Softwarewerkzeugen und klassischen relationalen Datenbanken nicht mehr effizient beherrschbar sind.

Welche drei klassischen Dimensionen (die ursprünglichen "3 V's") treiben den Einsatz von NoSQL-Datenbanken im Big-Data-Umfeld an?::**Volume** (riesige Datenmengen), **Velocity** (hohe Geschwindigkeit bei Generierung und Verarbeitung) und **Variety** (flexible, oft unstrukturierte Datenformate).

Nennen Sie die drei erweiterten "V's", die neben Volume, Velocity und Variety im modernen Big-Data-Kontext die Qualität und den wirtschaftlichen Nutzen der Daten beschreiben.::**Veracity** (Richtigkeit/Echtheit der Daten), **Validity** (Gültigkeit/Datenqualität) und **Value** (wirtschaftlicher Wert durch Analysen).

Wie lösen NoSQL-Systeme das Big-Data-Problem der "Variety" (Vielfalt der Daten)?::Sie erzwingen kein starres Tabellenschema (Schema-Flexibilität) und können daher mit völlig unterschiedlichen Datentypen (z.B. verschachtelte JSON-Dokumente) und semi-strukturierten Daten aus verschiedenen Quellen problemlos umgehen.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Big Data]]
SORT file.mtime DESC
```