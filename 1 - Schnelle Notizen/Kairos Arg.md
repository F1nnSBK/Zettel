
### Mathematische Argumentation: Cholesky-Updates in LinUCB

Bevor die konkrete Formulierung des LinUCB-Algorithmus betrachtet wird, ist eine grundlegende mathematische Unterscheidung zwischen **Exaktheit** und **numerischer Stabilität** erforderlich.

#### Exaktheit der Aktualisierung

Sei die regulierte Design-Matrix definiert als

$$  
A_t = \lambda I + \sum_{i=1}^{t} x_i x_i^\top,  
$$

wobei $\lambda > 0$ die Ridge-Regularisierung bezeichnet. Mit Eintreffen einer neuen Beobachtung $x_t$ ergibt sich das Rang-1-Update

$$  
A_t = A_{t-1} + x_t x_t^\top.  
$$

Sowohl die Sherman-Morrison-Formel als auch ein Cholesky-Rang-1-Update beschreiben exakt dieselbe mathematische Transformation dieser Matrix. Es gilt somit

 $$  
A_t^{(\mathrm{SM})}

 A_t^{(\mathrm{Chol})}

A_{t-1}  
+  
x_t x_t^\top.  
$$

Daraus folgt unmittelbar, dass Cholesky-Updates **keine Approximation** darstellen. Es wird weder Information verworfen noch eine Dimensionsreduktion vorgenommen. Beide Verfahren repräsentieren dieselbe Kovarianzmatrix und verarbeiten sämtliche Komponenten des Feature-Vektors vollständig.

Der Unterschied zwischen beiden Verfahren liegt daher ausschließlich in ihrer numerischen Umsetzung.

---

#### Numerische Stabilität

Die Sherman-Morrison-Formel aktualisiert die inverse Matrix direkt,

$$  
A_t^{-1}

A_{t-1}^{-1}

\frac{  
A_{t-1}^{-1}x_tx_t^\top A_{t-1}^{-1}  
}{  
1+x_t^\top A_{t-1}^{-1}x_t  
},  
$$

wobei sämtliche Operationen im Fließkommaformat $fl(\cdot)$ ausgeführt werden. Aufgrund unvermeidbarer Rundungsfehler akkumulieren sich numerische Abweichungen mit zunehmender Anzahl von Updates. Dadurch kann die berechnete Matrix schrittweise ihre Symmetrie sowie ihre positive Definitheit verlieren, obwohl diese Eigenschaften mathematisch erhalten bleiben müssten.

Der Cholesky-Ansatz verfolgt stattdessen die Faktorisierung

$$  
A_t=L_tL_t^\top,  
$$

wobei $L_t$ eine untere Dreiecksmatrix ist. Die Rang-1-Aktualisierung erfolgt unmittelbar auf den Faktoren,

$$  
L_t=\operatorname{CholeskyUpdate}(L_{t-1},x_t),  
$$

sodass die Beziehung

$$  
A_t=L_tL_t^\top  
$$

zu jedem Zeitpunkt erhalten bleibt. Da jede rekonstruierte Matrix per Konstruktion als Produkt einer Dreiecksmatrix mit ihrer Transponierten entsteht, bleiben Symmetrie und positive Definitheit numerisch wesentlich stabiler erhalten als bei einer direkten Aktualisierung der Inversen.

Der Vorteil des Cholesky-Verfahrens besteht folglich **nicht** in einer höheren mathematischen Genauigkeit, sondern ausschließlich in einer deutlich besseren numerischen Stabilität.

---

### Einordnung der Regularisierung

Eine tatsächliche Dämpfung oder Filterung des Modells entsteht nicht durch die Cholesky-Zerlegung selbst, sondern an anderen Stellen des Gesamtsystems.

Zum einen wirkt die Ridge-Regularisierung

$$  
A=\lambda I+\sum_i x_ix_i^\top  
$$

als Prior und begrenzt den Einfluss einzelner Beobachtungen auf die Parameterschätzung. Zum anderen reduzieren Matryoshka-Embeddings (MRL) die effektive Repräsentation auf besonders informationshaltige Merkmalsdimensionen und unterdrücken dadurch irrelevante oder verrauschte Signalanteile.

