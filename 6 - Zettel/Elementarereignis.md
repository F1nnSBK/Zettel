#Note

2026-05-19

Tags: [[Statistik]], [[Stochastik]], [[Wahrscheinlichkeitsrechnung]], [[Ereignis]]
#stochastik

---
Ein **Elementarereignis** ($\omega$) ist ein einzelner, unteilbarer Ausgang eines Zufallsexperiments. Es ist ein Element des Grundraums $\Omega$ ($\omega \in \Omega$).

### Elementarereignis vs. Zusammengesetztes Ereignis

- **Elementarereignis ($\omega$ oder $\{\omega\}$):** Der kleinstmögliche Ausgang.
    _Beispiel:_ Beim Werfen eines Spielwürfels ist das Würfeln einer „4“ ein Elementarereignis: $\omega_4 = 4$.
    
- **Zusammengesetztes Ereignis ($A$):** Eine Teilmenge des Grundraums ($A \subseteq \Omega$), die mehr als ein Elementarereignis enthalten kann. Es tritt ein, wenn eines der in ihm enthaltenen Elementarereignisse realisiert wird.
    _Beispiel:_ Das Ereignis „eine gerade Zahl würfeln“ ist $A = \{2, 4, 6\}$. Es setzt sich aus den drei Elementarereignissen $\omega_2, \omega_4$ und $\omega_6$ zusammen.


### Mathematische Präzisierung

In der fortgeschrittenen Stochastik unterscheidet man streng zwischen dem **[[Ergebnis]]** (dem Element $\omega$) und dem **Elementarereignis** (der einelementigen [[Menge]] $\{\omega\}$).

Da Wahrscheinlichkeiten historisch und mathematisch nur für _Mengen_ (Ereignisse) definiert sind, ordnet man die Wahrscheinlichkeit formal der Menge zu:

$$P(\{\omega\}) = p$$

Bei einem Laplace-Experiment mit einem endlichen [[Grundraum]] $\Omega$ hat jedes Elementarereignis die exakt gleiche Wahrscheinlichkeit:

$$P(\{\omega_i\}) = \frac{1}{|\Omega|}$$

### Flashcards

Was unterscheidet ein Elementarereignis fundamental von einem zusammengesetzten Ereignis?::Ein Elementarereignis besteht aus nur einem einzigen, nicht weiter zerlegbaren Ergebnis des Grundraums, während ein zusammengesetztes Ereignis eine Teilmenge aus mehreren Elementarereignissen ist.

Wie lässt sich das Ereignis "Würfeln einer Zahl größer als 4" ($A$) durch Elementarereignisse ausdrücken?::Als Vereinigungsmenge der einelementigen Mengen der Ergebnisse 5 und 6: $A = \{5\} \cup \{6\} = \{5, 6\}$.

Warum ist die Summe der Wahrscheinlichkeiten aller Elementarereignisse in einem endlichen Grundraum immer exakt 1?
?
Weil die Elementarereignisse paarweise disjunkt (unvereinbar) sind und ihre Vereinigung den gesamten Grundraum $\Omega$ ergibt. Nach den Kolmogorow-Axiomen gilt $P(\Omega) = 1$.

Welche Wahrscheinlichkeit besitzt ein einzelnes Elementarereignis bei einer stetigen Zufallsvariablen (z.B. exakte Körpergröße)?
?
Die Wahrscheinlichkeit ist exakt **0** ($P(\{\omega\}) = 0$). Bei stetigen Verteilungen können Wahrscheinlichkeiten nur für Intervalle (Flächen unter der Dichtefunktion) berechnet werden, nicht für isolierte Punkte.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Elementarereignis]]
SORT file.mtime DESC
```