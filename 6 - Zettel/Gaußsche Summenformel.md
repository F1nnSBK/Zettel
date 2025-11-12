#Note

2025-11-12

Tags: [[Prinzip der vollständigen Induktion]], [[Analysis 1]], [[Mathematik]]

---
Die **Gaußsche Summenformel** ist ein klassisches Beispiel für das [[Prinzip der vollständigen Induktion]]. 
**Satz:**
Für jede [[Natürliche Zahlen|natürliche Zahl]] $n$ gilt:
$$A(n): \sum_{k=1}^{n} k = \frac{n(n+1)}{2}$$
**Beweis durch [[Prinzip der vollständigen Induktion|vollständige Induktion]]:**
+ $(I)$ Induktionsanfang $n=1$: 
	$$A(1) = \sum_{k=1}^{1} k =1= \frac{1(1+1)}{2} = \frac{2}{2} = 1$$
	Die Aussage ist für $n=1$ wahr.

+ $(II)$ Induktionsschluss $A(n) \to A(n+1)$: 
	**Induktionsvoraussetzung (IV):** $$\sum_{k=1}^{n} k = \frac{n(n+1)}{2}$$
	**Induktionsbehauptung (IB):** $$\sum_{k=1}^{n+1} k = \frac{(n+1)(n+2)}{2}$$
	**Beweis:**
	  $$A(n+1) = 1, \dots, n + (n+1) = \frac{n+1((n+1)+1)}{2}$$
	  Aus $(I)$ wissen wir, $1, \dots, n = \frac{n(n+1)}{2}$ also setzen wir $\frac{n(n+1)}{2}$ links ein.
	  $$\frac{n(n+1)}{2}+(n+1)=\frac{(n+1)(n+2)}{2}$$
	  Ausklammern von $(n+1)$.
	  $$(n+1)(\frac{n}{2}+ 1)=\frac{(n+1)(n+2)}{2}$$
	  Gleicher Nenner in $(\frac{n}{2} +1)$.
	  $$(n+1)(\frac{n}{2}+ \frac{2}{2})=\frac{(n+1)(n+2)}{2}$$
	$$(n+1)(\frac{n+2}{2})=\frac{(n+1)(n+2)}{2}$$
	$$\frac{(n+1)(n+2)}{2}=\frac{(n+1)(n+2)}{2}$$
Gauß hat diese Summenformel als Kind im Unterricht bewiesen, als er die Summe $\sum_{k=1}^{100} k$ bilden sollte. Er hat jeweils die Summe der an den Enden gegenüberliegenden Paare $100 + 1, 99 + 2, 98 +3, ...$ gebildet.
$$\sum_{k=1}^{100} = \frac{100(100 + 1)}{2}=\frac{10100}{2}=5050$$
---
### Verwendung
```dataview
list from [[Gaußsche Summenformel]]
```