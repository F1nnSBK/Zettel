#Note

2025-05-15

Tags: [[Rang]], [[Matrizen]], [[Lineare Algebra]], [[Lineare Gleichungssysteme]], [[Lösbarkeit]], [[Zeilenstufenform]], [[Reduzierte Zeilenstufenform]], [[Lineare Unabhängigkeit]], [[Vektorräume]]

---

Der **Rang** einer [[Matrizen|Matrix]] A, notiert als $rg(A)$, ist ein Skalarwert, der die maximale Anzahl **[[Lineare Unabhängigkeit|linear unabhängiger]] Zeilenvektoren** oder **Spaltenvektoren** in der Matrix angibt.

**[[Berechnung]] des Rangs:**

Der Rang einer Matrix wird typischerweise mithilfe des [[Gauß-Algorithmus]] bestimmt. Man bringt die Matrix durch elementare Zeilenumformungen in die [[Zeilenstufenform]] (ZSF) oder [[Reduzierte Zeilenstufenform]] (RZF).

Der Rang der Matrix entspricht dann der **Anzahl der Nicht-Null-Zeilen** in ihrer [[Zeilenstufenform]]. Dies ist gleich der Anzahl der Pivotelemente.

**Bedeutung des Rangs:**

Der Rang ist entscheidend für die [[Lösbarkeit]] und die Anzahl der Lösungen von [[Lineare Gleichungssysteme|Linearen Gleichungssystemen]] ($A\vec{x} = \vec{b}$).

* Ein LGS ist lösbar, wenn $rg(A) = rg(A|\vec{b})$.
* Es gibt genau eine Lösung, wenn $rg(A) = rg(A|\vec{b}) = n$ (Anzahl der Variablen).
* Es gibt unendlich viele Lösungen, wenn $rg(A) = rg(A|\vec{b}) < n$.

Der Rang einer Matrix ist auch gleich der [[Dimension]] des **Spaltenraums** (Bildraum, $Im(A)$) und der [[Dimension]] des **Zeilenraums** der Matrix. Er gibt an, wie viele Dimensionen der durch die Matrix aufgespannte Raum hat.

Für eine $m \times n$ Matrix A gilt immer $rg(A) \le \min(m, n)$. Eine Matrix hat **vollen Rang**, wenn $rg(A) = \min(m, n)$.

---

## Verwendung:

```dataview
list from [[Rang]]
```