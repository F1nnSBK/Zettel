#Note
2025-05-15

Tags: [[Koordinatenform]], [[Ebenen]], [[Vektoren]], [[Normalenvektor]], [[Analytische Geometrie]]

---

Die Koordinatenform ist eine Möglichkeit, geometrische Objekte wie [[Ebenen]] im Raum durch eine Gleichung darzustellen, die die Koordinaten ($x_1, x_2, x_3$) der Punkte auf dem Objekt direkt verwendet. Sie steht im Gegensatz zur [[Parameterdarstellung]], die Vektoren und Parameter nutzt.

**Formel (für eine Ebene im $\mathbb{R}^3$):**

Die Koordinatenform einer Ebene ist eine lineare Gleichung der Form:
$$n_1 x_1 + n_2 x_2 + n_3 x_3 = n_0$$
Diese Gleichung kann auch als Skalarprodukt eines Vektors $\vec{n}$ mit dem Ortsvektor $\vec{x} = \begin{pmatrix} x_1 \\ x_2 \\ x_3 \end{pmatrix}$ zum Punkt $(x_1, x_2, x_3)$ geschrieben werden:
$$\vec{n} \cdot \vec{x} = n_0$$

**Komponenten:**

* $\vec{n} = \begin{pmatrix} n_1 \\ n_2 \\ n_3 \end{pmatrix}$ ist der **Normalenvektor** der Ebene. Dieser Vektor steht senkrecht (orthogonal) auf der Ebene. (Siehe auch [[Normalenvektor]])
* $n_0$ ist ein Skalar, der die Lage der Ebene relativ zum Ursprung bestimmt.

**Herleitung aus der Parameterdarstellung (für Ebenen):**

Wenn eine Ebene in Parameterdarstellung $\vec{x} = \vec{p} + \lambda \cdot \vec{q} + \mu \cdot \vec{r}$ gegeben ist, kann die Koordinatenform wie folgt gefunden werden:
1.  Bestimme den Normalenvektor $\vec{n}$ durch das [[Kreuzprodukt]] der Richtungsvektoren (im $\mathbb{R}^3$):
    $$\vec{n} = \vec{q} \times \vec{r}$$
2.  Setze den Normalenvektor und einen Punkt auf der Ebene (z.B. den Endpunkt des Stützvektors $\vec{p}$) in die Gleichung $\vec{n} \cdot \vec{x} = n_0$ ein, um $n_0$ zu berechnen:
    $$n_0 = \vec{n} \cdot \vec{p}$$
    Die resultierende Gleichung $n_1 x_1 + n_2 x_2 + n_3 x_3 = n_0$ ist die Koordinatenform.

**Vergleich mit Parameterdarstellung:**

Während die Parameterdarstellung ideal ist, um Punkte auf dem Objekt zu erzeugen, ist die Koordinatenform oft nützlicher, um zu überprüfen, ob ein gegebener Punkt auf dem Objekt liegt (indem man seine Koordinaten in die Gleichung einsetzt).

---

## Verwendung:

```dataview
list from [[Koordinatenform]]
```