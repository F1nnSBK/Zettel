#Note

2026-06-09

Tags: [[Datenbanken]], [[Relationenalgebra]], [[Logik]], [[Mengenlehre]], [[Menge]]
#datenbanken 

---
Die **De Morgan'schen Gesetze** sind zwei fundamentale Transformationsregeln der Booleschen Algebra und der Mengenlehre. Sie definieren exakt, was passiert, wenn man eine negierte Gruppe (eine Klammer mit NOT) auflöst.

Sie sind besonders wertvoll im Datenbankentwurf, da Fachabteilungen (z.B. Marketing) Zielgruppen oft sehr unscharf und mehrdeutig formulieren. De Morgan zwingt uns, die Semantik ("Zielgruppe aus einer anderen Perspektive betrachtet") glasklar aufzuschlüsseln.

**Das Business-Szenario:** Das Marketing sucht Kunden basierend auf zwei Merkmalen:

- Merkmal A: Kunde ist **männlich**.
- Merkmal B: Kunde wohnt in **Ravensburg**.

Gesetz 1: Die negierte ODER-Verknüpfung (Vereinigung)

Wenn wir ausschließen wollen, dass _mindestens eine_ von zwei Bedingungen zutrifft, bedeutet das logisch, dass **beide** Bedingungen _nicht_ zutreffen dürfen.

- **Logik:** ¬(A∨B)=¬A∧¬B
- **Mengenlehre:** (A∪B)C=AC∩BC

**Anwendung auf das Business-Szenario (Zielgruppe 1):**

- _Mit Klammern:_ Wir schließen alle Kunden aus, die entweder männlich sind ODER in Ravensburg wohnen: `NOT (männlich OR Ravensburg)`.
- _Ohne Klammern (De Morgan):_ Wir suchen ausschließlich Kundinnen, die sich außerhalb von Ravensburg befinden: `NOT männlich AND NOT Ravensburg`. Beide SQL-Abfragen liefern exakt dasselbe Ergebnis.

Gesetz 2: Die negierte UND-Verknüpfung (Durchschnitt)

Wenn wir ausschließen wollen, dass _beide_ Bedingungen _gleichzeitig_ zutreffen, bedeutet das logisch, dass **mindestens eine** Bedingung _nicht_ zutreffen darf.

- **Logik:** ¬(A∧B)=¬A∨¬B
- **Mengenlehre:** (A∩B)C=AC∪BC

**Anwendung auf das Business-Szenario (Zielgruppe 2):**

- _Das Problem:_ Die Aussage "Unsere Zielgruppe sind nicht Ravensburger" ist semantisch extrem missverständlich (ist die weibliche Form mitgemeint oder ausgeschlossen?). Gemeint ist: Die Zielgruppe sind Kunden, die _nicht gleichzeitig_ männlich UND in Ravensburg ansässig sind: `NOT (männlich AND Ravensburg)`.
- _Ohne Klammern (De Morgan):_ Die Zielgruppe besteht zum einen aus ALLEN Kundinnen (egal woher) und _zusätzlich_ aus allen nicht in Ravensburg ansässigen Kunden (egal welchen Geschlechts): `NOT männlich OR NOT Ravensburg`.

--------------------------------------------------------------------------------

### Flashcards

Warum sind die De Morgan'schen Gesetze im Datenbank-Kontext (z.B. bei SQL) so wichtig?
?
Weil sie es ermöglichen, extrem komplexe, verneinte logische Ausdrücke (`NOT (...)`) in der WHERE-Klausel fehlerfrei aufzulösen, zu vereinfachen und semantische Missverständnisse der natürlichen Sprache zu beseitigen.

Wie lautet das De Morgan'sche Gesetz für die Transformation einer negierten UND-Verknüpfung (in Logik und Mengenlehre)?
?
Die negierte UND-Verknüpfung wird zu einer ODER-Verknüpfung der einzeln negierten Parameter. **Logik:** ¬(A∧B)=¬A∨¬B **Menge:** (A∩B)C=AC∪BC

Wie lautet das De Morgan'sche Gesetz für die Transformation einer negierten ODER-Verknüpfung (in Logik und Mengenlehre)?
?
Die negierte ODER-Verknüpfung wird zu einer UND-Verknüpfung der einzeln negierten Parameter. **Logik:** ¬(A∨B)=¬A∧¬B **Menge:** (A∪B)C=AC∩BC

Übersetze folgenden Filter nach De Morgan, um die Klammer aufzulösen: `NOT (Alter > 30 OR Stadt = 'Berlin')`.::`NOT Alter > 30 AND NOT Stadt = 'Berlin'` (Oder vereinfacht: `Alter <= 30 AND Stadt != 'Berlin'`).

Was ist das logische Ergebnis (nach De Morgan), wenn wir die Menge "Kunden, die NICHT (männlich UND aus Ravensburg) sind" suchen?::Wir suchen alle Kunden, die NICHT männlich sind, ODER die NICHT aus Ravensburg stammen (Die Zielgruppe besteht also aus allen Frauen plus allen Männern, die nicht in Ravensburg leben).
<!--SR:!2026-06-11,1,230-->


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[De Morgan]]
SORT file.mtime DESC
```