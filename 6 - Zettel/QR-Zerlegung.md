#Note

2025-05-18

Tags: [[QR-Zerlegung]], [[Matrixzerlegung]], [[Matrizen]], [[Lineare Algebra]], [[Orthogonale Matrix]], [[Dreiecksmatrix]], [[Gram-Schmidt-Verfahren]], [[Lineare Gleichungssysteme]], [[Lineare Regression]], [[Kleinste Quadrate]], [[Normalengleichung]], [[Eigenwerte]]

---

Die **QR-Zerlegung** ist eine [[Matrixzerlegung|Matrixzerlegung]], bei der eine Matrix $A$ in das Produkt einer [[Orthogonale Matrix|orthogonalen Matrix]] $Q$ und einer oberen [[Dreiecksmatrix]] $R$ faktorisiert wird.

**Definition:**

Eine $m \times n$ Matrix $A$ wird zerlegt in:

$$A = QR$$

* $Q$: Eine $m \times m$ **[[Orthogonale Matrix|orthogonale Matrix]]**. Das bedeutet, ihre Spalten bilden eine orthonormale Basis für $\mathbb{R}^m$, und es gilt $Q^T Q = E$. Link zu [[Orthogonale Matrix]].
* $R$: Eine $m \times n$ obere **[[Dreiecksmatrix]]**. Wenn $m > n$, enthält $R$ am unteren Ende Nullzeilen.

**Bestimmung von Q und R:**

Eine gebräuchliche Methode zur [[Berechnung]] der QR-Zerlegung ist das **[[Gram-Schmidt-Verfahren]]**, angewendet auf die Spalten der Matrix $A$. Die orthonormalen Vektoren aus dem Gram-Schmidt-Verfahren bilden die Spalten der Matrix $Q$. Die Matrix $R$ enthält die Koeffizienten, die die ursprünglichen Spalten von $A$ als Linearkombinationen der orthonormalen Vektoren ausdrücken, und hat die Struktur einer oberen [[Dreiecksmatrix]].

**Nutzen der QR-Zerlegung:**

Die QR-Zerlegung ist rechnerisch sehr nützlich und oft numerisch stabiler als die [[LU-Zerlegung]], insbesondere bei der Lösung von [[Lineare Gleichungssysteme|LGS]] und [[Kleinste Quadrate|Kleinste-Quadrate-Problemen]]:

* **Lösen von [[Lineare Gleichungssysteme|LGS]]:** Ein [[Lineare Gleichungssysteme|LGS]] $A\vec{x} = \vec{b}$ kann durch $QR\vec{x} = \vec{b}$ ersetzt werden. Durch Multiplikation mit $Q^T$ von links (da $Q^T Q = E$) erhalten wir $Q^T QR\vec{x} = Q^T\vec{b}$, was sich zu $R\vec{x} = Q^T\vec{b}$ vereinfacht. Dieses System kann effizient durch **Rückwärtseinsetzen** gelöst werden, da $R$ eine obere [[Dreiecksmatrix]] ist. Die Multiplikation mit der orthogonalen Matrix $Q^T$ ist numerisch stabil, da Orthogonale Matrizen [[Norm|Normen]] und [[Inneres Produkt|Innere Produkte]] erhalten.
* **Anwendung in der [[Lineare Regression|Linearen Regression]] ([[Kleinste Quadrate]]):** Die QR-Zerlegung ist eine hervorragende Methode zur Lösung des [[Kleinste Quadrate|Kleinste-Quadrate-Problems]] $\min ||\vec{y} - X\vec{c}||$, das zur [[Normalengleichung]] $X^T X \vec{c} = X^T \vec{y}$ führt. Durch Ersetzen von $X$ durch $QR$ können wir die [[Normalengleichung]] vermeiden und das Problem direkt lösen: $\min ||\vec{y} - QR\vec{c}||$. Da orthogonale Transformationen die Euklidische [[Norm]] erhalten, gilt $||\vec{y} - QR\vec{c}|| = ||Q^T (\vec{y} - QR\vec{c})|| = ||Q^T\vec{y} - Q^T QR\vec{c}|| = ||Q^T\vec{y} - R\vec{c}||$. Das Minimierungsproblem reduziert sich auf das Lösen von $R\vec{c} = Q^T\vec{y}$, was durch Rückwärtseinsetzen sehr effizient ist und die potenziell numerisch instabile [[Berechnung]] von $X^T X$ und dessen [[Inverse Matrix|Inversen]] vermeidet.
* **[[Berechnung]] von [[Eigenwerte|Eigenwerten]]:** Der QR-Algorithmus ist ein iteratives Verfahren, das die QR-Zerlegung nutzt, um die [[Eigenwerte]] einer Matrix zu approximieren.

---

## Verwendung:

```dataview
list from [[QR-Zerlegung]]
```