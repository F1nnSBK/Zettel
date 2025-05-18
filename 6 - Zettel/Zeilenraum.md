#Note

2025-05-17

Tags: [[Zeilenraum]], [[Matrizen]], [[Lineare Algebra]], [[Vektorräume]], [[Unterraum]], [[Rang]], [[Basis]], [[Transponieren]], [[Spaltenraum]], [[Zeilenstufenform]], [[CR-Zerlegung]]

---

Der **Zeilenraum** einer [[Matrizen|Matrix]] $A$ (oft notiert als $\operatorname{Row}(A)$) ist die Menge aller möglichen [[Linearkombinationen|Linearkombinationen]] der Zeilenvektoren von $A$.

**Definition:**

Für eine $m \times n$ Matrix $A$ mit Zeilenvektoren $\vec{z}_1, \vec{z}_2, \dots, \vec{z}_m$ ist der Zeilenraum definiert als:

$$ \operatorname{Row}(A) = \{ c_1 \vec{z}_1 + c_2 \vec{z}_2 + \dots + c_m \vec{z}_m \mid c_1, c_2, \dots, c_m \in \mathbb{R} \} $$

Der Zeilenraum ist ein [[Vektorräume|Unterraum]] von $\mathbb{R}^n$.

**Eigenschaften und Bedeutung:**

* Der Zeilenraum einer Matrix $A$ ist identisch mit dem [[Spaltenraum]] ihrer [[Transponieren|transponierten]] Matrix $A^T$: $\operatorname{Row}(A) = \operatorname{Col}(A^T)$.
* **[[Rang]]:** Die Dimension des Zeilenraums ist gleich dem [[Rang]] der Matrix $A$. $\dim(\operatorname{Row}(A)) = rg(A)$.
* Der [[Rang]] des Zeilenraums ist immer gleich dem [[Rang]] des [[Spaltenraum|Spaltenraums]].
* Eine [[Basis]] für den Zeilenraum kann gefunden werden, indem man die **Nicht-Null-Zeilen** in der [[Zeilenstufenform (ZSF)]] oder [[Reduzierte Zeilenstufenform (RZF)]] der Matrix $A$ wählt.
* **[[CR-Zerlegung]]:** Bei der [[CR-Zerlegung]] $A=CR$ bilden die Zeilen der Matrix $R$ eine [[Basis]] für den Zeilenraum von $A$.

Der Zeilenraum beschreibt den Teil des Zielraums, der von den Zeilen der Matrix "erreicht" werden kann.

---

## Verwendung:

```dataview
list from [[Zeilenraum]]
```