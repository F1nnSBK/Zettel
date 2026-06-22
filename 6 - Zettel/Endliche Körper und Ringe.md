#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Kryptographie]], [[Mathematik]]
#it_security

---

### Endliche Körper und Ringe

In der fortgeschrittenen Kryptographie (z. B. bei [[AES]] oder klassischer Verschlüsselung wie der Affinen Chiffre) werden mathematische Strukturen wie **Ringe** und **Endliche Körper (Galois-Körper)** verwendet.

---

#### 1. Endliche Körper / Galois-Körper ($GF(q)$)
Ein Körper ist eine algebraische Struktur, in der Addition, Subtraktion, Multiplikation und Division (außer durch Null) möglich sind. Ein Körper mit einer endlichen Anzahl von Elementen heißt **Galois-Körper** (Galois Field, $GF(q)$).
* **Elementezahl ($q$)**: Die Anzahl der Elemente in einem endlichen Körper ist immer eine Primzahlpotenz: $q = p^n$ (wobei $p$ eine Primzahl und $n \ge 1$ eine natürliche Zahl ist).
* **GF(2)**: Der kleinste Körper. Enthält nur $\{0, 1\}$. Addition entspricht der XOR-Operation, Multiplikation der AND-Operation.
* **GF($2^8$)**: Wird in [[AES]] verwendet. Jedes Byte wird als Polynom vom Grad $< 8$ interpretiert. Addition ist bitweises XOR; Multiplikation erfolgt modulo eines irreduziblen Polynoms (z. B. $P(x) = x^8 + x^4 + x^3 + x + 1$).

---

#### 2. Das multiplikative Inverse
In einem Ring oder Körper ist das multiplikative Inverse zu $a$ modulo $m$ diejenige Zahl $x$, für die gilt:
$$a \cdot x \equiv 1 \pmod m \quad (\text{geschrieben als } a^{-1})$$

##### Existenzbedingung
Das multiplikative Inverse $a^{-1}$ modulo $m$ existiert **genau dann, wenn** $a$ und $m$ teilerfremd sind:
$$\text{ggT}(a, m) = 1$$

##### Berechnung: Der Erweiterte Euklidische Algorithmus (EEA)
Zur effizienten Berechnung des Inversen wird der **Erweiterte Euklidische Algorithmus** genutzt. Er liefert Koeffizienten $x$ und $y$, sodass gilt:
$$a \cdot x + m \cdot y = \text{ggT}(a, m) = 1$$
Modulo $m$ gerechnet fällt der Term $m \cdot y$ weg, und es bleibt:
$$a \cdot x \equiv 1 \pmod m \implies x = a^{-1} \pmod m$$

**Verknüpfte Zettel:**
- [[Matrizen]] (Kalkulationen in linearen Systemen über Körpern)

---
#### Flashcards

Unter welcher Bedingung existiert das multiplikative Inverse $a^{-1}$ modulo $m$?::Wenn $a$ und $m$ teilerfremd sind, das heißt: $\text{ggT}(a, m) = 1$.

Welches Verfahren dient zur Berechnung des multiplikativen Inversen modulo $m$?::Der Erweiterte Euklidische Algorithmus (EEA).

Warum wird in AES der Körper $GF(2^8)$ und nicht der Ring $\mathbb{Z}_{256}$ verwendet?::Weil $\mathbb{Z}_{256}$ kein Körper ist (256 ist keine Primzahl). Viele Elemente in $\mathbb{Z}_{256}$ besitzen kein multiplikatives Inverses, was für die Entschlüsselung notwendig ist. In $GF(2^8)$ besitzt jedes Element ungleich Null ein Inverses.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Endliche Körper und Ringe]]
SORT file.mtime DESC
```
