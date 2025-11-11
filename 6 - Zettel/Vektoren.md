#Note
2025-05-15

Tags: [[Vektoren]], [[Lineare Algebra]], [[3 - Tags/Grundlagen]], [[Operationen]], [[Normen]], [[Geraden]], [[Ebenen]]

---

Ein Vektor ist ein mathematisches Objekt, das sowohl eine Richtung als auch eine Länge (Betrag) besitzt. Vektoren werden oft verwendet, um Verschiebungen im Raum oder Kräfte zu beschreiben.

**Darstellung:**

Vektoren können als Spaltenvektoren oder Zeilenvektoren dargestellt werden:
Spaltenvektor $\vec{a} = \begin{pmatrix} a_1 \\ a_2 \\ \vdots \\ a_n \end{pmatrix}$
Zeilenvektor $\vec{a} = (a_1, a_2, \dots, a_n)$

Durch **Transponieren** ($^T$) wird ein Spaltenvektor zu einem Zeilenvektor und umgekehrt, z.B., wenn $\vec{a} = \begin{pmatrix} a_1 \\ a_2 \end{pmatrix}$, dann ist $\vec{a}^T = (a_1, a_2)$.

Ein **Skalar** ist eine Zahl (z. B. $1, 2, 3.45$), die keine Richtung besitzt.

**Länge (Betrag oder euklidische Distanz):**

Der Betrag eines Vektors $\vec{a}$ ist der Abstand von seinem Ursprung zum Punkt, auf den er zeigt. Er wird mit Betragsstrichen $||$ oder einfachen Strichen $||$ bezeichnet. Die euklidische Distanz in $\mathbb{R}^n$ ist gegeben durch:
$$||\vec{a}|| = \sqrt{a_1^2 + a_2^2 + \dots + a_n^2} = \sqrt{\sum_{i=1}^n a_i^2}$$

**Vektoroperationen:**

* **Multiplikation mit einem Skalar:** Skaliert die Länge des Vektors.
    $$k \cdot \vec{a} = k \cdot \begin{pmatrix} a_1 \\ \vdots \\ a_n \end{pmatrix} = \begin{pmatrix} k \cdot a_1 \\ \vdots \\ k \cdot a_n \end{pmatrix}, \quad k \in \mathbb{R}$$
* **Addition / Subtraktion:** Erfolgt komponentenweise für Vektoren gleicher Dimension.
    $$\vec{a} \pm \vec{b} = \begin{pmatrix} a_1 \\ \vdots \\ a_n \end{pmatrix} \pm \begin{pmatrix} b_1 \\ \vdots \\ b_n \end{pmatrix} = \begin{pmatrix} a_1 \pm b_1 \\ \vdots \\ a_n \pm b_n \end{pmatrix}$$
* **Skalarprodukt (Punktprodukt):** Das Ergebnis ist ein Skalar. Für Vektoren in $\mathbb{R}^n$:
    $$\vec{a}^T \cdot \vec{b} = (a_1, \dots, a_n) \cdot \begin{pmatrix} b_1 \\ \vdots \\ b_n \end{pmatrix} = a_1 b_1 + \dots + a_n b_n = \sum_{i=1}^n a_i b_i$$
    Zwei Vektoren sind orthogonal (senkrecht) zueinander, wenn ihr Skalarprodukt Null ist: $\vec{a}^T \cdot \vec{b} = 0$.
* **Kreuzprodukt:** Ist nur im dreidimensionalen Raum ($\mathbb{R}^3$) definiert. Das Ergebnis ist ein Vektor, der senkrecht auf der Ebene liegt, die von den beiden Vektoren aufgespannt wird (Normalenvektor).
    $$\vec{a} \times \vec{b} = \begin{pmatrix} a_1 \\ a_2 \\ a_3 \end{pmatrix} \times \begin{pmatrix} b_1 \\ b_2 \\ b_3 \end{pmatrix} = \begin{pmatrix} a_2 b_3 - a_3 b_2 \\ a_3 b_1 - a_1 b_3 \\ a_1 b_2 - a_2 b_1 \end{pmatrix}$$

**Normen:**

Eine Norm ist eine Funktion, die einem Vektor einen nicht-negativen Wert zuordnet, der als "Länge" oder "Betrag" interpretiert werden kann ($p(\vec{x}) = ||\vec{x}||$). Eine Norm muss folgende Eigenschaften erfüllen:
1.  **Dreiecksungleichung:** $||\vec{x} + \vec{y}|| \le ||\vec{x}|| + ||\vec{y}||$ für alle $\vec{x}, \vec{y} \in \mathbb{R}^n$.
2.  **Absolute Homogenität:** $||s\vec{x}|| = |s| \cdot ||\vec{x}||$ für alle $\vec{x} \in \mathbb{R}^n$ und $s \in \mathbb{R}$.
3.  **Definitheit:** $||\vec{x}|| = 0$ gilt genau dann, wenn $\vec{x} = \vec{0}$ ist.

