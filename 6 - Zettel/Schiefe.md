#Note

2026-05-15

Tags: [[Statistik]], [[Deskriptive Statistik]], [[Normalverteilung]], [[Momente]], [[Hypothesentest]]
#deskriptive_statistik

---
Die **Schiefe** (Skewness) ist ein Maß für die Asymmetrie einer Wahrscheinlichkeitsverteilung. Sie gibt an, ob die Masse der Daten links oder rechts vom Zentrum konzentriert ist.

### Arten der Schiefe

1. **Symmetrisch (Skewness ≈ 0):** Linke und rechte Seite sind Spiegelbilder (z. B. Normalverteilung).
    - Mittelwert $\approx$ Median $\approx$ Modus.
2. **Rechtsschief / Linkssteil (Skewness > 0):** Der „Schwanz“ der Verteilung zieht sich nach rechts zu hohen Werten (z. B. Einkommensverteilung).
    - **Reihenfolge:** Modus < Median < Mittelwert
3. **Linksschief / Rechtssteil (Skewness < 0):** Der „Schwanz“ zieht sich nach links zu kleinen Werten (z. B. Alter bei Renteneintritt).
    - **Reihenfolge:** Mittelwert < Median < Modus.

### Mathematische Definition (Momentenkoeffizient)

Um die Schiefe unabhängig von der Maßeinheit zu machen, wird das dritte zentrale Moment durch die Standardabweichung hoch 3 normiert:

$$g_1 = \frac{1}{n} \sum_{i=1}^n \left( \frac{x_i - \bar{x}}{s} \right)^3$$

### Schiefe in statistischen Tests

Die Schiefe ist ein kritischer Indikator für die Prüfung auf Normalverteilung. Es gibt spezialisierte Tests, die die Schiefe explizit nutzen:

- **Jarque-Bera-Test:** Prüft gleichzeitig, ob Schiefe ($S$) und Wölbung ($K$) mit einer Normalverteilung ($S=0, K=3$) vereinbar sind.
$$JB = \frac{n}{6} \left( S^2 + \frac{1}{4}(K-3)^2 \right)$$
	Liegt der JB-Wert über einem kritischen Schwellenwert, wird die Nullhypothese (Daten sind normalverteilt) verworfen.

- **Shapiro-Wilk-Test:** Gilt als mächtigster Test für kleine Stichproben ($n < 50$), reagiert aber extrem sensibel auf jede Form von Asymmetrie.

### Behandlung in der Daten-Pipeline

In der Data Science führt eine hohe Schiefe oft zu Problemen bei Modellen, die auf euklidischen Distanzen oder quadratischen Fehlern basieren.

- **Log-Transformation:** $y = \log(x)$ (Reduziert Rechtsschiefe massiv).
- **Square-Root Transformation:** $y = \sqrt{x}$ (Moderater Effekt).
- **Box-Cox Transformation:** Sucht automatisch den optimalen Exponenten $\lambda$ zur Symmetrisierung.

---

### Flashcards

Warum führt eine rechtsschiefe Verteilung dazu, dass das arithmetische Mittel größer als der Median ist?::Die extrem hohen Werte im rechten "Schwanz" der Verteilung ziehen das arithmetische Mittel aufgrund der Summierung stark nach oben, während der Median als Lagemaß stabil in der Mitte der geordneten Reihe bleibt.

Welcher statistische Test nutzt explizit die Schiefe und die Wölbung zur Prüfung auf Normalverteilung? :: Der **Jarque-Bera-Test**.
<!--SR:!2026-06-09,1,230-->

Was ist das Ziel einer Log-Transformation bei rechtsschiefen Daten im Machine Learning?
?
Die Transformation staucht große Werte stärker zusammen als kleine, wodurch die Verteilung symmetrischer (normalverteilungsähnlicher) wird. Dies verbessert die Schätzgenauigkeit von Modellen, die konstante Fehlervarianzen (Homoskedastizität) voraussetzen.

Warum ist ein reiner Blick auf die Schiefe nicht ausreichend, um eine Normalverteilung zu bestätigen?
?
Eine Verteilung kann perfekt symmetrisch sein (Schiefe = 0), aber dennoch eine extreme Wölbung (Kurtosis) aufweisen (z. B. t-Verteilung mit wenigen Freiheitsgraden). Erst die Kombination aus Schiefe und Wölbung erlaubt eine fundierte Aussage über die Verteilungsform.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Schiefe]]
SORT file.mtime DESC
```