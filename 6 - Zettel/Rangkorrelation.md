#Note

2026-05-15

Tags: [[Statistik]], [[Spearman]], [[Rangkorrelation]], [[Machine Learning]], [[Robustheit]]
#deskriptive_statistik

---
Die **Spearman-Rangkorrelation** ($\rho$ oder $r_s$) ist ein nicht-parametrisches Maß für den Zusammenhang. Sie bewertet, wie gut die Beziehung zwischen zwei Variablen durch eine monotone Funktion beschrieben werden kann.

### Kernkonzept

Anstatt die Differenzen der Messwerte $(x_i - \bar{x})$ zu betrachten, nutzt man die Differenzen der Ränge $d_i = R(x_i) - R(y_i)$.

- Ein Wert von **+1** bedeutet einen perfekt gleichgerichteten monotonen Zusammenhang.
- Ein Wert von **-1** bedeutet einen perfekt gegengerichteten monotonen Zusammenhang.
- Ein Wert von **0** bedeutet keinen monotonen Zusammenhang.

### Mathematische Definition (nach Spearman)

Wenn keine Bindungen (gleiche Ränge) vorliegen, vereinfacht sich die Berechnung auf:

$$r_s = 1 - \frac{6 \sum_{i=1}^n d_i^2}{n(n^2 - 1)}$$

$d_i$ ist dabei die Differenz der Ränge des $i$-ten Paares.

### Vorteile gegenüber Pearson

1. **Skalenniveau:** Funktioniert bereits ab Ordinalskala (z. B. Umfrage-Rankings).
2. **Robustheit:** Ein extremer Ausreißer verändert nur seinen Rang (z. B. von Rang 10 auf Rang 11), aber nicht die Magnitude der Differenz im Zähler.
3. **Nicht-Linearität:** Erfasst jeden Zusammenhang, der streng monoton steigend oder fallend ist, unabhängig von der Krümmung der Funktion.

### Kendall's Tau ($\tau$)

Eine Alternative zur Spearman-Korrelation, die auf dem Vergleich von **konkordanten** (gleichsinnigen) und **diskordanten** (gegensinnigen) Paaren basiert. $\tau$ ist oft noch robuster bei kleinen Stichproben mit vielen Bindungen.

---

### Flashcards

Was ist der fundamentale Unterschied in der Datenbasis zwischen Pearson- und Spearman-Korrelation?::Pearson nutzt die metrischen Rohwerte (Abstände zum Mittelwert), während Spearman ausschließlich die Rangplätze (Positionen in der sortierten Reihe) der Datenpunkte verwendet.

Warum ist die Spearman-Rangkorrelation unempfindlich gegenüber Ausreißern?::Da ein Ausreißer unabhängig von seinem extremen Wert lediglich den höchsten oder niedrigsten Rangplatz einnimmt. Die mathematische Differenz zu den Nachbarrängen bleibt immer konstant klein ($d=1$), egal wie weit der Wert numerisch entfernt ist.

Welches Ergebnis liefern Pearson ($r$) und Spearman ($\rho$) für die Funktion $y = \log(x)$ bei streng positiven Werten?
?
Spearman liefert $\rho = 1$, da die Funktion streng monoton steigend ist. Pearson liefert $r < 1$, da der Zusammenhang zwar steigend, aber aufgrund der Krümmung der Logarithmus-Funktion nicht streng linear ist.

Wie ist $d_i$ in der Spearman-Formel definiert?
?
$d_i = R(x_i) - R(y_i)$. Es ist die Differenz der Rangplätze, die ein Objekt $i$ in den beiden untersuchten Merkmalen $X$ und $Y$ einnimmt.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Rangkorrelation]]
SORT file.mtime DESC
```