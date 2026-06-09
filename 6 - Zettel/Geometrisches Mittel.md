#Note

2026-05-15

Tags: [[Statistik]], [[Deskriptive Statistik]], [[Lagemasse]], [[Wachstumsraten]]
#deskriptive_statistik

---
Das **geometrische Mittel** $\bar{x}_G$ wird verwendet, wenn die Merkmalswerte multiplikativ verknüpft sind. Dies ist typischerweise bei Wachstumsraten, Zinsfaktoren oder Indexzahlen der Fall.

### Die „geometrische“ Intuition

Warum heißt es „geometrisch“?

Stellen wir uns ein Rechteck mit den Seiten $x_1$ und $x_2$ vor. Die Fläche ist $A = x_1 \cdot x_2$. Suchen wir nun ein **Quadrat**, das exakt die gleiche Fläche besitzt, ist dessen Seitenlänge $\bar{x}_G$.

- Bei $n$ Dimensionen: Das geometrische Mittel ist die Seitenlänge eines $n$-dimensionalen **Hyperwürfels**, der das gleiche Volumen hat wie der Quader mit den Seiten $x_1, x_2, \dots, x_n$.

### Definition

Für $n$ positive Messwerte $x_i > 0$:

$$\bar{x}_G = \sqrt[n]{x_1 \cdot x_2 \cdot \dots \cdot x_n} = \left( \prod_{i=1}^n x_i \right)^{1/n}$$

### Anwendung bei Wachstumsraten

Wenn ein Bestand $B_0$ über $n$ Jahre mit den Faktoren $q_1, q_2, \dots, q_n$ wächst (z. B. $q=1,05$ für 5% Wachstum), dann ist der durchschnittliche Wachstumsfaktor:

$$\bar{q} = \sqrt[n]{q_1 \cdot q_2 \cdot \dots \cdot q_n}$$

Das Endkapital berechnet sich dann einfach über $B_n = B_0 \cdot \bar{q}^n$.

### Eigenschaften

- **Voraussetzung:** Alle $x_i$ müssen positiv sein ($x_i > 0$). Ein Wert von $0$ führt zu einem Mittelwert von $0$; negative Werte machen die Wurzelberechnung unmöglich (bzw. komplex).
- **Robustheit:** Es ist weniger empfindlich gegenüber extrem hohen Werten als das arithmetische Mittel, aber extrem empfindlich gegenüber Werten nahe Null.

---

### Flashcards

Warum ist das arithmetische Mittel für die Berechnung von Durchschnittsrenditen ungeeignet?::Das arithmetische Mittel ignoriert den Zinseszinseffekt. Multiplikative Veränderungen summieren sich nicht, sondern potenzieren sich; nur das geometrische Mittel bildet diesen Prozess korrekt ab.

Was ist die geometrische Interpretation des geometrischen Mittels zweier Werte $a$ und $b$?::Es repräsentiert die Seitenlänge eines Quadrats, dessen Flächeninhalt exakt dem des Rechtecks mit den Seiten $a$ und $b$ entspricht.
<!--SR:!2026-06-11,3,250-->

Warum darf das geometrische Mittel nicht berechnet werden, wenn ein Datenpunkt $0$ ist?
?
Da die Berechnung auf dem Produkt aller Werte basiert, würde eine einzige Null das gesamte Produkt zu Null machen ($\sqrt[n]{0} = 0$). Dies würde den Durchschnitt verfälschen, da eine $0$ in einer Wachstumsrate den Totalverlust bedeutet, was rechnerisch zwar korrekt, aber für die Analyse der restlichen Dynamik oft nicht zielführend ist.
<!--SR:!2026-06-09,1,230-->

Wie lautet der Zusammenhang zwischen dem geometrischen Mittel und Logarithmen?
?
Der Logarithmus des geometrischen Mittels ist gleich dem arithmetischen Mittel der Logarithmen der Einzelwerte:$$\log(\bar{x}_G) = \frac{1}{n} \sum_{i=1}^n \log(x_i)$$
<!--SR:!2026-06-09,1,230-->


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Geometrisches Mittel]]
SORT file.mtime DESC
```