#Note

2025-05-18

Tags: [[Gram-Schmidt-Verfahren]], [[Orthogonalität]], [[Orthonormalität]], [[Basis]], [[Vektorräume]], [[Lineare Algebra]], [[Inneres Produkt]], [[Norm]], [[Lineare Unabhängigkeit]], [[QR-Zerlegung]]

---

Das **Gram-Schmidt-Verfahren** ist ein Algorithmus, der verwendet wird, um aus einer gegebenen Menge von [[Lineare Unabhängigkeit|linear unabhängigen]] [[Vektoren]] in einem [[Vektorräume|Vektorraum]] mit [[Inneres Produkt|Innerem Produkt]] eine **[[Orthogonalität|orthogonale]]** oder **[[Orthonormalität|orthonormale]] Menge** von [[Vektoren]] zu konstruieren, die denselben [[Spann (Lineare Hülle)|Unterraum]] aufspannt. Wenn die ursprüngliche Menge eine [[Basis]] war, ist die resultierende Menge eine [[Basis|orthogonale]] oder [[Basis|orthonormale Basis]] für denselben [[Unterraum]].

**Die Idee:**

Das Verfahren funktioniert, indem es die gegebenen [[Vektoren]] nacheinander durchgeht. Jeder neue Vektor wird so modifiziert, dass er orthogonal zu allen zuvor konstruierten orthogonalen Vektoren ist. Dies geschieht, indem man die Projektionen des aktuellen Vektors auf die bereits konstruierten orthogonalen Vektoren subtrahiert. Für eine orthonormale Menge werden die Vektoren am Ende (oder schrittweise) normiert.

**Schritte zur Konstruktion einer orthonormalen Menge aus einer linear unabhängigen Menge $\{v_1, v_2, \dots, v_k\}$:**

1.  **Normiere den ersten Vektor:**
    $$ u_1 = \frac{v_1}{||v_1||} $$
    ($u_1$ hat jetzt [[Norm]] 1)
2.  **Mache den zweiten Vektor orthogonal zu $u_1$ und normiere ihn:**
    Subtrahiere die Projektion von $v_2$ auf $u_1$ von $v_2$:
    $$ v_2' = v_2 - \langle v_2, u_1 \rangle u_1 $$
    Normiere $v_2'$:
    $$ u_2 = \frac{v_2'}{||v_2'||} $$
    ($u_2$ ist jetzt orthogonal zu $u_1$ und hat [[Norm]] 1)
3.  **Mache den dritten Vektor orthogonal zu $u_1$ und $u_2$ und normiere ihn:**
    Subtrahiere die Projektionen von $v_3$ auf $u_1$ und $u_2$ von $v_3$:
    $$ v_3' = v_3 - \langle v_3, u_1 \rangle u_1 - \langle v_3, u_2 \rangle u_2 $$
    Normiere $v_3'$:
    $$ u_3 = \frac{v_3'}{||v_3'||} $$
    ($u_3$ ist jetzt orthogonal zu $u_1$ und $u_2$ und hat [[Norm]] 1)
4.  **Wiederhole für $i = 4, \dots, k$:**
    Subtrahiere die Projektionen von $v_i$ auf alle vorherigen orthonormalen Vektoren $u_1, \dots, u_{i-1}$:
    $$ v_i' = v_i - \sum_{j=1}^{i-1} \langle v_i, u_j \rangle u_j $$
    Normiere $v_i'$:
    $$ u_i = \frac{v_i'}{||v_i'||} $$

Die resultierende Menge $ \{u_1, u_2, \dots, u_k\} $ ist eine orthonormale Menge. Wenn nur eine orthogonale Menge gewünscht ist, lässt man den Normierungsschritt weg und verwendet $v_i'$ (oder skaliert sie beliebig).

**Voraussetzung:**

Das Verfahren erfordert, dass die ursprüngliche Menge von [[Vektoren]] **[[Lineare Unabhängigkeit|linear unabhängig]]** ist.

**Verbindung zur [[QR-Zerlegung]]:**

Das Gram-Schmidt-Verfahren kann zur [[Berechnung]] der [[QR-Zerlegung]] einer Matrix $A=QR$ verwendet werden. Die Spalten der Matrix $Q$ (die eine [[Orthogonale Matrix|orthogonale Matrix]] ist) werden durch Anwendung von Gram-Schmidt auf die Spalten von $A$ konstruiert, und $R$ ist eine obere [[Dreiecksmatrix]].

---

## Verwendung:

```dataview
list from [[Gram-Schmidt-Verfahren]]
```