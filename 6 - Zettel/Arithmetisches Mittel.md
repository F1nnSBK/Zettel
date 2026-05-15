#Note

2026-05-15

Tags: [[Statistik]], [[Deskriptive Statistik]], [[Lagemasse]], [[Arithmetisches Mittel]], [[Momente]], [[Smoothing]]
#deskriptive_statistik 

---
Das **arithmetische Mittel** (Durchschnitt) ist das am häufigsten verwendete Lagemaß für metrisch skalierte Daten. Es repräsentiert den Wert, den alle Beobachtungen hätten, wenn die Gesamtsumme gleichmäßig auf alle Merkmalsträger verteilt wäre.

### Definition

Für eine Urliste $x_1, x_2, \dots, x_n$:

$$\bar{x} = \frac{1}{n} \sum_{i=1}^n x_i$$

### Das gewichtete arithmetische Mittel

Wenn Daten in gruppierter Form (Häufigkeitstabelle) vorliegen oder Gruppen unterschiedlich stark gewichtet werden sollen:

$$\bar{x}_w = \frac{\sum_{i=1}^k w_i \cdot x_i}{\sum_{i=1}^k w_i}$$

Hierbei steht $w_i$ für die absolute Häufigkeit $n_i$ oder ein spezifisches Gewicht.

### Wichtige Eigenschaften

1. **Schwerpunkteigenschaft:** Die Summe der Abweichungen aller Messwerte vom Mittelwert ist immer Null:
$$\sum_{i=1}^n (x_i - \bar{x}) = 0$$

2. **Minimale quadratische Abweichung:** Die Summe der quadrierten Abweichungen wird genau dann minimal, wenn sie am arithmetischen Mittel berechnet wird:

$$\sum (x_i - a)^2 \rightarrow \min \quad \text{für} \quad a = \bar{x}$$

3. **Lineare Transformation:** Wenn $y_i = a + b \cdot x_i$, dann gilt für den Mittelwert:
$$\bar{y} = a + b \cdot \bar{x}$$

### Kritik und Grenzen

- **Metrische Skala:** Erfordert zwingend Intervall- oder Verhältnisskala.
- **Ausreißerempfindlichkeit:** Ein einziger extrem hoher oder niedriger Wert kann den Mittelwert so stark verzerren, dass er nicht mehr repräsentativ für die "Masse" der Daten ist.

---

### Flashcards

Was beschreibt die Schwerpunkteigenschaft des arithmetischen Mittels mathematisch?::Die Summe aller Differenzen zwischen den Einzelwerten und dem Mittelwert ist Null: $\sum (x_i - \bar{x}) = 0$.

Warum ist das arithmetische Mittel für nominalskalierte Daten (z. B. Geschlecht) nicht definiert?::Da nominale Daten keine numerische Bedeutung haben, ist eine Summenbildung ($\sum x_i$) mathematisch sinnlos. Es existiert keine "Durchschnittsfarbe" oder ein "Durchschnittsgeschlecht" auf Basis von Addition.

Wie reagiert das arithmetische Mittel auf eine lineare Transformation der Daten (z.B. Umrechnung von Celsius in Fahrenheit)?
?
Vollkommen linear. Wenn jeder Wert $x$ mit einem Faktor $b$ multipliziert und um $a$ erhöht wird, verändert sich der Mittelwert exakt nach der gleichen Formel: $\bar{y} = a + b \cdot \bar{x}$.

In welcher Situation liefert das gewichtete arithmetische Mittel ein anderes Ergebnis als das einfache Mittel der Gruppenmittelwerte?
?
Immer dann, wenn die zugrunde liegenden Gruppen unterschiedliche Fallzahlen ($n_i$) haben. Das einfache Mittel würde kleine Gruppen überrepräsentieren; das gewichtete Mittel stellt sicher, dass jeder Einzeldatenpunkt den gleichen Einfluss auf das Gesamtergebnis hat.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Arithmetisches Mittel]]
SORT file.mtime DESC
```