# Note

2025-05-15

Tags: [[Laplace-Entwicklung]], [[Determinante]], [[Matrizen]], [[Lineare Algebra]], [[Kofaktor]], [[Unterdeterminante]]

---

Die **[[Laplace-Entwicklung]]** (oder Kofaktorentwicklung) ist eine rekursive Methode zur [[Berechnung]] der [[Determinante]] einer [[Quadratische Matrix|quadratischen Matrix]]. Sie ist besonders nützlich für Matrizen der [[Dimension]] $n \times n$ mit $n \ge 4$, da sie die [[Berechnung]] auf die [[Determinante|Determinanten]] kleinerer [[Untermatrix|Untermatrizen]] reduziert.

**Prinzip:**

Man wählt eine beliebige Zeile oder Spalte der Matrix. Die [[Determinante]] der Matrix ist dann die Summe der Produkte der Elemente dieser Zeile oder Spalte mit ihren zugehörigen [[Kofaktor|Kofaktoren]].

Die Formel für die Entwicklung nach der $i$-ten Zeile ist:

$$
\det(A) = \sum_{k=1}^n a_{i,k} \cdot \operatorname{Cof}_{i,k}
$$

Die Formel für die Entwicklung nach der $k$-ten Spalte ist:

$$
\det(A) = \sum_{i=1}^n a_{i,k} \cdot \operatorname{Cof}_{i,k}
$$

Der [[Kofaktor]] $\operatorname{Cof}_{i,k}$ (entspricht $a_{i,k}^*$) zum Element $a_{i,k}$ ist 

$$
(-1)^{i+k} \cdot \det(A_{i,k}),
$$ 

wobei $A_{i,k}$ die [[Untermatrix]] ist, die durch Entfernen der $i$-ten Zeile und $k$-ten Spalte entsteht.

**Schrittweise [[Berechnung]] für eine $4 \times 4$ Matrix:**

Wir möchten die [[Determinante]] der folgenden $4 \times 4$ Matrix $A$ berechnen:

$$
A = \begin{pmatrix} 
1 & 0 & 2 & -1 \\ 
0 & 1 & 0 & 2 \\ 
3 & 0 & 0 & 1 \\ 
4 & -2 & 0 & 0 
\end{pmatrix}
$$

Um die [[Berechnung]] zu vereinfachen, wählen wir eine Zeile oder Spalte mit möglichst vielen Nullen. In diesem Fall ist die 2. Spalte eine gute Wahl, da sie zwei Nullen enthält. Wir entwickeln also nach der 2. Spalte ($k = 2$).

$$
\det(A) = a_{1,2} \operatorname{Cof}_{1,2} + a_{2,2} \operatorname{Cof}_{2,2} + a_{3,2} \operatorname{Cof}_{3,2} + a_{4,2} \operatorname{Cof}_{4,2}
$$

$$
\det(A) = 0 \cdot \operatorname{Cof}_{1,2} + 1 \cdot \operatorname{Cof}_{2,2} + 0 \cdot \operatorname{Cof}_{3,2} + (-2) \cdot \operatorname{Cof}_{4,2}
$$

Terme mit $a_{i,2} = 0$ fallen weg:

$$
\det(A) = 1 \cdot \operatorname{Cof}_{2,2} + (-2) \cdot \operatorname{Cof}_{4,2}
$$

Nun müssen wir die [[Kofaktor|Kofaktoren]] $\operatorname{Cof}_{2,2}$ und $\operatorname{Cof}_{4,2}$ berechnen. Dies erfordert die [[Berechnung]] der [[Determinante|Determinanten]] von $3 \times 3$ [[Untermatrix|Untermatrizen]].

**Berechnung von $\operatorname{Cof}_{2,2}$:**

$$
\operatorname{Cof}_{2,2} = (-1)^{2+2} \cdot \det(A_{2,2}) = +1 \cdot \det \begin{pmatrix} 
1 & 2 & -1 \\ 
3 & 0 & 1 \\ 
4 & 0 & 0 
\end{pmatrix}
$$

Wir berechnen die [[Determinante]] der $3 \times 3$ [[Untermatrix]] $A_{2,2}$. Wir können hier wieder die [[Laplace-Entwicklung]] nutzen, z.B. nach der 2. Spalte (enthält Nullen):

$$
\det(A_{2,2}) = 2 \cdot (-1)^{1+2} \cdot \det \begin{pmatrix} 
3 & 1 \\ 
4 & 0 
\end{pmatrix}
+ 0 \cdot \operatorname{Cof}_{2,2}' + 0 \cdot \operatorname{Cof}_{3,2}'
$$

$$
\det(A_{2,2}) = -2 \cdot (3 \cdot 0 - 1 \cdot 4) = -2 \cdot (-4) = 8
$$

Also ist $\operatorname{Cof}_{2,2} = 8$.

**Berechnung von $\operatorname{Cof}_{4,2}$:**

$$
\operatorname{Cof}_{4,2} = (-1)^{4+2} \cdot \det(A_{4,2}) = +1 \cdot \det \begin{pmatrix} 
1 & 2 & -1 \\ 
0 & 0 & 2 \\ 
3 & 0 & 1 
\end{pmatrix}
$$

Wir berechnen die [[Determinante]] der $3 \times 3$ [[Untermatrix]] $A_{4,2}$. Wir nutzen wieder die [[Laplace-Entwicklung]], z.B. nach der 2. Spalte:

$$
\det(A_{4,2}) = 2 \cdot (-1)^{1+2} \cdot \det \begin{pmatrix} 
0 & 2 \\ 
3 & 1 
\end{pmatrix} + 0 \cdot \operatorname{Cof}_{2,2}'' + 0 \cdot \operatorname{Cof}_{3,2}''
$$

$$
\det(A_{4,2}) = -2 \cdot (0 \cdot 1 - 2 \cdot 3) = -2 \cdot (-6) = 12
$$

Also ist $\operatorname{Cof}_{4,2} = 12$.

**Endergebnis:**

Nun setzen wir die berechneten [[Kofaktor|Kofaktoren]] in die ursprüngliche Entwicklungsformel ein:

$$
\det(A) = 1 \cdot \operatorname{Cof}_{2,2} + (-2) \cdot \operatorname{Cof}_{4,2} = 1 \cdot (8) - 2 \cdot (12) = 8 - 24 = -16
$$

Die [[Determinante]] der Matrix $A$ beträgt **$-16$**.

Die [[Laplace-Entwicklung]] zerlegt die [[Berechnung]] einer großen [[Determinante]] in die [[Berechnung]] kleinerer [[Unterdeterminante|Unterdeterminanten]], bis man bei $2 \times 2$ oder $3 \times 3$ Matrizen ankommt, deren [[Determinante]] einfacher zu berechnen ist.

---

## Verwendung:

```dataview
list from [[Laplace-Entwicklung]]
```
