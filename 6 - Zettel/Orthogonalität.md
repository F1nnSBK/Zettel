#Note

2025-05-18

Tags: [[Orthogonalität]], [[Vektorräume]], [[Lineare Algebra]], [[Inneres Produkt]], [[Orthonormalität]], [[Basis]], [[Gram-Schmidt-Verfahren]], [[Orthogonale Matrix]]

---

**Orthogonalität** beschreibt die Eigenschaft von [[Vektoren]] in einem [[Vektorräume|Vektorraum]] mit [[Inneres Produkt|Innerem Produkt]], **senkrecht** zueinander zu stehen.

**Definition für zwei [[Vektoren]]:**

Zwei [[Vektoren]] $v$ und $w$ in einem Inneren Produktraum sind **orthogonal**, wenn ihr [[Inneres Produkt]] gleich Null ist:

$$ \langle v, w \rangle = 0 $$

Der [[Nullvektor]] $\vec{0}$ ist orthogonal zu jedem Vektor.

**Definition für eine Menge von [[Vektoren]]:**

Eine Menge von [[Vektoren]] $ \{v_1, v_2, \dots, v_k\} $ ist eine **orthogonale Menge**, wenn jeder Vektor der Menge orthogonal zu jedem anderen **verschiedenen** Vektor in der Menge ist:

$$ \langle v_i, v_j \rangle = 0 \quad \text{für alle } i \neq j $$

**Bedeutung:**

* Jede orthogonale Menge von Vektoren, die nicht den [[Nullvektor]] enthält, ist **[[Lineare Unabhängigkeit|linear unabhängig]]**. Dies ist eine sehr nützliche Eigenschaft.
* Orthogonale [[Basis|Basen]] vereinfachen viele Berechnungen, wie z.B. die Darstellung eines Vektors als [[Linearkombinationen|Linearkombination]] der [[Basis|Basisvektoren]].

**Verbindungen zu anderen Konzepten:**

* **[[Inneres Produkt]]:** Ist die Grundlage für die Definition von Orthogonalität.
* **[[Orthonormalität]]:** Eine orthogonale Menge, bei der jeder Vektor zusätzlich die [[Norm]] 1 hat, ist eine orthonormale Menge.
* **[[Basis|Orthogonale Basis]]:** Eine [[Basis]], die eine orthogonale Menge ist.
* **[[Gram-Schmidt-Verfahren]]:** Ein Algorithmus, um aus einer Menge linear unabhängiger Vektoren eine orthogonale (oder orthonormale) Menge bzw. Basis zu konstruieren.
* **[[Orthogonale Matrix]]:** Eine [[Quadratische Matrix|quadratische Matrix]], deren Spalten- (und Zeilen-)vektoren eine orthonormale Menge bilden (und somit auch eine orthogonale Menge).

Orthogonalität ist ein Schlüsselkonzept, das in vielen mathematischen und angewandten Bereichen verwendet wird, um Unabhängigkeit und Struktur zu beschreiben.

---

## Verwendung:

```dataview
list from [[Orthogonalität]]
```