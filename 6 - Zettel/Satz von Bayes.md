#Note

2026-05-19

Tags: [[Statistik]], [[Stochastik]], [[Wahrscheinlichkeitsrechnung]], [[Bayes]], [[Machine Learning]]
#stochastik

---
Der **Satz von Bayes** ist einer der bedeutendsten Sätze der Wahrscheinlichkeitsrechnung. Er verknüpft die bedingte Wahrscheinlichkeit zweier Ereignisse $A$ und $B$ in beide Richtungen.

### Mathematische Herleitung

Aus der Multiplikationsregel der [[Bedingte Wahrscheinlichkeit|bedingten Wahrscheinlichkeit]] wissen wir, dass die Schnittmenge symmetrisch ist:

$$P(A \cap B) = P(A \mid B) \cdot P(B) \quad \text{und} \quad P(A \cap B) = P(B \mid A) \cdot P(A)$$

Gleichsetzen und Auflösen nach $P(A \mid B)$ liefert das Theorem:

$$P(A \mid B) = \frac{P(B \mid A) \cdot P(A)}{P(B)}$$

### Interpretation im Machine Learning & Data Science

In der modernen KI-Forschung und Statistik werden den Termen feste Rollen zugewiesen:

$$\text{Posterior} = \frac{\text{Likelihood} \cdot \text{Prior}}{\text{Evidence}}$$

- **$P(A \mid B)$ (Posterior):** Die aktualisierte Wahrscheinlichkeit der Hypothese $A$, nachdem die Evidenz (Daten) $B$ beobachtet wurde.
    
- **$P(B \mid A)$ (Likelihood):** Die Wahrscheinlichkeit, dass die Daten $B$ auftreten, wenn die Hypothese $A$ wahr wäre.
    
- **$P(A)$ (Prior):** Die Ausgangswahrscheinlichkeit der Hypothese $A$ vor dem Experiment (Vorab-Wissen).
    
- **$P(B)$ (Evidence):** Die totale Wahrscheinlichkeit der Daten $B$ unter allen möglichen Hypothesen. Sie dient als Normierungskonstante.
    

### Praxis-Formel mit totaler Wahrscheinlichkeit

Da die absolute _Evidence_ $P(B)$ selten direkt bekannt ist, zerlegt man den Nenner meist über den Satz der totalen Wahrscheinlichkeit in die Summe aller bedingten Pfade (für den Fall zweier Ausprägungen $A$ und $\bar{A}$):

$$P(A \mid B) = \frac{P(B \mid A) \cdot P(A)}{P(B \mid A) \cdot P(A) + P(B \mid \bar{A}) \cdot P(\bar{A})}$$




---
#### Flashcards

Wie lautet die mathematische Formel des Satzes von Bayes?
?
$$P(A \mid B) = \frac{P(B \mid A) \cdot P(A)}{P(B)}$$

Wie heißen die vier Kernkomponenten des Bayes-Theorems in der ML-Terminologie?
?
$P(A \mid B)$ ist der Posterior, $P(B \mid A)$ die Likelihood, $P(A)$ der Prior und $P(B)$ die Evidence.

Was beschreibt das Phänomen des Basisraten-Fehlschlusses?
?
Die kognitive Verzerrung, bei der die bedingte Wahrscheinlichkeit eines Ereignisses (z. B. tatsächliche Erkrankung nach positivem Test) dramatisch überschätzt wird, weil die geringe Grundwahrscheinlichkeit des Ereignisses in der Bevölkerung (der Prior) vernachlässigt wird.

Welche Funktion erfüllt der Nenner $P(B)$ im Satz von Bayes?
?
Er repräsentiert die totale Wahrscheinlichkeit der beobachteten Daten (Evidence) über alle Hypothesen hinweg und fungiert als Normierungskonstante, damit die Summe aller Posterior-Wahrscheinlichkeiten exakt 1 ergibt.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Satz von Bayes]]
SORT file.mtime DESC
```