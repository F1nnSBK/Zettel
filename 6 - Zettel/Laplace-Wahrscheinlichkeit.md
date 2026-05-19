#Note

2026-05-19

Tags: [[Statistik]], [[Stochastik]], [[Wahrscheinlichkeitsrechnung]], [[Laplace]]
#stochastik 

---
Die **Laplace-Wahrscheinlichkeit** (auch klassische Wahrscheinlichkeit) bildet das historische Fundament der Stochastik. Sie quantifiziert Gewinnchancen bei idealen Zufallsexperimenten (Glücksspielen).

### Voraussetzungen des Laplace-Modells

Ein Zufallsexperiment wird genau dann als Laplace-Experiment bezeichnet, wenn:

1. Die Ergebnismenge $\Omega$ **endlich** ist ($|\Omega| < \infty$).
    
2. Alle Elementarereignisse $\omega_i \in \Omega$ die **exakt gleiche Wahrscheinlichkeit** besitzen.
    

Daraus folgt zwingend für jedes Elementarereignis:

$$P(\{\omega_i\}) = \frac{1}{|\Omega|}$$

### Die Laplace-Formel

Für ein zusammengesetztes Ereignis $A \subseteq \Omega$ berechnet sich die Wahrscheinlichkeit als Quotient aus der Anzahl der für $A$ günstigen Ergebnisse und der Anzahl aller möglichen Ergebnisse im Grundraum:

$$P(A) = \frac{|A|}{|\Omega|} = \frac{\text{Anzahl der günstigen Ergebnisse (Fälle)}}{\text{Anzahl der möglichen Ergebnisse (Fälle)}}$$

### Der Brückenschlag zur Kombinatorik

In einfachen Beispielen (Würfel, Münze) lassen sich $|A|$ und $|\Omega|$ direkt ablesen. Bei komplexeren Problemen (z. B. "Wie hoch ist die Wahrscheinlichkeit, beim Poker ein Full House zu bekommen?") versagt direktes Abzählen. Hier müssen die **Kombinatorischen Abzählverfahren** genutzt werden, um die Mächtigkeiten $|A|$ und $|\Omega|$ mathematisch zu bestimmen.

### Grenzen des Modells

Das Laplace-Modell ist blind für:

- **Unendliche Grundräume:** (Stetige Zufallsvariablen wie Messfehler, Wartezeiten).
    
- **Asymmetrische Prozesse:** (Wettervorhersagen, Überlebenswahrscheinlichkeiten in der Medizin, Aktienkurse), bei denen Ergebnisse von Natur aus ungleiche Wahrscheinlichkeiten besitzen. Hier greift stattdessen der _empirische (frequentistische) Wahrscheinlichkeitsbegriff_.
    

### Flashcards

Wie lautet die mathematische Definition der Laplace-Wahrscheinlichkeit für ein Ereignis $A$?
?
$P(A) = \frac{|A|}{|\Omega|}$ (Mächtigkeit der Menge der günstigen Fälle dividiert durch die Mächtigkeit des gesamten Grundraums).

Welche zwei Bedingungen müssen erfüllt sein, um die klassische Laplace-Formel anwenden zu dürfen?::Der Grundraum $\Omega$ muss endlich sein und alle Elementarereignisse müssen zwingend die gleiche Eintrittswahrscheinlichkeit besitzen (Symmetrie).

Warum kann die Wahrscheinlichkeit für das Eintreffen von Regen morgen nicht mit dem Laplace-Modell berechnet werden?
?
Weil die beiden möglichen Ergebnisse ($\Omega = \{\text{Regen}, \text{kein Regen}\}$) in der Realität nicht gleichwahrscheinlich (asymmetrisch) sind. Das Wetter wird durch komplexe meteorologische Gesetzmäßigkeiten bestimmt, nicht durch ein symmetrisches Zufallsgerät.

Wie hoch ist die Laplace-Wahrscheinlichkeit, bei einem fairen sechsseitigen Würfel eine Primzahl zu würfeln?
?
Günstige Fälle: $A = \{2, 3, 5\} \implies |A| = 3$. Mögliche Fälle: $|\Omega| = 6$.$$P(A) = \frac{3}{6} = 0,5 \quad (50\%)$$

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Laplace-Wahrscheinlichkeit]]
SORT file.mtime DESC
```