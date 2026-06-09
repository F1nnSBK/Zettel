#Note

2026-05-15

Tags: [[Statistik]], [[Bivariate Daten]], [[Kontingenz]], [[Deskriptive Statistik]]
#deskriptive_statistik

---
Der **Kontingenzkoeffizient** quantifiziert die Stärke des statistischen Zusammenhangs zwischen zwei kategorialen Variablen in einer [[Kontingenztabelle]].

### Die $\chi^2$-Statistik ([[Chi-Quadrat]])

$\chi^2$ summiert die quadrierten normierten Abweichungen zwischen den beobachteten Häufigkeiten ($n_{ij}$) und den bei Unabhängigkeit erwarteten Häufigkeiten ($e_{ij}$):

$$\chi^2 = \sum_{i=1}^k \sum_{j=1}^m \frac{(n_{ij} - e_{ij})^2}{e_{ij}}$$

- $\chi^2 = 0 \implies$ Perfekte Unabhängigkeit.
- Je größer $\chi^2$, desto stärker die Abweichung von der Unabhängigkeit.

### Pearsons Kontingenzkoeffizient ($C$)

Da $\chi^2$ mit der Stichprobengröße $n$ wächst, wird es für $C$ normiert:

$$C = \sqrt{\frac{\chi^2}{\chi^2 + n}}$$

- **Nachteil:** Die theoretische Obergrenze von $C$ ist $C_{max} = \sqrt{\frac{M-1}{M}}$ (mit $M = \min(k, m)$). Er erreicht bei quadratischen Tabellen nie die 1.

### Korrigierter Kontingenzkoeffizient ($C_{korr}$)

Um die Vergleichbarkeit zu gewährleisten, wird $C$ an seiner maximal möglichen Obergrenze relativiert:

$$C_{korr} = \frac{C}{C_{max}}$$

- $C_{korr} \in [0, 1]$. Ein Wert von 1 bedeutet nun tatsächlich einen perfekten Zusammenhang.

### Cramérs V

In der aktuellen Forschung wird häufig Cramérs V bevorzugt, da es mathematisch eleganter normiert:

$$V = \sqrt{\frac{\chi^2}{n \cdot (\min(k, m) - 1)}}$$

- $V=0$: Kein Zusammenhang.
- $V=1$: Perfekter Zusammenhang.

---

### Flashcards

Warum ist Cramérs V gegenüber dem einfachen $\chi^2$-Wert vorzuziehen?::Der $\chi^2$-Wert ist abhängig von der Stichprobengröße $n$. Cramérs V normiert diesen Wert auf ein Intervall von $[0, 1]$, was die Interpretation der Zusammenhangsstärke unabhängig von $n$ und der Tabellengröße ermöglicht.

Wie berechnet man die maximale Obergrenze $C_{max}$ für Pearsons Kontingenzkoeffizienten in einer $3 \times 5$ Tabelle?
?
$M = \min(3, 5) = 3$.
<!--SR:!2026-06-08,0,230-->$$C_{max} = \sqrt{\frac{M-1}{M}} = \sqrt{\frac{3-1}{3}} = \sqrt{\frac{2}{3}} \approx 0,816$$

Was bedeutet ein Kontingenzkoeffizient von $C = 0$?::Es besteht kein empirischer Zusammenhang zwischen den beiden Merkmalen; die beobachteten Häufigkeiten entsprechen exakt den unter Unabhängigkeit erwarteten Häufigkeiten.
<!--SR:!2026-06-09,1,230-->

Welches Skalenniveau ist die Mindestanforderung für die Berechnung von Kontingenzkoeffizienten?
?
Das **Nominalskalenniveau**. Da nur Häufigkeiten in Kategorien verglichen werden, ist weder eine Rangfolge noch eine Metrik erforderlich.
<!--SR:!2026-06-09,1,230-->


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Kontingenzkoeffizient]]
SORT file.mtime DESC
```