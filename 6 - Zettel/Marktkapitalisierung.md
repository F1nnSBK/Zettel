#Note

2025-12-11

Tags: [[Grundlagen Finanzierung & Investition]], [[Aktie]], [[Unternehmensbewertung]]
#finance

---
Die **Marktkapitalisierung** (Market Cap) ist der aktuelle Gesamtwert des Eigenkapitals eines börsennotierten Unternehmens, bewertet durch den Markt.

#### Berechnung
Sie berechnet sich als Produkt aus dem aktuellen Börsenkurs und der Anzahl der **ausstehenden** Aktien.

$$\text{Market Cap} = \text{Aktienkurs} \cdot \text{Anzahl ausstehender Aktien}$$

_(Hinweis: Im Unternehmensbesitz befindliche "Eigene Aktien" werden nicht mitgerechnet, da sie dem Markt nicht zur Verfügung stehen)._

#### Kategorisierung (Indizes)
Die Marktkapitalisierung ist meist das entscheidende Kriterium für die Aufnahme in Aktienindizes (z.B. DAX).
- **Large Caps (Blue Chips):** Unternehmen mit sehr hoher Marktkapitalisierung (z.B. SAP, Siemens).
- **Mid Caps:** Mittelgroße Unternehmen (MDAX).
- **Small Caps:** Kleinere Unternehmen (SDAX).

---

#### Aktienrückkäufe (Share Buybacks)
Warum kaufen Konzerne ihre eigenen Aktien zurück?
Unternehmen nutzen überschüssige Liquidität oft, um Aktien über die Börse zurückzukaufen und meist anschließend zu vernichten.

**Die 4 Hauptmotive:**
1. Kennzahlenpflege (EPS-Steigerung):
    Durch die Vernichtung der Aktien sinkt die Anzahl der ausstehenden Aktien ($n$). Da der Gewinn gleich bleibt, steigt der Gewinn pro Aktie (Earnings per Share, EPS).
    
    $$\uparrow EPS = \frac{\text{Gewinn}}{\text{Anzahl Aktien} \downarrow}$$
    
    $\rightarrow$ Das Kurs-Gewinn-Verhältnis (KGV) wirkt optisch günstiger.
    
2. Signaling (Unterbewertung):
    Das Management signalisiert dem Markt: "Wir halten unsere eigene Aktie für unterbewertet und investieren lieber in uns selbst als in teure Übernahmen." Das stärkt das Vertrauen der Anleger.
    
3. Kapitalstruktur-Optimierung:
    Das Eigenkapital wird reduziert. Dadurch steigt der Verschuldungsgrad relativ an, was den Leverage-Effekt verstärken kann (sofern $r_{GK} > r_{FK}$).
    
4. Mitarbeiterbeteiligung:
    Die zurückgekauften Aktien werden nicht vernichtet, sondern als Boni/Optionen an Mitarbeiter ausgegeben (keine Verwässerung für Altaktionäre, da keine neuen Aktien geschaffen werden).
    

---
#### Flashcards

Wie berechnet sich die Marktkapitalisierung? :: Aktienkurs $\times$ Anzahl der ausstehenden Aktien.
<!--SR:!2025-12-17,1,230-->

Werden "Eigene Aktien" (Treasury Shares) bei der Berechnung der Marktkapitalisierung berücksichtigt? :: Nein, nur die **ausstehenden** (im Umlauf befindlichen) Aktien zählen.

Welchen Effekt hat ein Aktienrückkauf auf den Gewinn pro Aktie (EPS)? :: Der Gewinn pro Aktie **steigt**, da sich der Gewinn auf weniger Aktien verteilt.

Was versteht man unter "Signaling" beim Aktienrückkauf? :: Das Management signalisiert dem Markt, dass es die eigene Aktie für **unterbewertet** hält (Vertrauensbeweis).

Wie nennt man Unternehmen mit der höchsten Marktkapitalisierung (z.B. DAX-Konzerne)? :: **Large Caps** oder Blue Chips.

Ist die Marktkapitalisierung identisch mit dem Eigenkapital in der Bilanz? :: Nein. Die Marktkapitalisierung ist der **Marktwert** (Börsenwert), das bilanzielle Eigenkapital ist der **Buchwert**. (Der Marktwert ist bei gesunden Firmen meist deutlich höher).

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Marktkapitalisierung]]
SORT file.mtime DESC
```