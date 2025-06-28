#Note

2025-05-15

Tags: [[Linearkombinationen]], [[Vektoren]], [[Skalar]], [[Lineare Algebra]], [[Spann (Lineare Hülle)]], [[Basis]], [[Vektorräume]], [[Lineare Unabhängigkeit]]

---

Eine **Linearkombination** einer Menge von [[Vektoren]] ist ein Ausdruck, der durch die Multiplikation jedes [[Vektoren|Vektors]] mit einem [[Skalar]] und die anschließende Addition der Ergebnisse gebildet wird.

**Definition:**

Gegeben seien eine Menge von [[Vektoren]] $\{\vec{v}_1, \vec{v}_2, \dots, \vec{v}_k\}$ aus einem [[Vektorräume|Vektorraum]] und eine Menge von [[Skalar|Skalaren]] $\{c_1, c_2, \dots, c_k\}$ aus dem zugehörigen Körper (meist $\mathbb{R}$). Eine Linearkombination dieser [[Vektoren]] ist der Vektor:

$$ c_1 \vec{v}_1 + c_2 \vec{v}_2 + \dots + c_k \vec{v}_k = \sum_{i=1}^k c_i \vec{v}_i $$

**Beispiel:**

Gegeben seien die [[Vektoren]] $\vec{a} = \begin{pmatrix} 1 \\ 2 \end{pmatrix}$ und $\vec{b} = \begin{pmatrix} 3 \\ -1 \end{pmatrix}$ und die [[Skalar|Skalare]] $c_1 = 2$ und $c_2 = -3$Eine Linearkombination von $\vec{a}$ und $\vec{b}$ ist:

$$ 2 \cdot \vec{a} + (-3) \cdot \vec{b} = 2 \begin{pmatrix} 1 \\ 2 \end{pmatrix} - 3 \begin{pmatrix} 3 \\ -1 \end{pmatrix} = \begin{pmatrix} 2 \\ 4 \end{pmatrix} - \begin{pmatrix} 9 \\ -3 \end{pmatrix} = \begin{pmatrix} 2 - 9 \\ 4 - (-3) \end{pmatrix} = \begin{pmatrix} -7 \\ 7 \end{pmatrix} $$

**Der [[Spann (Lineare Hülle)|Spann (Lineare Hülle)]]:**

Die Menge **aller möglicher** Linearkombinationen einer gegebenen Menge von [[Vektoren]] wird als deren [[Spann (Lineare Hülle)|Spann]] (oder Lineare Hülle) bezeichnet. Der [[Spann (Lineare Hülle)|Spann]] einer Menge von [[Vektoren]] bildet immer einen [[Vektorräume|Unterraum]] des ursprünglichen [[Vektorräume|Vektorraums]].

**Bedeutung:**

Das Konzept der Linearkombination ist fundamental, da es die Grundlage für viele weitere Konzepte in der [[Lineare Algebra]] bildet, darunter:

* [[Lineare Unabhängigkeit|Lineare (Un-)Abhängigkeit]]: [[Vektoren]] sind linear abhängig, wenn der [[Nullvektor]] als nicht-triviale Linearkombination dargestellt werden kann.
* [[Spann (Lineare Hülle)|Spann]] / Lineare Hülle: Beschreibt alle [[Vektoren]], die aus einer Menge von [[Vektoren]] durch Linearkombinationen erzeugt werden können.
* [[Basis|Basen]]: Eine [[Basis]] ist eine Menge linear unabhängiger [[Vektoren]], die den gesamten [[Vektorräume|Vektorraum]] aufspannen (d.h., jeder Vektor im Raum ist eine Linearkombination der [[Basis|Basisvektoren]]).
* [[Vektorräume|Vektorräume]] / [[Vektorräume|Unterräume]]: Diese Strukturen sind unter Linearkombinationen abgeschlossen.
* [[Lineare Gleichungssysteme|Lösung von LGS]]: Die elementaren Zeilenumformungen basieren auf Linearkombinationen von Zeilen.

---

## Verwendung:

```dataview
list from [[Linearkombinationen]]
```