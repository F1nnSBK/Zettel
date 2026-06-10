#Note

2026-06-09

Tags: [[Datenbanken]], [[Relationenalgebra]], [[Logik]], [[SQL]]
#datenbanken 

---
Die **Logischen Operatoren** dienen als Kontrollwerkzeuge bei der Selektion von Daten. Sie arbeiten nicht auf Tabellenebene, sondern **bewerten auf Tupel-Ebene (Zeilenebene)**. Da sie auf der Booleschen Algebra beruhen, sind ihre Rechenregeln absolut identisch zu denen der Mengenlehre.

#### Die 4 logischen Kernoperatoren

Wenn die Marketingabteilung eine komplexe Zielgruppe sucht, müssen die natürlichen Sätze in formale Logik übersetzt werden:

|Operator|Logik-Symbol|SQL-Befehl|Funktion / Bedeutung|Business-Beispiel|
|---|---|---|---|---|
|**Konjunktion (AND)**|∧|`AND`|**Alle** verknüpften Bedingungen müssen zwingend zutreffen.|_"Kunden aus Berlin_ **und** _älter als 30."_<br>σStadt=′Berlin′∧Alter>30​(Kunden)|
|**Disjunktion (OR)**|∨|`OR`|**Mindestens eine** der Bedingungen muss zutreffen.|_"Kunden aus Berlin_ **oder** _älter als 30."_<br>σStadt=′Berlin′∨Alter>30​(Kunden)|
|**Negation (NOT)**|¬|`NOT`|Kehrt den Wahrheitswert um. Wählt genau die Tupel, die die Bedingung **nicht** erfüllen.|_"Kunden, die_ **nicht** _in Berlin wohnen."_<br>σ¬(Stadt=′Berlin′)​(Kunden)|
|**Antivalenz (XOR)**|⊕|`(A OR B) AND NOT (A AND B)`|Exklusives Oder: **Genau eine** Bedingung ist wahr, aber niemals beide gleichzeitig.|_"Kunden aus Berlin oder Hamburg, aber_ **nicht aus beiden**_."_|

#### Die Eiserne Regel: Priorität (Ausführungsreihenfolge)

Genau wie bei "Punkt vor Strich" in der Mathematik, verarbeitet die Datenbank logische Operatoren in einer absolut strikten Reihenfolge, wenn **keine Klammern** gesetzt sind:

1. **Klammer** `()` (Hebelt jede andere Regel aus!)
2. **NOT** ¬ (Negation wird zuerst gebunden)
3. **AND** ∧ (Bindet stärker als OR!)
4. **OR** ∨
5. **XOR** ⊕

**Die Gefahr des Distributivgesetzes:** Das Weglassen von Klammern verändert die Suchergebnismenge komplett! Die Abfrage _Alle Männer oder junge Ravensburger_ ( `männlich OR (jung AND aus Ravensburg)` ) liefert ein völlig anderes Ergebnis als _Alle männlichen oder jungen Kunden, die aus Ravensburg kommen_ ( `(männlich OR jung) AND aus Ravensburg` ). Klammern können hier **nicht** weggelassen werden.

#### Das Gesetz von [[De Morgan]]

Das Gesetz von De Morgan ist das wichtigste Werkzeug, um komplexe negierte Bedingungen umzuformulieren und zu vereinfachen. Es besagt, dass sich beim Auflösen einer negierten Klammer das `AND` in ein `OR` umkehrt (und umgekehrt):

- **Regel 1:** ¬(A∧B)=¬A∨¬B
    - _Praxis:_ "Suche Kunden, die NICHT (männlich UND aus Ravensburg) sind" bedeutet das Gleiche wie "Suche Kunden, die NICHT männlich sind ODER NICHT aus Ravensburg kommen".
- **Regel 2:** ¬(A∨B)=¬A∧¬B
    - _Praxis:_ "Suche Kunden, die NICHT (männlich ODER aus Ravensburg) sind" bedeutet exakt "Suche Kunden, die NICHT männlich UND NICHT aus Ravensburg sind".

--------------------------------------------------------------------------------

### Flashcards

Was ist die funktionale Aufgabe eines logischen Operators in der Relationenalgebra?::Er arbeitet als Funktion, die für eine definierte Filterbedingung (z.B. in der Selektion) einen Wahrheitswert (WAHR oder FALSCH) für das jeweilige Tupel zurückliefert.
<!--SR:!2026-06-10,0,230-->

In welcher festen Reihenfolge (Priorität) arbeitet eine Datenbank logische Operatoren ab, wenn keine Klammern gesetzt sind?::1. Klammer, 2. NOT, 3. AND, 4. OR, 5. XOR.
<!--SR:!2026-06-10,0,230-->

Wie lässt sich der logische Operator XOR (exklusives Oder) durch AND, OR und NOT ausdrücken?::Eine Bedingung muss erfüllt sein, aber nicht beide: (A∨B)∧¬(A∧B).

Was besagt das erste Gesetz von De Morgan in Bezug auf eine verneinte UND-Bedingung?
?
Eine verneinte UND-Klammer wird zu einer ODER-Bedingung, bei der die einzelnen Parameter verneint sind. Logisch: ¬(A∧B)=¬A∨¬B.
<!--SR:!2026-06-13,3,250-->

Warum ist das Setzen von Klammern bei der Kombination von AND und OR (Distributivgesetz) geschäftskritisch?
?
Weil die Datenbank das AND ansonsten strikt vor dem OR berechnet. Wenn man Klammern weglässt, verändert das die Semantik und damit die Ergebnismenge völlig (z.B. `A OR (B AND C)` vs. `(A OR B) AND (A OR C)`).


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Logische Operatoren]]
SORT file.mtime DESC
```