Die Cholesky-Zerlegung verändert hingegen ausschließlich die numerische Darstellung der Matrix und besitzt keinen regularisierenden oder informationsfilternden Effekt.

---

## Anwendung der Cholesky-Zerlegung im LinUCB-Algorithmus

Der Upper-Confidence-Bound eines Arms $a$ für einen Nutzer $u$ ist definiert durch

# $$  
\operatorname{UCB}_{u,a}

x_{t,a}^\top\hat{\theta}_u  
+  
\alpha  
\sqrt{  
x_{t,a}^\top A_u^{-1}x_{t,a}  
}.  
$$

Dabei gilt

# $$  
A_u

\lambda I  
+  
\sum_{\tau\in\mathcal H_u}  
x_\tau x_\tau^\top  
$$

sowie

$$  
\hat{\theta}_u=A_u^{-1}b_u,  
\qquad  
b_u=\sum_{\tau}r_\tau x_\tau.  
$$

Anstelle einer expliziten Inversion wird nun die Cholesky-Zerlegung

$$  
A_u=L_uL_u^\top  
$$

verwendet.

### Explorationsterm

Für den Unsicherheitsterm gilt

 $$  
x^\top A_u^{-1}x

 x^\top(L_uL_u^\top)^{-1}x

x^\top(L_u^\top)^{-1}L_u^{-1}x.  
$$

Definiert man den Hilfsvektor $z$ als Lösung des linearen Gleichungssystems

$$  
L_uz=x,  
$$

so folgt unmittelbar

$$  
x^\top A_u^{-1}x

 z^\top z

|z|_2^2.  
$$

Damit vereinfacht sich der Explorationsterm zu

$$  
\alpha|z|_2,  
\qquad  
L_uz=x.  
$$

Da $L_u$ eine untere Dreiecksmatrix ist, kann $z$ mittels Vorwärtssubstitution in $O(d^2)$ bestimmt werden. Eine explizite Matrixinversion ist nicht erforderlich.

---

### Parameterschätzung

Auch die Schätzung des Parametervektors erfolgt ohne Inversion. Aus

$$  
A_u\hat{\theta}_u=b_u  
$$

folgt

$$  
L_uL_u^\top\hat{\theta}_u=b_u.  
$$

Die Lösung erfolgt in zwei aufeinanderfolgenden linearen Gleichungssystemen.

Zunächst wird mittels Vorwärtssubstitution

$$  
L_uy=b_u  
$$

gelöst. Anschließend ergibt sich durch Rückwärtssubstitution

$$  
L_u^\top\hat{\theta}_u=y.  
$$

Damit wird die Parameterschätzung vollständig auf numerisch stabile Dreieckssysteme zurückgeführt.

---

### Rang-1-Update

Nach einer neuen Beobachtung $x_t$ wird die Design-Matrix gemäß

# $$  
A_{\mathrm{neu}}

A_{\mathrm{alt}}  
+  
x_tx_t^\top  
$$

aktualisiert.

Unter Verwendung der Cholesky-Faktorisierung entspricht dies

# $$  
L_{\mathrm{neu}}L_{\mathrm{neu}}^\top

L_{\mathrm{alt}}L_{\mathrm{alt}}^\top  
+  
x_tx_t^\top.  
$$

Anstelle einer Aktualisierung der inversen Matrix wird ein Cholesky-Rang-1-Update angewendet,

# $$  
L_{\mathrm{neu}}

\operatorname{CholeskyUpdate}  
(  
L_{\mathrm{alt}},  
x_t  
),  
$$

welches den Faktor $L_{\mathrm{alt}}$ direkt in $O(d^2)$ Operationen transformiert. Die Faktorisierung bleibt dabei exakt erhalten, sodass sämtliche nachfolgenden Berechnungen ausschließlich auf numerisch stabilen Dreieckssystemen basieren.

Damit liefert das Cholesky-Verfahren dieselbe mathematische Lösung wie Sherman-Morrison, reduziert jedoch die Akkumulation von Fließkommafehlern und gewährleistet eine deutlich robustere numerische Implementierung bei langen Online-Lernprozessen.