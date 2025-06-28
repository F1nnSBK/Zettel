#Note
2025-05-15

Tags: [[Geraden]], [[Vektoren]], [[Analytische Geometrie]], [[Lineare Algebra]]

---

Geraden im Raum können mithilfe von Vektoren beschrieben werden, typischerweise durch die Parameterdarstellung.

**Parameterdarstellung einer Geraden:**

Eine Gerade G kann beschrieben werden durch die Gleichung:
$$\vec{x} = \vec{p} + \lambda \cdot \vec{q}, \quad \lambda \in \mathbb{R}$$

Dabei gilt:
* $\vec{x}$ ist der Ortsvektor zu einem beliebigen Punkt auf der Geraden.
* $\vec{p}$ ist der **Stützvektor** (oder Ortsvektor), der zu einem bekannten Punkt auf der Geraden zeigt.
* $\vec{q}$ ist der **Richtungsvektor**, der die Richtung der Geraden angibt.
* $\lambda$ (Lambda) ist ein **Parameter** (ein Skalar), der die "Schrittweite" entlang des Richtungsvektors vom Stützvektor aus bestimmt. Durch Variieren von $\lambda$ erhält man alle Punkte auf der Geraden.

**Gerade durch zwei Punkte:**

Eine Gerade durch zwei gegebene Punkte $P_1$ und $P_2$ mit den Ortsvektoren $\vec{p}_1$ und $\vec{p}_2$ kann ebenfalls in Parameterdarstellung angegeben werden. Wir können einen der Punktvektoren als Stützvektor wählen (z.B. $\vec{p}_1$) und der Vektor von $P_1$ nach $P_2$ dient als Richtungsvektor:
$$\vec{x} = \vec{p}_1 + \lambda \cdot (\vec{p}_2 - \vec{p}_1), \quad \lambda \in \mathbb{R}$$
Hierbei ist $\vec{p}_2 - \vec{p}_1$ der Richtungsvektor $\vec{P_1 P_2}$.

---

## Verwendung:

```dataview
list from [[Geraden]]
```