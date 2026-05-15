#Note

2026-05-15

Tags: [[Statistik]], [[Mathematik]], [[Feature Scaling]], [[Deskriptive Statistik]], [[Machine Learning]]
#deskriptive_statistik

---
Die **lineare Transformation** beschreibt die Umrechnung von Merkmalswerten $x_i$ in neue Werte $y_i$ durch eine lineare Funktion. Dies ist in der Praxis essenziell für Währungsumrechnungen, Einheitenwechsel (km zu Meilen) oder die Normalisierung in ML-Pipelines.

### Die Transformationsgleichung

$$y_i = a + b \cdot x_i$$

- **$a$ (Translation):** Verschiebung des Nullpunkts.
- **$b$ (Skalierung):** Streckung oder Stauchung der Intervalle.

### Auswirkungen auf statistische Kennzahlen

Nach Jeske gelten folgende Regeln für die Transformation:

1. **Lagemaße (Mittelwert, Median, Quartile):**
    Sie verhalten sich vollkommen analog zur Transformation:
        $$\bar{y} = a + b \cdot \bar{x}$$
    
2. **Streuungsmaße:**
    
    - **Varianz:** Reagiert nur auf $b$, und zwar quadratisch: $s_y^2 = b^2 \cdot s_x^2$.
    - **Standardabweichung:** Reagiert linear auf den Betrag von $b$: $s_y = |b| \cdot s_x$.
    - **Spannweite/IQR:** Reagieren ebenfalls nur auf $|b|$.
3. **Formmaße (Schiefe, Wölbung) & Korrelation:**

    Diese Maße sind **invariant** gegenüber linearen Transformationen (solange $b > 0$). Sie beschreiben die reine Struktur der Daten, die durch Skalierung nicht verändert wird.

### Spezialfall: Standardisierung (Z-Transformation)

In der Datenwissenschaft ist dies die häufigste Anwendung. Hierbei wählt man $a = -\frac{\bar{x}}{s_x}$ und $b = \frac{1}{s_x}$:

$$z_i = \frac{x_i - \bar{x}}{s_x}$$

**Ergebnis:** Die neue Variable $Z$ hat immer den Mittelwert $0$ und die Varianz $1$. Dies macht Variablen mit unterschiedlichen Einheiten (z. B. Alter in Jahren und Einkommen in Euro) vergleichbar.

---

### Flashcards

Wie verändert sich das arithmetische Mittel $\bar{x}$, wenn alle Werte mit 10 multipliziert und danach um 5 erhöht werden?::Das neue Mittel $\bar{y}$ ist ebenfalls das 10-fache des alten Mittels plus 5 ($\bar{y} = 10 \cdot \bar{x} + 5$).

Warum hat der additive Term $a$ keinen Einfluss auf die Standardabweichung?::Die Standardabweichung misst die Distanzen zwischen den Werten. Wenn man alle Werte um denselben Betrag $a$ verschiebt, bleiben die Abstände zwischen den Werten absolut identisch.

Welchen Mittelwert und welche Varianz besitzt eine Variable nach einer erfolgreichen Z-Transformation?
?
Der Mittelwert ist immer **0** und die Varianz (sowie die Standardabweichung) ist immer **1**.

Wie wirkt sich eine Multiplikation aller Datenpunkte mit $b = -2$ auf die Varianz aus?
?
Die Varianz vergrößert sich um den Faktor $b^2$, also um den Faktor **4**. Da Abweichungen quadriert werden, verschwindet das negative Vorzeichen.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Lineare Transformation]]
SORT file.mtime DESC
```