
Grundproblem Overfitting
Modell hat eine exzellente In Sample Performance auf den Trainingsdaten und ist damit darauf überangepasst (es hat sie auswendig gelernt). Die Out Of Sample performance kracht dramatisch ein.
Problem auch menschliches Overfitting, Testdaten werden für Parametertuning genutzt. Nicht nachweisbar aber auch am Ende Overfitting
Auswahl der unabhängigen Variablen

Wieso nicht einfach summe der Koeff als Regularisierung -> negative Koeffizienten
Entweder Betrag davo nnehmen, Lasso-Regression (L1 Reg) oder Quadrieren Ridge-Regression (L2 Reg)

Verhalten Ridge-Regression:
Strafe explodiert quadratisch und wird für große schätzer überproportional bestraft und strafe für schätzer < 1 unterproportional
Verhalten Lasso-Regression:Wirft unabhängige Variablen aus dem Modell raus. Erzeugt nicht differenzierbare stellen. Müssen wir auf 0 setzen?
Lasso + Ridge = Elastic-Net-Regression
Problem ist Erwartungstreue, da wir ja ein Bias durch die Regularisierung einbringen. Abhängigkeit von den Einheiten

MLE

Schätzung der größten Wahrscheinlichkeit (nicht für OLS) 
Wie wahrscheinlich ist es eine Stichprobe mit den Parametern \mu und sigma² bzw suche die parameter, die die wahrhsceinlichkeit maximiert

erhalte x gegeben mu sigma
max problem
Schätzung der Parameter theta (bei normal mit sigma und mu) aber allgemein theta
suche nach werte für die parameter theta für die die wahrscheinlichkeit maximal wird unsere stichprobe zu erhalten
verteilungsunabhängig
$$\max p(x_1,\dots,x_n \vert \theta_1,\dots,\theta_n)$$
Annahme alle Beobachtungen kommen aus der gleichen Stichprobe und beeinflussen sich nicht gegenseitig 
Produkt einzzelner Wahrscheinlichkeiten
$$p(x_1,\dots,x_n) = \prod_{i=1}^{n}p(x_i)$$
Wahrscheinlichkeit spot on treffer immer 0 außer edge case varianz 0
dichtefunktion muss genutzt werden, gibt mir nd exakt die wahrscheinlichkeit aber ist proportional zur wahrscheinlichkeit dieses x zu bekommen wiel wir die genaue wahrscheinlichkeit nicht genau bestimmen können.

$$$$ Dichtefunktion hier

Likelihood funktion als produkt über die dichtefunktion an den stellen, die meine stichprobe hergibt. Likelihood ist die wahrscheinlichkeit, gegeben bestimmer parameter
Die Dichtefunktion ist nicht einfach lösbar, dafür nutzen wir Logarithmusgesetze, damit landen wir bei der log-likelihood.
Wegen dem log gesetz wird aus einem Produkt eine Summe 
### Was ist die Likelihood?

Angenommen, du hast Daten $x_1, x_2, \dots, x_n$ und ein Modell mit Parameter $\theta$.

Die Likelihood ist

$$
L(\theta) = P(x_1, \dots, x_n \mid \theta).
$$

Für unabhängige Beobachtungen wird daraus ein Produkt:

$$
L(\theta) = \prod_{i=1}^{n} P(x_i \mid \theta).
$$

---

### 2. Warum nimmt man den Logarithmus?

Der Logarithmus macht aus Produkten Summen:

$$
\log\!\left(\prod_{i=1}^{n} P(x_i \mid \theta)\right)
=
\sum_{i=1}^{n} \log P(x_i \mid \theta).
$$

Das hat mehrere Vorteile:

#### Einfachere Mathematik

Statt ein riesiges Produkt zu maximieren, maximierst du eine Summe.
oft wird dann ein minus vor die log-likelihood funktion gemacht
$\min -\ell(\theta)$ oder $\max \ell(\theta)$
Bei der Normalvertielung sind unsere schätzer einfach Stichprobenmittel für mu und Stichprobenvarianz für sigma hoch 2 


Klausur
Ganz stark an der Übungsklausur orientieren aber ohne Multiple Choice 
Verteilungsfunktion/Dichtefunktion Erwartungswert Varainz, Wahrscheinlichkeitsfunktion und Z Test

Stat. Modellierung mit Verteilungen Vertilungen verstehen Glecih Binomial Poission Exponentialverteilung Gleichverteilung. Bestimmte Storys Binomial Poission Exponential
Fokus nicht Rechnung sondern wann welche Verteilung welche parameter, was bedeuten die und wie setz ich das ein

Statistische Test
Umgehen, Hypothesenpaar aufstellen, p wert und konfidenzintervall interpretation, ttest familie 1 und 2 stichproben bei 2 verbunden/nicht verbunden allgemeein gerichtete und ungerichtete stichprobe auf verteilung kolmogorov smirnov anderson darling ... Chi quadrat und ANOVA tests
Nicht viel von hand rechnen also interpretieren und code kennen/Verständnis

Lineare Regression
regressionstabelle iinterpretieren was bedeuten koeff p wert R2 wert numerisches merkmal categorial merkmal std
herausforderungen overfitting endogenitätsprobleme multikollinearität 
Open Book Klausur

Vordrucke auf der klausur oder Tabellen/etc WICHTIG WAS JETZT KOMMT.
vorlagen nutzen auf dem klausurpapier, weil sonst selbstzeichnen viel zeit kostet
Rechenaufgaben sind Antwortsätze überflüssig
Keine größeren Coding Aufgaben weil keine IDE und weil kein mensch code so schreibt