#Note

2025-05-15

Tags: [[Lineare Unabhängigkeit]], [[Vektoren]], [[Lineare Algebra]], [[Rang]], [[Gauß-Algorithmus]], [[Determinante]], [[Invertierbarkeit]], [[Matrizen]], [[Basis]], [[Vektorräume]]

---

**Lineare Unabhängigkeit** ist eine Eigenschaft, die eine Menge von [[Vektoren]] in einem [[Vektorräume|Vektorraum]] haben kann. Eine Menge von [[Vektoren]] $\{\vec{v}_1, \vec{v}_2, \dots, \vec{v}_k\}$ ist **linear unabhängig**, wenn keiner dieser [[Vektoren]] als [[Linearkombinationen|Linearkombination]] der anderen dargestellt werden kann.

**Formale Definition:**

Eine Menge von [[Vektoren]] $\{\vec{v}_1, \vec{v}_2, \dots, \vec{v}_k\}$ ist linear unabhängig, wenn die einzige Möglichkeit, den [[Nullvektor]] $\vec{0}$ als [[Linearkombinationen|Linearkombination]] dieser [[Vektoren]] darzustellen, darin besteht, dass alle Koeffizienten (Skalare) gleich Null sind:

$$ c_1 \vec{v}_1 + c_2 \vec{v}_2 + \dots + c_k \vec{v}_k = \vec{0} \quad \implies \quad c_1 = c_2 = \dots = c_k = 0 $$

Wenn es auch nur eine Lösung gibt, bei der mindestens ein Koeffizient $c_i \neq 0$ ist, dann ist die Menge der [[Vektoren]] **linear abhängig**. Das bedeutet, dass mindestens einer der [[Vektoren]] als [[Linearkombinationen|Linearkombination]] der anderen geschrieben werden kann.

**Test auf [[Lineare Unabhängigkeit]]:**

Um die lineare Unabhängigkeit einer Menge von [[Vektoren]] zu prüfen, kann man diese [[Vektoren]] als Spalten (oder Zeilen) einer [[Matrizen|Matrix]] $A$ anordnen. Die [[Vektoren]] sind genau dann linear unabhängig, wenn der [[Rang]] dieser Matrix $A$ gleich der Anzahl der [[Vektoren]] ist:

$$ \{\vec{v}_1, \dots, \vec{v}_k\} \text{ linear unabhängig} \quad \iff \quad rg(A) = k $$

Der [[Rang]] kann effizient mithilfe des [[Gauß-Algorithmus]] bestimmt werden.

**Verbindungen zu anderen Konzepten:**

* **[[Rang]]:** Der [[Rang]] einer [[Matrizen|Matrix]] ist definiert als die maximale Anzahl linear unabhängiger Zeilenvektoren oder Spaltenvektoren in der Matrix[cite: 20].
* **[[Determinante]] und [[Invertierbarkeit]]:** Für eine [[Quadratische Matrix|quadratische Matrix]] $A$ sind ihre Spaltenvektoren (und auch ihre Zeilenvektoren) genau dann linear unabhängig, wenn die [[Determinante]] von $A$ ungleich Null ist ($\det(A) \neq 0$). Dies ist wiederum äquivalent dazu, dass die Matrix $A$ [[Invertierbarkeit|invertierbar]] ist.
* **[[Basis]]:** Eine Menge von [[Vektoren]] bildet eine [[Basis]] für einen [[Vektorräume|Vektorraum]], wenn sie linear unabhängig ist und den gesamten Raum aufspannt. Die Anzahl der [[Basis|Basisvektoren]] in einer [[Basis]] ist die [[Dimension]] des [[Vektorräume|Vektorraums]].
* **Zerlegungen:** Konzepte wie die CR-Zerlegung einer Matrix basieren darauf, eine Matrix als Produkt von Matrizen darzustellen, die aus linear unabhängigen Spalten- bzw. Zeilenvektoren der ursprünglichen Matrix gebildet werden (deren Anzahl dem [[Rang]] entspricht). Lineare Unabhängigkeit ist somit ein Schlüsselkonzept für viele Matrixfaktorisierungen und das Verständnis der Struktur von [[Matrizen]].

---

## Verwendung:

```dataview
list from [[Lineare Unabhängigkeit]]
```