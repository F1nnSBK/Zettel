#Note

2025-05-18

Tags: [[Metrik]], [[Distanzfunktion]], [[Vektorräume]], [[Norm]], [[Lineare Algebra]], [[Analytische Geometrie]]

---

Eine **Metrik**, auch **Distanzfunktion** genannt, ist eine Funktion, die jedem Paar von Elementen in einer Menge eine nicht-negative Zahl zuordnet. Diese Zahl repräsentiert den "Abstand" oder die "Distanz" zwischen den beiden Elementen.

**Definition:**

Eine Funktion $d: V \times V \to \mathbb{R}$ auf einer Menge $V$ (oft einem [[Vektorräume|Vektorraum]]) ist eine Metrik, wenn sie für alle $v, w, u \in V$ die folgenden vier [[Eigenschaften]] (Axiome) erfüllt:

1.  **Nicht-Negativität:** Die Distanz ist immer größer oder gleich Null.
    $$ d(v, w) \ge 0 $$
2.  **Identität des Ununterscheidbaren:** Die Distanz ist genau dann Null, wenn die Elemente identisch sind.
    $$ d(v, w) = 0 \iff v = w $$
3.  **Symmetrie:** Die Distanz von $v$ nach $w$ ist die gleiche wie von $w$ nach $v$.
    $$ d(v, w) = d(w, v) $$
4.  **Dreiecksungleichung:** Der direkte Weg ist nie länger als ein Umweg über einen dritten Punkt.
    $$ d(v, w) \le d(v, u) + d(u, w) $$

Eine Menge $V$ zusammen mit einer Metrik $d$ heißt **metrischer Raum** $(V, d)$.

**Verbindung zur [[Norm]]:**

Jede [[Norm]] $|| \cdot ||$ auf einem [[Vektorräume|Vektorraum]] $V$ **induziert** eine Metrik $d$ auf $V$, definiert durch die [[Norm]] der Differenz zwischen zwei [[Vektoren]]:

$$ d(v, w) = ||v - w|| $$

Ein [[Vektorräume|Vektorraum]] mit einer definierten [[Norm]] wird als **normierter Raum** bezeichnet. Da jede [[Norm]] eine Metrik induziert, ist jeder normierte Raum auch ein metrischer Raum.

---

## Verwendung:

```dataview
list from [[Metrik]]
```