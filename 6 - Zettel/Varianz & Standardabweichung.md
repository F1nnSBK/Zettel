#Note

2026-05-15

Tags: [[Statistik]], [[Varianz]], [[Standardabweichung]], [[Machine Learning]], [[Feature Scaling]], [[Centroid-Based Clustering]], [[Smoothing]], [[Kovarianz]]
#deskriptive_statistik

---
Varianz und Standardabweichung sind die fundamentalen Maße für die Streuung (Dispersion) metrischer Daten. Sie beschreiben die "Energiedichte" der Abweichungen vom Zentrum.

### Die Varianz ($s^2$)

Die Varianz ist der Durchschnitt der quadrierten Abweichungen vom arithmetischen Mittel.

- **Empirische Varianz (Stichprobe):**
$$s^2 = \frac{1}{n-1} \sum_{i=1}^n (x_i - \bar{x})^2$$

- **Einheiten-Problem:** Da die Werte quadriert werden, ändert sich die Einheit (z. B. von $m$ zu $m^2$). Das macht die Interpretation im Sachkontext schwierig.


### Die Standardabweichung ($s$)

Sie ist die positive Quadratwurzel der Varianz und stellt die Streuung wieder auf die ursprüngliche Skala der Messwerte zurück.

$$s = \sqrt{s^2}$$

### Brückenschlag: Unsupervised Learning & Data Science

1. **[[PCA]] (Principal Component Analysis):** Die PCA sucht jene Projektionen, welche die maximale Varianz der Daten erhalten. Varianz wird hier mit **Informationsgehalt** gleichgesetzt.

2. **[[Z-Score]] Normalisierung:** Um Features vergleichbar zu machen, transformiert man sie so, dass sie eine Varianz von 1 haben:
$$z = \frac{x - \bar{x}}{s}$$

3. **[[Smoothing]] (Glättung):** In Kernel-Methoden bestimmt die Varianz $\sigma^2$ des Kernels (z. B. RBF-Kernel), wie stark benachbarte Punkte einander beeinflussen. Eine hohe Varianz führt zu starkem "Over-smoothing" (hoher Bias), eine zu kleine zu "Wiggliness" (hohe Varianz des Modells).

4. **[[Anomalieerkennung]]:** Punkte, die mehr als $3s$ vom Mittelwert entfernt sind, werden oft als potenzielle Ausreißer flaggiert (Sigma-Regeln).

---

### Flashcards

Warum führt die Quadrierung der Abweichungen in der Varianzberechnung dazu, dass Ausreißer überproportional stark gewichtet werden?::Da die Abweichung $(x_i - \bar{x})$ quadriert wird, wächst der Einfluss eines Wertes quadratisch mit seiner Distanz zum Mittelwert. Eine doppelt so große Abweichung führt zu einem viermal so großen Beitrag zur Varianz.
<!--SR:!2026-06-09,1,230-->

Was ist der mathematische Grund für die Division durch $n-1$ statt $n$ bei der Stichprobenvarianz?::Da der Mittelwert der Stichprobe bereits eine Schätzung ist, sind die Abweichungen zum Stichprobenmittelwert tendenziell kleiner als zum wahren Mittelwert der Grundgesamtheit. Die Division durch $n-1$ (Bessel-Korrektur) korrigiert diesen Bias und macht den Schätzer erwartungstreu.
<!--SR:!2026-06-09,1,230-->

Inwiefern hängen die Konzepte "Varianz" und "Information" in der PCA zusammen?
?
Die PCA geht davon aus, dass Dimensionen mit hoher Varianz die wesentlichen Strukturen und Unterschiede der Daten enthalten (Signal), während Dimensionen mit sehr geringer Varianz oft nur Rauschen repräsentieren und vernachlässigt werden können.
<!--SR:!2026-06-09,1,230-->

Wie wirkt sich eine Erhöhung der Varianz ($\sigma^2$) in einem [[Gauß-Kernel]] auf die Glättung einer Zeitreihe aus?
?
Eine höhere Varianz vergrößert die Bandbreite des Kernels. Dadurch werden weiter entfernte Zeitpunkte stärker in die Mittelwertbildung einbezogen, was zu einer glatteren Kurve führt, aber feine, kurzfristige Details (hochfrequente Signale) auslöscht.
<!--SR:!2026-06-09,1,230-->


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Varianz & Standardabweichung]]
SORT file.mtime DESC
```