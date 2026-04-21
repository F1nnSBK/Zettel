#Note

2026-01-02

Tags: [[Statistik]], [[Deskriptive Statistik]], [[Daten]]
#deskriptive_statistik

---
Nominalskala (Nominales Merkmal)
-> Unterscheidung nur nach **Art und Weise** (Kategorie/Name). Es existiert **keine** sinnvolle Rangfolge.

• _Zulässige Relationen:_ Gleichheit (=) oder Ungleichheit (=).
• _Beispiele:_ Geschlecht, Nationalität, Farbe, Wohnort,,.

Ordinalskala (Ordinales Merkmal)
-> Die Ausprägungen weisen eine natürliche **Rangfolge** (Ordnung) auf. Die **Abstände** zwischen den Rängen sind jedoch **nicht** interpretierbar oder nicht gleich groß.

• _Zulässige Relationen:_ Größer/Kleiner (<,>) und Gleichheit.
• _Beispiele:_ Schulnoten, Güteklassen, Ratings, Tabellenplätze,,.

Kardinalskala (Metrische Skala)
-> Die Ausprägungen unterliegen einer Rangfolge und die **Abstände** (Differenzen) zwischen den Werten sind **interpretierbar**.

• _Zulässige Relationen:_ Alle mathematischen Operationen (Differenzen, Summen etc., je nach Unterteilung).

• _Unterteilung:_
	◦ **Intervallskala:** Kein natürlicher Nullpunkt (z. B. Temperatur in °C),.
	◦ **Verhältnisskala:** Natürlicher Nullpunkt existiert (z. B. Gewicht, Länge, Einkommen),.

• _Beispiele:_ Alter, Größe, Geldbeträge.


---
#### Flashcards

Was unterscheidet die Ordinalskala von der Nominalskala? :: Bei der Ordinalskala lassen sich die Ausprägungen in eine sinnvolle Rangfolge bringen, bei der Nominalskala nicht.

Was ist das entscheidende Merkmal einer Kardinalskala (metrischen Skala)? :: Die Abstände (Differenzen) zwischen den Merkmalsausprägungen sind interpretierbar.

Welche Rechenoperationen sind bei nominalskalierten Daten zulässig? :: Nur der Vergleich auf Gleichheit oder Ungleichheit (Häufigkeitszählungen).

Nenne ein Beispiel für ein ordinalskaliertes Merkmal! :: Schulnoten, Güteklassen oder Zufriedenheits-Ratings.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Skalenniveaus]]
SORT file.mtime DESC
```