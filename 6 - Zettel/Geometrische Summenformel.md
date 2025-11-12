#Note

2025-11-12

Tags: [[Prinzip der vollständigen Induktion]], [[Mathematik]], [[]]

---
Die **geometrische Summenformel** kann wie die [[Gaußsche Summenformel]] gut mit dem [[Prinzip der vollständigen Induktion]] Bewiesen werden. Die [[Summe]], welche aus ihr hervorgeht, beschreibt eine "[[Zinseszins]]"-Summe, jeder Term ist ein Vielfaches des vorherigen mit dem Faktor $x$. Das ermöglicht auch eine einfache, intuitive Herleitung.

$$S_n=1+x+x^2+\dots+x^n = \frac{1-x^{n+1}}{1-x}$$
+ Intuitive Herleitung mit $S_n - x \cdot S_n$ 
$$S_n -xS_n=(1 + \cdot +x^n)-(x + \cdot + x^{n+1})$$$$S_n(1-x)=1-x^{n+1}$$$$S_n=\frac{1-x^{n+1}}{1-x}$$
**Beweis durch [[Prinzip der vollständigen Induktion|vollständige Induktion]]:**
+ $(I)$ Induktionsanfang $n=1$:
	$$A(1)=1+x^1=1+x=\frac{1-x^{1+1}}{1-x}=\frac{(1-x)(1+x)}{1-x}=1+x$$
	Der Induktionsanfang ist also richtig $\forall x \neq 1$ und $n=1$.

+ $(II)$ Induktionsschluss $A(n) \to A(n+1)$:
	**Induktionsvoraussetzung (IV):**
	$$A(n)=\sum_{k=0}^{n}x^k=\frac{1-x^{n+1}}{1-x}$$
	**Induktionsbehauptung (IB):**
	$$A(n+1)=\sum_{k=0}^{n+1}x^k=\frac{1-x^{n+2}}{1-x}$$
	**Beweis:**
	$$\frac{1-x^{n+1}}{1-x}+x^{n+1}=\frac{1-x^{n+2}}{1-x}$$
	$$\frac{1-x^{n+1}}{1-x}+\frac{x^{n+1}(1-x)}{1-x}=\frac{1-x^{n+2}}{1-x}$$
	$$\frac{1-x^{n+1}+x^{n+1}-x^{n+2}}{1-x}=\frac{1-x^{n+2}}{1-x}$$
	$$\frac{1-x^{n+2}}{1-x}=\frac{1-x^{n+2}}{1-x}$$
	Die Summenformel ist also richtig $\forall x \neq 1$.


---
### Verwendung
```dataview
list from [[Geometrische Summenformel]]
```