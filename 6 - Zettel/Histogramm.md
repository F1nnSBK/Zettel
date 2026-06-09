#Note

2026-05-18

Tags: [[Statistik]], [[Visualisierung]], [[Deskriptive Statistik]], [[Diagramme für Häufigkeiten]]
#deskriptive_statistik

---
Das **Histogramm** ist das Standardwerkzeug zur Visualisierung von **klassierten, stetigen Daten**. Im Gegensatz zum Säulendiagramm berühren sich die Balken hier immer, um die Kontinuität des Merkmalsraums darzustellen.

### Das Prinzip der Flächenproportionalität

Die goldene Regel lautet:

$$\text{Fläche} = \text{Häufigkeit}$$

Dies ist unproblematisch, solange alle Klassen $K_i$ die gleiche Breite $b_i$ haben. Sobald die Klassen jedoch unterschiedlich breit sind (z. B. Einkommensklassen: 0-1000, 1000-5000, 5000-20000), muss die Höhe korrigiert werden.

### Die Dichtekorrektur

Um die Korrektheit der Fläche zu wahren, berechnet man die **Häufigkeitsdichte** (oder Rechteckhöhe) $h_i$:

$$h_i = \frac{f_i}{b_i}$$

_(wobei $f_i$ die Häufigkeit und $b_i$ die Breite der Klasse $i$ ist)_

Durch diese Korrektur wird sichergestellt, dass breite Klassen nicht allein durch ihre Ausdehnung auf der x-Achse eine Dominanz vortäuschen, die sie in den Daten nicht besitzen.

### Implementation

```Python
import matplotlib.pyplot as plt
import numpy as np

# Example data: skewed distribution
data = np.random.lognormal(mean=0.0, sigma=0.5, size=1000)

# 1. Standard Histogram (Equal bins)
plt.figure(figsize=(10, 4))
plt.subplot(1, 2, 1)
plt.hist(data, bins=20, color='skyblue', edgecolor='black')
plt.title("Equal Class Widths")
plt.xlabel("Value")
plt.ylabel("Frequency (Height)")

# 2. Manual Unequal Bins with Density Correction
plt.subplot(1, 2, 2)
custom_bins = [0, 0.5, 1.0, 2.0, 5.0]
# density=True ensures the area sums to 1
plt.hist(data, bins=custom_bins, density=True, color='salmon', edgecolor='black')
plt.title("Unequal Widths (Density Corrected)")
plt.xlabel("Value")
plt.ylabel("Density (Area = 1)")

plt.tight_layout()
plt.show()
```

---
### Flashcards

Was ist der fundamentale Unterschied zwischen einem Säulendiagramm und einem Histogramm?::Beim Säulendiagramm repräsentiert die Höhe die Häufigkeit; beim Histogramm repräsentiert die Fläche die Häufigkeit.
<!--SR:!2026-06-09,1,230-->

Warum ist eine Dichtekorrektur bei ungleichen Klassenbreiten zwingend erforderlich?::Ohne Korrektur würden breitere Klassen bei gleicher Höhe eine viel größere Fläche einnehmen. Das menschliche Auge interpretiert Fläche als Masse, was zu einer massiven optischen Überbewertung breiter Klassen führen würde.
<!--SR:!2026-06-09,1,230-->

Wie berechnet man die Höhe $h_i$ eines Balkens im Histogramm bei relativen Häufigkeiten $r_i$ und Klassenbreite $b_i$?
?
$h_i = \frac{r_i}{b_i}$. Die resultierende Einheit auf der y-Achse ist "Prozent pro Einheit der x-Achse" (Dichte).

Was passiert mit der Gesamtsumme der Flächen aller Balken, wenn man ein Histogramm mit relativen Häufigkeiten (Dichte-Modus) zeichnet?
?
Die Summe aller Flächen ergibt exakt **1** (oder 100 %). Dies entspricht der Eigenschaft einer Wahrscheinlichkeitsdichtefunktion.
<!--SR:!2026-06-12,4,270-->



---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Histogramm]]
SORT file.mtime DESC
```