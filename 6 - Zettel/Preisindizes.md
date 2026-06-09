#Note

2026-05-15

Tags: [[Statistik]], [[Verhältniszahlen]], [[Wirtschaftsstatistik]], [[Inflation]]
#deskriptive_statistik

---
Preisindizes dienen dazu, die Preisentwicklung für eine Gruppe von Gütern zusammenzufassen. Sie sind die Grundlage für die Berechnung der Inflationsrate (Verbraucherpreisindex).

### Notation

- $p_i^0, p_i^t$: Preise des Gutes $i$ im Basisjahr ($0$) und Berichtsjahr ($t$).
- $q_i^0, q_i^t$: Mengen des Gutes $i$ im Basisjahr ($0$) und Berichtsjahr ($t$).

### Preisindex nach Laspeyres ($P_L$)

Der Warenkorb wird auf dem Niveau des **Basisjahres** fixiert. Man fragt: „Was würde der alte Warenkorb heute kosten?“

$$P_L = \frac{\sum_{i=1}^n p_i^t \cdot q_i^0}{\sum_{i=1}^n p_i^0 \cdot q_i^0}$$

- **Vorteil:** Nur die Preise müssen aktuell erhoben werden; der Warenkorb bleibt über Jahre gleich (gut für die amtliche Statistik).
- **Nachteil:** Substitutionsprozesse der Konsumenten werden ignoriert.

### Preisindex nach Paasche ($P_P$)

Der Warenkorb wird auf dem Niveau des **Berichtsjahres** fixiert. Man fragt: „Was hat der aktuelle Warenkorb früher gekostet?“

$$P_P = \frac{\sum_{i=1}^n p_i^t \cdot q_i^t}{\sum_{i=1}^n p_i^0 \cdot q_i^t}$$

- **Vorteil:** Berücksichtigt das aktuelle Konsumverhalten.
- **Nachteil:** Mengen müssen für jedes Jahr neu erhoben werden (teuer/aufwendig).

### Vergleich Laspeyres vs. Paasche

|**Merkmal**|**Laspeyres (PL​)**|**Paasche (PP​)**|
|---|---|---|
|**Warenkorb**|Basisjahr ($q^0$)|Berichtsjahr ($q^t$)|
|**Preistendenz**|Eher zu hoch (Obergrenze)|Eher zu niedrig (Untergrenze)|
|**Praxis**|Standard für Inflation|Seltener (eher BIP-Deflator)|

---

### Flashcards

Welche Mengenkomponente wird beim Preisindex nach Laspeyres konstant gehalten?::Die Mengen des Basisjahres ($q_i^0$).
<!--SR:!2026-06-09,1,230-->

Warum gilt der Laspeyres-Index als „konsumentenunfreundlich“ bei der Inflationsmessung?::Weil er davon ausgeht, dass Konsumenten starr am alten Warenkorb festhalten und nicht auf günstigere Ersatzprodukte ausweichen, wenn ein Gut teurer wird.
<!--SR:!2026-06-09,1,230-->

Wie lautet die Grundformel für den Preisindex nach Paasche?
?
$$P_P = \frac{\sum p_i^t \cdot q_i^t}{\sum p_i^0 \cdot q_i^t}$$Er vergleicht die Kosten des aktuellen Warenkorbs zu heutigen Preisen mit den Kosten des gleichen (aktuellen) Warenkorbs zu Preisen des Basisjahres.
<!--SR:!2026-06-09,1,230-->

Was ist der Unterschied zwischen einem Preisindex und einem Mengenindex?
?
Beim Preisindex werden die Mengen fixiert, um Preisänderungen zu messen. Beim Mengenindex werden die Preise fixiert (z. B. auf Basisjahr-Niveau), um die reale Veränderung des Volumens/Verbrauchs zu isolieren.
<!--SR:!2026-06-11,3,250-->


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Preisindizes]]
SORT file.mtime DESC
```