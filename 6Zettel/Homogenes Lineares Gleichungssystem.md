#Note

2025-05-17

Tags: [[Homogenes Lineares Gleichungssystem]], [[Lineare Gleichungssysteme]], [[Vektorräume]], [[Unterraum]], [[Kern]], [[Lösbarkeit]], [[Matrizen]], [[Lineare Algebra]]

---

Ein **Homogenes [[Lineares Gleichungssystem|Lineares Gleichungssystem]]** ist ein [[Lineares Gleichungssystem|LGS]] der Form $A\vec{x} = \vec{b}$, bei dem der Vektor der rechten Seiten $\vec{b}$ der [[Nullvektor]] $\vec{0}$ ist.

Die allgemeine Form ist also:

$$A\vec{x} = \vec{0}$$

**Eigenschaften:**

* Ein homogenes [[Lineares Gleichungssystem|LGS]] ist **immer lösbar**. Eine offensichtliche Lösung ist der **triviale Nullvektor** $\vec{x} = \vec{0}$.
* Die Menge aller Lösungen eines homogenen [[Lineares Gleichungssystem|LGS]] bildet den **[[Kern (Nullraum)|Kern]]** (oder Nullraum) der [[Matrizen|Matrix]] $A$. Der [[Kern (Nullraum)|Kern]] ist immer ein [[Vektorräume|Unterraum]] des [[Vektorräume|Vektorraums]], aus dem die Lösungsvektoren $\vec{x}$ stammen.
* Die Struktur der [[Lösbarkeit]] (genau eine Lösung vs. unendlich viele Lösungen) hängt vom [[Rang]] der Matrix $A$ und der Anzahl der Variablen ab. Wenn $rg(A) = n$ (Anzahl der Variablen), ist $\vec{x} = \vec{0}$ die einzige Lösung. Wenn $rg(A) < n$, gibt es unendlich viele Lösungen (den [[Kern (Nullraum)|Kern]] mit Dimension $n - rg(A)$).
* Das homogene [[Lineares Gleichungssystem|LGS]] $A\vec{x} = \vec{0}$ spielt eine zentrale Rolle bei der Beschreibung der **allgemeinen Lösung** eines *nicht-homogenen* [[Lineares Gleichungssystem|LGS]] ($A\vec{x} = \vec{b}$, $\vec{b} \neq \vec{0}$). Die allgemeine Lösung des nicht-homogenen Systems ist die Summe einer partikulären Lösung des nicht-homogenen Systems und der allgemeinen Lösung des zugehörigen homogenen Systems.

---

## Verwendung:

```dataview
list from [[Homogenes Lineares Gleichungssystem]]
```