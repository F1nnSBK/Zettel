#Note

2025-05-17

Tags: [[Cholesky-Zerlegung]], [[Matrixzerlegung]], [[Matrizen]], [[Lineare Algebra]], [[Symmetrische Matrix]], [[Definitheit (Matrizen)]], [[Dreiecksmatrix]], [[Lineare Gleichungssysteme]], [[LU-Zerlegung]], [[Lineare Regression]], [[Normalengleichung]]

---

Die **Cholesky-Zerlegung** ist eine [[Matrixzerlegung|Matrixzerlegung]], die nur für **[[Symmetrische Matrix|symmetrische]]** und **[[Definitheit (Matrizen)|positiv definite]]** [[Quadratische Matrix|quadratische Matrizen]] $A$ angewendet werden kann. Sie zerlegt die Matrix $A$ in das Produkt einer unteren [[Dreiecksmatrix]] $L$ und ihrer [[Transponieren|Transponierten]] $L^T$.

**Definition:**

Eine [[Symmetrische Matrix|symmetrische]] und [[Definitheit (Matrizen)|positiv definite]] Matrix $A$ kann zerlegt werden als:

$$A = L L^T$$

Dabei ist $L$ eine untere [[Dreiecksmatrix]] mit positiven Einträgen auf der Hauptdiagonale. Manchmal wird die Zerlegung auch als $A = U^T U$ geschrieben, wobei $U = L^T$ eine obere Dreiecksmatrix ist.

**Voraussetzungen:**

Die Cholesky-Zerlegung existiert genau dann, wenn die Matrix $A$ **[[Symmetrische Matrix|symmetrisch]]** ($A = A^T$) und **[[Definitheit (Matrizen)|positiv definit]]** ist (d.h., alle [[Eigenwerte]] von $A$ sind positiv).

**Bestimmung von L:**

Die Elemente der Matrix $L$ können direkt mit spezifischen Formeln berechnet werden, die auf elementaren Operationen basieren, ähnlich wie bei einer spezialisierten Form des [[Gauß-Algorithmus]].

**Nutzen der Cholesky-Zerlegung:**

Die Cholesky-Zerlegung ist rechnerisch sehr effizient und numerisch stabil für die Matrizen, für die sie anwendbar ist:

* **Lösen von [[Lineare Gleichungssysteme|LGS]]:** Ähnlich wie bei der [[LU-Zerlegung]], kann ein [[Lineare Gleichungssysteme|LGS]] $A\vec{x} = \vec{b}$ durch $LL^T\vec{x} = \vec{b}$ ersetzt und in zwei Schritte zerlegt werden:
    1.  Löse $L\vec{y} = \vec{b}$ nach $\vec{y}$ durch Vorwärtseinsetzen.
    2.  Löse $L^T\vec{x} = \vec{y}$ nach $\vec{x}$ durch Rückwärtseinsetzen.
    Dies ist besonders schnell, da $L^T$ ebenfalls eine Dreiecksmatrix ist.
* **Anwendung in der [[Lineare Regression|Linearen Regression]]:** Die Cholesky-Zerlegung ist sehr nützlich zur Lösung der **[[Normalengleichung]]** $X^T X \vec{c} = X^T \vec{y}$. Die Matrix $X^T X$ ist immer [[Symmetrische Matrix|symmetrisch]] und ist [[Definitheit (Matrizen)|positiv definit]] (und somit invertierbar), wenn die [[Designmatrix]] $X$ vollen Spaltenrang hat. Daher kann $X^T X = LL^T$ zerlegt und die [[Normalengleichung]] effizient gelöst werden durch $L\vec{y} = X^T\vec{y}$ gefolgt von $L^T\vec{c}=\vec{y}$.
* **[[Optimierung|Optimierung]] und Simulation:** Die Cholesky-Zerlegung findet Anwendung in verschiedenen Bereichen wie der [[Optimierung|Optimierung]], Finanzmathematik und Monte-Carlo-Simulationen.

---

## Verwendung:

```dataview
list from [[Cholesky-Zerlegung]]
```