Wichtige Normen:
* **p-Norm:** Verallgemeinerung von L1- und L2-Norm.
    $$||\vec{x}||_p = \left( \sum_{i=1}^n |x_i|^p \right)^{\frac{1}{p}}$$
* **L1-Norm (Manhattan-Norm, Taxi-Distanz):** Summe der Beträge der Komponenten.
    $$||\vec{x}||_1 = \sum_{i=1}^n |x_i|$$
* **L2-Norm (euklidische Norm):** Die Standardlänge, identisch mit dem Betrag.
    $$||\vec{x}||_2 = \sqrt{\sum_{i=1}^n |x_i|^2}$$
* **L$\infty$-Norm (Maximum-Norm):** Der größte Betrag einer Komponente.
    $$||\vec{x}||_\infty = \max(|x_1|, |x_2|, \dots, |x_n|)$$

**Linearkombination:**

Eine Linearkombination von Vektoren $\vec{a}_1, \dots, \vec{a}_n$ mit Skalaren $\lambda_1, \dots, \lambda_n$ ist gegeben durch:
$$\sum_{i=1}^n (\lambda_i \cdot \vec{a}_i) = \lambda_1 \vec{a}_1 + \lambda_2 \vec{a}_2 + \dots + \lambda_n \vec{a}_n$$
Die Menge aller möglichen Linearkombinationen einer Vektormenge wird als Lineare Hülle oder Spann bezeichnet.

**Spezielle Vektoren:**

* **Einheitsvektor:** Ein Vektor der Länge 1. Standard-Einheitsvektoren haben eine 1 auf einer Position und sonst 0, z.B. $\vec{e}_3 = \begin{pmatrix} 0 \\ 0 \\ 1 \end{pmatrix}$.
* **Nullvektor:** Ein Vektor, dessen Komponenten alle Null sind, z.B. $\vec{0} = \begin{pmatrix} 0 \\ 0 \end{pmatrix}$.

**Lineare Unabhängigkeit / Abhängigkeit:**

Vektoren $\vec{a}_1, \dots, \vec{a}_n$ sind **linear unabhängig**, wenn die einzige Lösung für die Vektorgleichung
$$\lambda_1 \vec{a}_1 + \lambda_2 \vec{a}_2 + \dots + \lambda_n \vec{a}_n = \vec{0}$$
die triviale Lösung $\lambda_1 = \lambda_2 = \dots = \lambda_n = 0$ ist.
Wenn es auch andere Lösungen gibt, bei denen nicht alle $\lambda_i$ gleich Null sind, dann sind die Vektoren **linear abhängig**.
Geometrisch sind zwei Vektoren linear abhängig, wenn sie parallel (kollinear) sind ($\vec{a} = k \cdot \vec{b}$). Bei mehr als zwei Vektoren sind sie linear abhängig, wenn mindestens einer von ihnen als Linearkombination der anderen dargestellt werden kann.

**Geraden und Ebenen (Parameterdarstellung):**

* **Gerade:** Die Parameterdarstellung einer Geraden im Raum ist gegeben durch:
    $$\vec{x} = \vec{p} + \lambda \cdot \vec{q}, \quad \lambda \in \mathbb{R}$$
    Hierbei ist $\vec{p}$ ein Stützvektor (Ortsvektor zu einem Punkt auf der Geraden) und $\vec{q}$ ein Richtungsvektor. Eine Gerade durch zwei Punkte $P_1$ und $P_2$ hat die Darstellung $\vec{x} = \vec{OP_1} + \lambda \cdot (\vec{p}_2 - \vec{p}_1)$.
* **Ebene:** Die Parameterdarstellung einer Ebene im Raum ist gegeben durch:
    $$\vec{x} = \vec{p} + \lambda \cdot \vec{q} + \mu \cdot \vec{r}, \quad \lambda, \mu \in \mathbb{R}$$
    Hierbei ist $\vec{p}$ ein Stützvektor und $\vec{q}$ sowie $\vec{r}$ sind zwei linear unabhängige Richtungsvektoren, die die Ebene aufspannen.
    Die **Koordinatenform** einer Ebene ist $n_1 x_1 + n_2 x_2 + n_3 x_3 = n_0$. Der Vektor $\vec{n} = \begin{pmatrix} n_1 \\ n_2 \\ n_3 \end{pmatrix}$ ist ein Normalenvektor der Ebene (senkrecht zur Ebene). Er kann durch das Kreuzprodukt der Richtungsvektoren $\vec{q}$ und $\vec{r}$ gefunden werden: $\vec{n} = \vec{q} \times \vec{r}$. Der Wert $n_0$ kann gefunden werden, indem man einen Punkt auf der Ebene (oft den Stützvektor $\vec{p}$) in die Koordinatenform einsetzt: $\vec{n} \cdot \vec{p} = n_0$. $n_0$ beschreibt die Lage der Ebene relativ zum Ursprung.

---

## Verwendung:

```dataview
list from [[Vektoren]]
```