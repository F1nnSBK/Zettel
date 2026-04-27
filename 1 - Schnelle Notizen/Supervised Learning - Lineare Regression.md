
In der Realität sind die Zusammenhänge eig nie linear
"Essentially, all models are wrong, but some are useful" ~Box

Einfaches lineares Modell, 1 Feature
$\hat{Y} = \beta_0 + \beta_1 X + \epsilon$ (Link zu Business Intelligence)

Link zur linearen Algebra mit $\beta = (X^TX)^{-1} \cdot y^{T}X$ 

Genauigkeit der Koeffizientenschätzung
Standardfehler der Koeffizienten S.14 über die Verteilungen der Koeffizienten wie $\beta$
Konfidenzintervalle mit SEs: 95% Konfidenzintervall = $\hat{\beta} \pm 2 \cdot SE(\hat{\beta})$
(- -> Untergranze, + -> Obergrenze)

Gibt es einen Zusammenhang zwischen zwei Variablen? Wenn $\beta_1$ = 0, dann gibt es **keinen** Zusammenhang

F: in der fort. Statistik sagen wir, dass wir uns sicher sind, dass ein Ergebnis richtig ist, wenn es außerhlab eines Konfidenzintervalls liegt aber hier sagen wir, es ist sicher, wenn es in dem Konfidenzintervall liegt. Bei der Statistik war das Argument, dass es in dem Konfidenzintervall auch andere Werte sein könnten. (Bezug zu p-Wert)

Verbindung zu Hypothesentests (t-test, p-Wert)
(das sind die zwei Varianten um den Koeffizient zu schätzen, also den zusammenhang)

Idee: Das fließt hier alles zusammen, p-Werte der Koeffizienten, Tests (fort Statistik), Business Intelligence. Weil wir bei IBM SPSS bei BI auch für die einzelnen Kausalvariablen, die wir mit Design-Variablen an/aus geschalten haben, p-Werte und Standardfehler bekommen haben (oder auch bei den Lag-Variablen, führt dann zu AR Komponenten von ARIMA -> PACF).

Verbindung zu Bestimmtheitsmaß, erklärte und nicht erklärte Streeung
kommt auch auf S.20 -> nur bei train

Multiple Lineare Regression. S.23
Formel: $Y=\beta_0 + \beta_j \cdot X_j$
Interpretation von $\beta_j$: Durchschnittliche Auswirkung auf $Y$ eines Einheitsanstiegs in $X_j$ wenn alle anderen **Featurewerte gleich bleiben**.
Idealszenario: Features sind unkorreliert. Achtung -> Problem der Kollinearität bei mehreren Features möglich -> numerisches Problem

Kollinearität -> beeinflusst die eine Variable die andere? Ja? -> doof (Problem Schätzbarkeit & Problem Interpretation). 
Dekorrelieren

Principal Component Regression
-> PCA wird vorgeschalten, dadurch hat man dekorrelierte Features und numerische Stabilität 
-> Interpretation wird dann schwierig, weil Features verloren gehen & transformiert werden

Feature Selection
Entscheidung über die wichtigen Variablen
zu hohe p-Werte aussortieren -> nicht immer ideal
Brute Force -> Oft zu komplex
Stepwise Selection (Forward/Backward) Logik in S.33
-> Einzeln die Modelle mit -> Forward oder ohne -> Backward eines Features Testen (Greedy) - Achtung bei der Wahl des Maßes

Mallow’s C, Akaike information criterion (AIC), Bayesian information criterion (BIC), adjusted $R^{2}$

Weitere Alternativen wären -> Optimierungsproblem Min Feature-Feature Cor(X1,X2) oder Max Feature-Label Cor(X,Y)
Lasso-Regression








