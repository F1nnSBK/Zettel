#Note

2026-05-15

Tags: [[Statistik]], [[Deskriptive Statistik]], [[Quantile]], [[Lagemasse]]
#deskriptive_statistik

---
Quantile sind Lagemaße, die eine sortierte Datenreihe in bestimmte Anteile zerlegen. Sie sind das zentrale Werkzeug zur Beschreibung von Verteilungen, insbesondere wenn diese nicht symmetrisch sind oder Ausreißer enthalten.

### Definition

Das $p$-Quantil $x_p$ (mit $0 < p < 1$) ist der Wert, für den gilt:
- Mindestens ein Anteil $p$ der Daten ist kleiner oder gleich $x_p$.
- Mindestens ein Anteil $1-p$ der Daten ist größer oder gleich $x_p$.
    
### Wichtige Spezialfälle (Quartile)

Quartile teilen die Daten in vier Viertel (25%-Schritte):
- **$Q_1$ (Unteres Quartil):** $p=0,25 \rightarrow$ 25% der Daten sind $\le Q_1$.
- **$Q_2$ (Median):** $p=0,50 \rightarrow$ 50% der Daten sind $\le Q_2$.
- **$Q_3$ (Oberes Quartil):** $p=0,75 \rightarrow$ 75% der Daten sind $\le Q_3$.

- **Interquartilsabstand (IQR):** $IQR = Q_3 - Q_1$. Er beschreibt die Breite der mittleren 50% der Daten und ist die Basis für die Ausreißer-Definition im [[Boxplot]].
    

### Berechnung (diskrete Daten)

Gegeben ist eine sortierte Urliste $x_{(1)}, x_{(2)}, ..., x_{(n)}$.
Berechne zuerst den Index $j = n \cdot p$:

1. **Fall: $j$ ist nicht ganzzahlig:**
    Nimm den nächsthöheren ganzzahligen Index $k = \lceil j \rceil$.

$$x_p = x_{(k)}$$
    
2. **Fall: $j$ ist ganzzahlig:**
    Das Quantil ist das arithmetische Mittel aus dem $j$-ten und dem nächsten Wert.

$$x_p = \frac{1}{2} (x_{(j)} + x_{(j+1)})$$


---
#### Flashcards

Warum ist das 0,5-Quantil (Median) robuster gegenüber Ausreißern als das arithmetische Mittel?::Da der Median nur auf der Rangordnung basiert. Ein extrem hoher Ausreißer verändert zwar den Wert am Ende der Liste, aber nicht die Position des mittleren Elements. Das arithmetische Mittel hingegen wird durch den hohen Wert direkt im Zähler der Summe $\sum x_i$ beeinflusst.

Wie berechnet man das 0,25-Quantil ($Q_1$) bei einer Stichprobe von $n=10$?
?
1. $j = n \cdot p = 10 \cdot 0,25 = 2,5$.

2. Da $j$ nicht ganzzahlig ist, wird aufgerundet: $k = 3$.

3. Ergebnis: $Q_1 = x_{(3)}$ (der dritte Wert der sortierten Liste).

Was beschreibt der Interquartilsabstand (IQR) im Kontext einer Verteilung?
?
Der $IQR = Q_3 - Q_1$ gibt die Spannweite an, in der sich die zentralen 50% der Beobachtungen befinden. Er ist ein Streuungsmaß, das unempfindlich gegenüber Extremwerten an den Rändern der Verteilung ist.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Quantile]]
SORT file.mtime DESC
```