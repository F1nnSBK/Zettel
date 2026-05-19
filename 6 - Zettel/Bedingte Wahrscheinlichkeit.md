#Note

2026-05-19

Tags: [[Statistik]], [[Stochastik]], [[Wahrscheinlichkeitsrechnung]], [[Satz von Bayes]]
#stochastik 

---
Die **bedingte Wahrscheinlichkeit** berechnet die Wahrscheinlichkeit des Eintreffens eines Ereignisses $A$ unter der Voraussetzung (Bedingung), dass das Ereignis $B$ bereits eingetreten ist. Man schreibt dies als $P(A \mid B)$ (gelesen: „Wahrscheinlichkeit von $A$ gegeben $B$“).

### Mathematische Definition

Für zwei Ereignisse $A$ und $B$ mit $P(B) > 0$ gilt:

$$P(A \mid B) = \frac{P(A \cap B)}{P(B)}$$

### Anschauliche Interpretation: Der schrumpfende [[Grundraum]]

Bei der normalen Wahrscheinlichkeit $P(A)$ ist die Bezugsgröße das gesamte Universum $\Omega$.

Sobald wir wissen, dass $B$ eingetreten ist, wird $B$ zu unserem neuen, eingeschränkten Universum. Elemente außerhalb von $B$ können nicht mehr eintreten. Ein Erfolg für das Ereignis $A$ ist jetzt nur noch in der Schnittmenge $A \cap B$ möglich.

### Die Multiplikationsregel

Durch Umstellung der Definitionsgleichung erhält man die Multiplikationsregel für stochastische Verknüpfungen. Sie ist die Basis für das Rechnen entlang von Pfaden in **Baumdiagrammen**:

$$P(A \cap B) = P(A \mid B) \cdot P(B)$$

### Wichtige Eigenschaften

- **Satz der totalen Wahrscheinlichkeit:** Erlaubt es, die Gesamtwahrscheinlichkeit eines Ereignisses $A$ aus den bedingten Wahrscheinlichkeiten bezüglich einer disjunkten Zerlegung des Grundraums (z. B. $B$ und $\bar{B}$) zu rekonstruieren:
$$P(A) = P(A \mid B) \cdot P(B) + P(A \mid \bar{B}) \cdot P(\bar{B})$$




---
### Flashcards

Wie lautet die formale Definition der bedingten Wahrscheinlichkeit $P(A \mid B)$?
?$$P(A \mid B) = \frac{P(A \cap B)}{P(B)} \quad \text{für } P(B) > 0$$

Was passiert anschaulich mit dem Grundraum $\Omega$ bei der Berechnung einer bedingten Wahrscheinlichkeit $P(A \mid B)$?::Der Grundraum schrumpft komplett auf das Ereignis $B$ zusammen. Alle Ergebnisse außerhalb von $B$ werden für die relative Berechnung ignoriert.

Warum ist $P(A \mid B)$ im Allgemeinen nicht das Gleiche wie $P(A \cap B)$?
?
$P(A \cap B)$ misst die Wahrscheinlichkeit, dass beide Ereignisse gleichzeitig eintreten, bezogen auf den _gesamten_ Grundraum $\Omega$. $P(A \mid B)$ misst denselben Erfolg, bezieht sich aber ausschließlich auf den _Teilraum_ $B$.

Ein fairer Würfel wird geworfen. Wie hoch ist die Wahrscheinlichkeit eine 6 zu würfeln ($A$), gegeben das Ergebnis ist eine gerade Zahl ($B$)?
?
$\Omega = \{1,2,3,4,5,6\}$, Gerade Zahlen: $B = \{2,4,6\} \implies P(B) = \frac{3}{6}$. Schnittmenge $A \cap B = \{6\} \implies P(A \cap B) = \frac{1}{6}$.

$$P(A \mid B) = \frac{1/6}{3/6} = \frac{1}{3} \quad (\approx 33,3\%)$$


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Bedingte Wahrscheinlichkeit]]
SORT file.mtime DESC
```