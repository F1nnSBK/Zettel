#Note

2025-05-17

Tags: [[Spaltenraum]], [[Bildmenge]], [[Matrizen]], [[Lineare Algebra]], [[Vektorräume]], [[Unterraum]], [[Rang]], [[Basis]], [[Lineare Gleichungssysteme]], [[Lösbarkeit]], [[CR-Zerlegung]]

---

Der **Spaltenraum** einer [[Matrizen|Matrix]] $A$ (oft notiert als $\operatorname{Col}(A)$ oder $\operatorname{Im}(A)$) ist die Menge aller möglichen [[Linearkombinationen|Linearkombinationen]] der Spaltenvektoren von $A$. Er wird auch als **Bildmenge** oder **Bildraum** der Matrix $A$ bezeichnet.

**Definition:**

Für eine $m \times n$ Matrix $A$ mit Spaltenvektoren $\vec{a}_1, \vec{a}_2, \dots, \vec{a}_n$ ist der Spaltenraum definiert als:

$$ \operatorname{Col}(A) = \{ c_1 \vec{a}_1 + c_2 \vec{a}_2 + \dots + c_n \vec{a}_n \mid c_1, c_2, \dots, c_n \in \mathbb{R} \} $$

Der Spaltenraum ist ein [[Vektorräume|Unterraum]] von $\mathbb{R}^m$.

**Eigenschaften und Bedeutung:**

* Jeder Vektor, der durch die Multiplikation der Matrix $A$ mit einem beliebigen Vektor $\vec{v}$ entsteht ($A\vec{v}$), liegt im Spaltenraum von $A$: $A\vec{v} \in \operatorname{Col}(A)$.
* **[[Lösbarkeit]] von [[Lineare Gleichungssysteme|LGS]]:** Ein [[Lineare Gleichungssysteme|LGS]] $A\vec{x} = \vec{b}$ ist genau dann lösbar, wenn der Vektor der rechten Seiten $\vec{b}$ im Spaltenraum von $A$ liegt ($\vec{b} \in \operatorname{Col}(A)$).
* **[[Rang]]:** Die Dimension des Spaltenraums ist gleich dem [[Rang]] der Matrix $A$. $\dim(\operatorname{Col}(A)) = rg(A)$.
* Eine [[Basis]] für den Spaltenraum kann gefunden werden, indem man die Spalten der ursprünglichen Matrix $A$ auswählt, die den [[Pivotelement|Pivot]]spalten in der [[Zeilenstufenform]] oder [[Reduzierte Zeilenstufenform (RZF)]] von $A$ entsprechen.
* **[[CR-Zerlegung]]:** Bei der [[CR-Zerlegung]] $A=CR$ bilden die Spalten der Matrix $C$ eine [[Basis]] für den Spaltenraum von $A$.

---

## Verwendung:

```dataview
list from [[Spaltenraum]]
```