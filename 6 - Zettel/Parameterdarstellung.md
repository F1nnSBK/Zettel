#Note

2025-05-15

Tags: [[Parameterdarstellung]], [[Vektoren]], [[Geraden]], [[Ebenen]], [[Analytische Geometrie]]

---

Die Parameterdarstellung ist eine Methode in der [[Analytische Geometrie]], um geometrische Objekte wie [[Geraden]], [[Ebenen]] oder Kurven mithilfe von [[Vektoren]] und Parametern zu beschreiben. Sie erlaubt es, jeden Punkt des Objekts durch das Einsetzen spezifischer Werte für die Parameter zu erreichen.

**Grundidee:**

Ein Punkt auf dem geometrischen Objekt wird als Ortsvektor $\vec{x}$ vom Ursprung aus beschrieben. Dieser Ortsvektor setzt sich zusammen aus:
1.  Einem **Stützvektor** $\vec{p}$, der zu einem festen Punkt auf dem Objekt zeigt.
2.  Einer oder mehreren **Richtungsvektoren** $\vec{q}, \vec{r}, \dots$, die die möglichen Bewegungsrichtungen auf dem Objekt vom Stützpunkt aus angeben.
3.  **Parametern** $\lambda, \mu, \dots$, die als Skalare die "Schrittweite" entlang der Richtungsvektoren bestimmen.

**Allgemeine Form (Beispiele):**

* Für eine [[Gerade]] (1-dimensionale Ausdehnung): Man benötigt einen Stützvektor und einen Richtungsvektor, sowie einen Parameter $\lambda$.
    $$\vec{x} = \vec{p} + \lambda \cdot \vec{q}, \quad \lambda \in \mathbb{R}$$
    (Siehe auch Notiz zu [[Geraden]])

* Für eine [[Ebene]] (2-dimensionale Ausdehnung im $\mathbb{R}^3$): Man benötigt einen Stützvektor und zwei linear unabhängige Richtungsvektoren, sowie zwei Parameter $\lambda$ und $\mu$.
    $$\vec{x} = \vec{p} + \lambda \cdot \vec{q} + \mu \cdot \vec{r}, \quad \lambda, \mu \in \mathbb{R}$$
    (Siehe auch Notiz zu [[Ebenen]])

Die Anzahl der benötigten Parameter entspricht der Dimension des geometrischen Objekts (z.B. 1 für eine Linie, 2 für eine Ebene).

Durch das Variieren der Parameter durch alle reellen Zahlen ("Durchlaufen" der Parameter) erhält man alle Punkte, die zu dem beschriebenen geometrischen Objekt gehören.

---

## Verwendung:

```dataview
list from [[Parameterdarstellung]]