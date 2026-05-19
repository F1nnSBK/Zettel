#Note

2026-05-19

Tags: [[Statistik]], [[Stochastik]], [[Kombinatorik]], [[Abzählverfahren]]
#stochastik 

 
Kombinatorische Abzählverfahren dienen dazu, die Anzahl der möglichen Ausgänge eines Zufallsexperiments systematisch zu bestimmen. Sie liefern die mathematische Basis, um $|A|$ und $|\Omega|$ in [[Laplace-Wahrscheinlichkeit|Laplace-Modellen]] zu berechnen.

### 1. Permutation (Anordnung)

Es werden **alle** $n$ vorhandenen Elemente einer [[Menge]] neu angeordnet.
- **Ohne Wiederholung (alle Elemente unterscheidbar):**
    
    $$P_n = n! \quad (n\text{-Fakultät})$$
    
- **Mit Wiederholung (einige Elemente sind identisch):** Haben Gruppen von Elementen die gleichen Eigenschaften ($k_1, k_2, \dots$), muss die Gesamtfakultät um deren interne [[Permutationen]] bereinigt werden:
    
    $$P_n^{mit} = \frac{n!}{k_1! \cdot k_2! \dots}$$
    

### 2. Variation (Auswahl MIT Reihenfolge)

Es werden $k$ Elemente aus einer Menge von $n$ Elementen ausgewählt. Die **Reihenfolge** der Ziehung spielt eine Rolle (z. B. PIN-Code, Pferderennen).
- **Mit Zurücklegen:**
    
    $$V_n^{mit} = n^k$$
    
- **Ohne Zurücklegen:**
    
    $$V_n^{ohne} = \frac{n!}{(n-k)!}$$
    

### 3. Kombination (Auswahl OHNE Reihenfolge)

Es werden $k$ Elemente aus einer Menge von $n$ Elementen ausgewählt. Die **Reihenfolge** ist völlig egal (z. B. Lotto 49 aus 6, Teambildung).
- **Ohne Zurücklegen:** Berechnet über den **[[Binomialkoeffizienten]]** ("$n$ über $k$"):
    
    $$K_n^{ohne} = \binom{n}{k} = \frac{n!}{k!(n-k)!}$$
    
- **Mit Zurücklegen:**
    
    $$K_n^{mit} = \binom{n+k-1}{k}$$
    

### Flashcards

Wie unterscheidet sich eine Variation fundamental von einer Kombination?::Bei einer Variation spielt die Reihenfolge der gezogenen Elemente eine Rolle (z. B. PIN-Code), bei einer Kombination ist die Reihenfolge irrelevant (z. B. Lottozahlen).

Was berechnet der Binomialkoeffizient $\binom{n}{k}$ anschaulich?::Er berechnet die Anzahl der Möglichkeiten, $k$ Objekte aus einer Menge von $n$ Objekten auszuwählen, ohne Berücksichtigung der Reihenfolge und ohne Zurücklegen.

Wie viele Möglichkeiten gibt es, 5 Personen auf 5 nebeneinanderstehende Stühle zu setzen?
?
Es handelt sich um eine Permutation ohne Wiederholung von 5 Elementen:$$5! = 5 \cdot 4 \cdot 3 \cdot 2 \cdot 1 = 120 \text{ Möglichkeiten.}$$

Welche Formel nutzt man für das Ziehen von $k$ aus $n$ Elementen mit Berücksichtigung der Reihenfolge, wenn gezogene Elemente wieder zurückgelegt werden?
?
Die Formel lautet $n^k$ (Variation mit Zurücklegen).



---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Abzählverfahren]]
SORT file.mtime DESC
```