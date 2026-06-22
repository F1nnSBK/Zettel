
Stichprobenvarianz nach Varianzberechnung nicht gemacht
$$s^2= \frac{N}{N-1} \cdot \sigma^2 $$
korrigierte Standardabweichung nicht gemacht
Wenn man im Zähler ein Quantil berechnen möchte, ist der erste Term unser $p$
$$x_p=u_{i-1}+ \frac{p-\sum^{i-1}_{j=1}r_j}{r_i}(u_i-u_{i-1})$$
p Zb mit 0,25; 0,75 oder 0,5 beim Median
Fisher Schiefe auf Formelblatt
Spannweite ist Range $R = x_{\max} - x_{\min}$
<<<<
### Fisher-Schiefe ($\gamma_{\text{Fisher}}$)

Misst die Asymmetrie einer Verteilung.

#### 1. Formel
$$\gamma_{\text{Fisher}} = \frac{M_3}{s^3}$$

* $M_3$: 3. zentrales Moment
* $s$: Empirische Standardabweichung ($s = \sqrt{s^2}$)

#### 2. Berechnung (klassierte Daten)
Gegeben: $N = \sum n_i$ (Gesamtzahl), $m_i$ (Klassenmitten), $n_i$ (Häufigkeiten) und $\bar{x}$ (Mittelwert).

1. **Varianz ($s^2$):** $$s^2 = \frac{1}{N} \sum n_i (m_i - \bar{x})^2$$
2. **3. zentrales Moment ($M_3$):** $$M_3 = \frac{1}{N} \sum n_i (m_i - \bar{x})^3$$

#### 3. Quick-Check
* $\gamma > 0 \rightarrow$ **rechtsschief** (linkssteil, langer Schwanz rechts)
* $\gamma = 0 \rightarrow$ **symmetrisch**
* $\gamma < 0 \rightarrow$ **linksschief** (rechtssteil, langer Schwanz links)


Gruppierte und klassierte Daten können auch gemischt vorkommen, übungsklausur aufgabe
Wenn zb Aufgabe mit gruppierten Daten + Klasse also kein arith. Mittel möglich dann schiefe oft mit Quantilskoeffizient

Fehlt in der Formelsammlung: 
Fisher Schiefe & Kurtosis
Quantilskoeffizient

Wahrscheinlichkeitsverteilung und Dichtevertailung beispielvisualisuerungen mit tikz (diskret)

idee bei skalierung von erwartungswert und vraianz das als \sum x i proportional zu N(n mal erwartungswert, n mal varianz)

wie man einen z test schriftlich rechnet
p wert ausrechnen über integral -infty bis grenze im taschenrechner auf kum normal umschalten

parameterschätzung bei der binom verteilung einfach nur p herausfinden, geht oft mit dreisatz
code für vetilungen in python kennen also stats.binom.cdf(parameter kennen) und die pmf etc 

bei mindestens gerne mit gegenwarhschelinlichkeit arbeiten

poisson vertilung parameter lambda ist erwartungswert und varianz und zusammenhang dass der oft pro stunde etwas sagt. Zsm mit pausen länge duch den kehrwert von lambda

was prüft der ttest, was prüfen alle tetst und die hypothesen standardhypothesen.
KS tes tauch

ANOVA catch verstehen 
regression analsieren können 
zb 
> | ============================================================= coef std err t P>|t| ============================================================= (Intercept) 50000.0 4500.0 11.11 < 0.001 gender_female -2200.0 4400.0 -0.50 0.618 state_abroad 5000.0 7500.0 0.67 0.504 industry_aerospace 5000.0 2500.0 2.00 0.048 * industry_engineering -2000.0 2000.0 -1.00 0.308 industry_consulting 5000.0 5000.0 1.00 0.308 math_1 -5.0 3.0 -1.67 0.092 . math_2 5.0 1.5 3.33 0.006 ** statistics 10.0 4.0 2.50 0.024 * logic -0.1 -5.0 0.02 0.937 ... ======================================
> 
> 