#Note

2026-05-15

Tags: [[Machine Learning]], [[Deep Tech]], [[Mathematik]], [[Kernel Methods]], [[SVM]], [[RBF]]
#supervised_learning

---
Der **Gauß-Kernel**, auch bekannt als **Radial Basis Function (RBF) Kernel**, ist eines der mächtigsten Werkzeuge im Bereich des Machine Learning und der Signalverarbeitung. Er dient als Maß für die lokale Ähnlichkeit zwischen zwei Vektoren.

### Mathematische Definition

Für zwei Vektoren $x$ und $x'$ ist der Gauß-Kernel definiert als:

$$K(x, x') = \exp\left( -\frac{||x - x'||^2}{2\sigma^2} \right)$$

Oft wird auch die Parametrisierung mit $\gamma = \frac{1}{2\sigma^2}$ verwendet:

$$K(x, x') = \exp(-\gamma ||x - x'||^2)$$

### Kernkonzepte & Mechanik

1. **Lokale Wirkung:** Der Wert des Kernels sinkt exponentiell mit steigender euklidischer Distanz. Punkte außerhalb eines Radius von ca. $3\sigma$ haben praktisch keinen Einfluss mehr auf die Berechnung.
2. **Die Rolle von $\sigma$ (Bandbreite):** - Ein **kleines $\sigma$** macht den Kernel "spitz". Nur sehr nahe Nachbarn werden berücksichtigt (Gefahr von Overfitting/Rauschen).
    - Ein **großes $\sigma$** macht den Kernel "flach". Die Gewichtung wird globaler, lokale Details gehen verloren (Smoothing).
    
3. **Invarianz:** Der Kernel ist translationsinvariant, da er nur vom Differenzvektor $x - x'$ abhängt.

### Einsatzgebiete

- **Support Vector Machines (SVM):** Projiziert Daten implizit in einen unendlichdimensionalen Raum, um nicht-lineare Trennbarkeit zu ermöglichen.
- **Kernel Density Estimation (KDE):** Schätzung einer Wahrscheinlichkeitsdichtefunktion durch Überlagerung von Gauß-Glocken an jedem Datenpunkt.
- **Gaussian Processes (GP):** Dient als Kovarianzfunktion, die festlegt, wie stark Vorhersagen an verschiedenen Stellen korreliert sind.
- **Bildverarbeitung (Gaussian Blur):** Glättung von Pixelwerten durch Faltung mit einer Gauß-Matrix zur Rauschunterdrückung.


---

### Flashcards

Warum führt der Gauß-Kernel (RBF) zu einem unendlichdimensionalen Merkmalsraum?::Da die Exponentialfunktion eine unendliche Taylor-Reihe besitzt ($\exp(x) = \sum \frac{x^n}{n!}$), enthält das Skalarprodukt im Kernel-Raum Polynome jeder beliebigen Ordnung, was einem unendlichdimensionalen Feature-Vektor entspricht.

Wie wirkt sich eine Erhöhung des Parameters $\sigma$ auf die Glätte einer KDE-Schätzung aus?::Ein größeres $\sigma$ erhöht die Bandbreite, wodurch die einzelnen "Glocken" breiter werden und stärker verschmelzen. Die resultierende Dichteschätzung wird glatter (höherer Bias), verliert aber Details über lokale Maxima (geringere Varianz).

Was ist der Vorteil des Gauß-Kernels gegenüber einem einfachen linearen Kernel in einer SVM?
?
Der Gauß-Kernel kann komplexe, nicht-lineare Entscheidungsgrenzen (z. B. umschlossene Cluster oder Spiralen) lernen, da er Ähnlichkeit lokal bewertet und Daten in einen Raum transformiert, in dem sie linear trennbar werden.

Was passiert mathematisch mit dem Kernel-Wert $K(x, x')$, wenn die Distanz zwischen zwei Punkten gegen Unendlich strebt?
?
Der Wert nähert sich asymptotisch der Null an ($\lim_{||x-x'|| \to \infty} K(x, x') = 0$). Dies sorgt für die lokale Eigenschaft des Kernels, da weit entfernte Punkte keinen Einfluss auf die lokale Schätzung haben.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Gauß-Kernel]]
SORT file.mtime DESC
```