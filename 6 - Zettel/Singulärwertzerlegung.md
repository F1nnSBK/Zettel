#Note
2025-05-15

Tags: [[Matrizen]], [[Lineare Algebra]], [[Zerlegung]], [[Eigenwerte]], [[Vektorräume]], [[PCA]], [[LoRA]], [[Diagonalmatrix]], [[Hauptkomponentenanalyse]]

---

Die Singulärwertzerlegung (SVD) ist eine fundamentale Matrixzerlegung, die auf jede beliebige Matrix A angewendet werden kann. Sie liefert tiefe Einblicke in die Struktur der Matrix.

**Formel:**

Eine Matrix A der Dimension $m \times n$ kann zerlegt werden als:
$$A = U \Sigma V^T$$

Dabei gilt:
* $A$ ist die ursprüngliche Matrix der Dimension $m \times n$.
* $U$ ist eine orthogonale Matrix der Dimension $m \times m$. Ihre Spalten sind die linken Singulärvektoren von A.
* $\Sigma$ (Sigma) ist eine $m \times n$ Diagonalmatrix, die die Singulärwerte von A enthält. Die Singulärwerte ($\sigma_i$) stehen auf der Hauptdiagonale in absteigender Reihenfolge ($\sigma_1 \ge \sigma_2 \ge ... \ge \sigma_r > 0$, wobei $r$ der Rang der Matrix ist). Die Singulärwerte sind immer nicht-negativ. Alle Nicht-Diagonalelemente sind Null.
  Die Form von $\Sigma$ hängt von den Dimensionen von A ab:
  Wenn $m > n$:
  $$\Sigma = \begin{pmatrix} \sigma_1 & 0 & \dots & 0 \\ 0 & \sigma_2 & \dots & 0 \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \dots & \sigma_n \\ 0 & 0 & \dots & 0 \\ \vdots & \vdots & \vdots & \vdots \\ 0 & 0 & \dots & 0 \end{pmatrix}_{m \times n}$$
  Wenn $n > m$:
  $$\Sigma = \begin{pmatrix} \sigma_1 & 0 & \dots & 0 & \dots & 0 \\ 0 & \sigma_2 & \dots & 0 & \dots & 0 \\ \vdots & \vdots & \ddots & \vdots & \dots & \vdots \\ 0 & 0 & \dots & \sigma_m & \dots & 0 \end{pmatrix}_{m \times n}$$
  Wenn $m = n$:
  $$\Sigma = \begin{pmatrix} \sigma_1 & 0 & \dots & 0 \\ 0 & \sigma_2 & \dots & 0 \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \dots & \sigma_n \end{pmatrix}_{n \times n}$$
* $V^T$ ist die Transponierte einer orthogonalen Matrix V der Dimension $n \times n$. Ihre Zeilen (bzw. Spalten von V) sind die rechten Singulärvektoren von A. ($V^T$ ist ebenfalls orthogonal).

**Singulärwerte:**

Die Singulärwerte $\sigma_i$ von A sind die Quadratwurzeln der Eigenwerte von $A^T A$ (oder $A A^T$).

**Geometrische Deutung:**

Die SVD zerlegt die durch A dargestellte lineare Transformation in drei grundlegende Schritte:
1.  Eine Rotation (oder Spiegelung) im $n$-dimensionalen Raum, beschrieben durch $V^T$. Orthogonale Matrizen erhalten Längen und Winkel.
2.  Eine Skalierung entlang der Koordinatenachsen, bestimmt durch die Singulärwerte in $\Sigma$. Diese kann auch die Dimension ändern, wenn A nicht quadratisch ist.
3.  Eine weitere Rotation (oder Spiegelung) im $m$-dimensionalen Raum, beschrieben durch U.

$$ \text{Transformation durch A} = (\text{Rotation/Spiegelung mit U}) \times (\text{Skalierung mit } \Sigma) \times (\text{Rotation/Spiegelung mit } V^T) $$

**Pseudoinverse (Moore-Penrose Inverse):**

Die Pseudoinverse $A^+$ einer Matrix A kann mithilfe der SVD berechnet werden:
$$A^+ = V \Sigma^+ U^T$$
Die Matrix $\Sigma^+$ wird aus $\Sigma$ gebildet, indem man die reziproken Werte der Nicht-Null-Singulärwerte auf der Diagonalen nimmt und die Matrix transponiert.
Für eine invertierbare quadratische Matrix A ist $A^+ = A^{-1}$. Die Pseudoinverse existiert immer und ist eindeutig.

**Berechnung von SVD:**

Ein Weg zur Berechnung ist über die Eigenzerlegung von $A^T A$ oder $A A^T$:
1.  Berechne $A^T A$ (Dimension $n \times n$) oder $A A^T$ (Dimension $m \times m$) – wähle die kleinere Matrix.
2.  Bestimme die Eigenwerte und die entsprechenden normierten Eigenvektoren der gewählten Matrix.
3.  Die Quadratwurzeln der positiven Eigenwerte sind die Singulärwerte $\sigma_i$. Bilde daraus die Matrix $\Sigma$.
4.  Die normierten Eigenvektoren von $A^T A$ bilden die Spalten von V (bzw. Zeilen von $V^T$). Die normierten Eigenvektoren von $A A^T$ bilden die Spalten von U.
5.  Bestimme die verbleibende Matrix (U oder V) aus der Beziehung $AV = U\Sigma$ oder $A^T U = V \Sigma$. (Numerisch stabilere Methoden nutzen iterative Verfahren).

**Reduzierte SVD:**

Oft betrachtet man nur die Teile der Zerlegung, die den Nicht-Null-Singulärwerten entsprechen, was zu einer kompakten oder reduzierten SVD führt, die nützlich für niedrigrangige Approximationen ist.

**Anwendungen:**

Die SVD ist ein mächtiges Werkzeug mit vielfältigen Anwendungen, z. B.:
* [[Dimensionsreduktion]], insbesondere die [[Hauptkomponentenanalyse (PCA)]].
* Bild- und Signalverarbeitung (Komprimierung, Rauschunterdrückung).
* Lösung linearer Kleinste-Quadrate-Probleme.
* Bestimmung des Rangs einer Matrix.
* [[LoRA]] (Low-Rank Adaptation) für das [[Fine-tuning]] von [[KI-Modellen]].
* Empfehlungssysteme.

---

## Verwendung:

```dataview
list from [[Singulärwertzerlegung (SVD)]]
```