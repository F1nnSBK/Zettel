#Note

2025-05-17

Tags: [[Eigenvektoren]], [[Eigenwerte]], [[Lineare Algebra]], [[Matrizen]], [[Vektoren]], [[Homogenes Lineares Gleichungssystem]], [[Eigenspace]]

---

Ein **Eigenvektor** einer [[Quadratische Matrix|quadratischen Matrix]] $A$ ist ein Vektor $\vec{x} \neq \vec{0}$, der bei Multiplikation mit $A$ lediglich skaliert (gestreckt oder gestaucht) wird, aber seine Richtung nicht ändert (er bleibt auf derselben Geraden durch den Ursprung). Der Skalierungsfaktor wird als zugehöriger [[Eigenwerte|Eigenwert]] $\lambda$ bezeichnet.

**Definition (Charakteristische Gleichung):**

Ein Vektor $\vec{x} \in \mathbb{R}^n$, $\vec{x} \neq \vec{0}$, ist ein Eigenvektor der $n \times n$ Matrix $A$, wenn es einen [[Skalar]] $\lambda$ gibt, sodass gilt:

$$A\vec{x} = \lambda\vec{x}$$

Diese Gleichung wird oft als **Charakteristische Gleichung** bezeichnet. Der Skalar $\lambda$ ist der zugehörige [[Eigenwerte|Eigenwert]].

**Eigenschaften von Eigenvektoren:**

* Jedes Vielfache $c\vec{x}$ (mit $c \in \mathbb{R}, c \neq 0$) eines Eigenvektors $\vec{x}$ zum Eigenwert $\lambda$ ist selbst wieder ein Eigenvektor zum selben Eigenwert $\lambda$. Eigenvektoren spannen somit eine "Eigenrichtung" auf.
* Wenn $A$ eine [[Symmetrische Matrix|symmetrische Matrix]] ist, dann sind Eigenvektoren zu verschiedenen [[Eigenwerte|Eigenwerten]] orthogonal zueinander.
* Wenn $\vec{x}$ ein Eigenvektor von $A$ zum Eigenwert $\lambda$ ist, dann ist $\vec{x}$ auch ein Eigenvektor von $A + \gamma E$ zum Eigenwert $\lambda + \gamma$ (für jedes $\gamma \in \mathbb{R}$ und die [[Einheitsmatrix]] $E$).
* Wenn $A$ [[Invertierbarkeit|invertierbar]] ist und $\vec{x}$ ein Eigenvektor von $A$ zum Eigenwert $\lambda$ ($\lambda \neq 0$, da invertierbar), dann ist $\vec{x}$ auch ein Eigenvektor von $A^{-1}$ zum Eigenwert $\lambda^{-1}$.
* Wenn $\vec{x}$ ein Eigenvektor von $A$ zum Eigenwert $\lambda$ ist, dann ist $A^k \vec{x} = \lambda^k \vec{x}$ für jede ganze Zahl $k \in \mathbb{Z}$ (sofern $A^k$ definiert ist).

**Berechnung von Eigenvektoren:**

Die Berechnung der Eigenvektoren erfolgt, nachdem die zugehörigen [[Eigenwerte|Eigenwerte]] $\lambda$ bekannt sind (siehe Notiz zu [[Eigenwerte]]):

1.  Für jeden gefundenen [[Eigenwerte|Eigenwert]] $\lambda$ muss das folgende **[[Homogenes Lineares Gleichungssystem]]** gelöst werden:

    $$(A - \lambda I)\vec{x} = \vec{0}$$

    wobei $I$ die [[Einheitsmatrix]] der gleichen Dimension wie $A$ ist.

2.  Man löst dieses [[Homogenes Lineares Gleichungssystem]] typischerweise mithilfe des [[Gauß-Algorithmus]], indem man die erweiterte Matrix $(A - \lambda I | \vec{0})$ in [[Reduzierte Zeilenstufenform (RZF)]] bringt.
3.  Die Lösungsmenge dieses Systems für ein gegebenes $\lambda$ bildet den zugehörigen **[[Eigenspace|Eigenraum]]** (oder [[Kern (Nullraum)|Kern]] von $A - \lambda I$). Jeder Vektor in diesem [[Eigenspace|Eigenraum]] (außer dem [[Nullvektor]]) ist ein Eigenvektor zum Eigenwert $\lambda$.

Der [[Eigenspace|Eigenraum]] für einen Eigenwert $\lambda$ ist immer ein [[Vektorräume|Unterraum]].

---

## Verwendung:

```dataview
list from [[Eigenvektoren]]
```