#Note

2026-05-15

Tags: [[Statistik]], [[Bivariate Daten]], [[Kontingenz]], [[Deskriptive Statistik]]
#deskriptive_statistik

---
Die **Kontingenztabelle** (auch Kreuztabelle) ist das Standardinstrument zur Darstellung der gemeinsamen Häufigkeitsverteilung von zwei Merkmalen $X$ und $Y$. Sie wird primär für nominal- oder ordinalskalierte Daten verwendet.

### Aufbau der Tabelle

Ein Merkmal $X$ habe $k$ Ausprägungen (Zeilen), Merkmal $Y$ habe $m$ Ausprägungen (Spalten).

- **Zellenhäufigkeit ($n_{ij}$):** Anzahl der Beobachtungen, die gleichzeitig die Ausprägung $x_i$ und $y_j$ besitzen.
- **Randhäufigkeiten (Marginalwerte):**
    - Zeilensumme: $n_{i.} = \sum_{j=1}^m n_{ij}$ (Häufigkeit von $x_i$ ungeachtet von $Y$)
    - Spaltensumme: $n_{.j} = \sum_{i=1}^k n_{ij}$ (Häufigkeit von $y_j$ ungeachtet von $X$)

- **Gesamtzahl ($n$):** $\sum \sum n_{ij}$

### Bedingte Häufigkeiten

Um Zusammenhänge zu verstehen, betrachtet man die Verteilung eines Merkmals unter der Bedingung, dass das andere Merkmal fixiert ist:

- **Zeilenweise:** $h(y_j | x_i) = \frac{n_{ij}}{n_{i.}}$ (Wie verteilt sich $Y$ innerhalb der Gruppe $x_i$?)
- **Spaltenweise:** $h(x_i | y_j) = \frac{n_{ij}}{n_{.j}}$ (Wie verteilt sich $X$ innerhalb der Gruppe $y_j$?)

### Statistische Unabhängigkeit

Zwei Merkmale sind (empirisch) unabhängig, wenn die relativen Häufigkeiten in den Zellen dem Produkt der relativen Randhäufigkeiten entsprechen.

**Erwartete Häufigkeit ($e_{ij}$):** Der Wert, der bei perfekter Unabhängigkeit in der Zelle stehen müsste:

$$e_{ij} = \frac{n_{i.} \cdot n_{.j}}{n}$$

Die Differenz $(n_{ij} - e_{ij})$ ist die Basis für alle Kontingenzmaße (z.B. $\chi^2$-Test).

---

### Flashcards

Was versteht man unter den "Randhäufigkeiten" in einer Kontingenztabelle?::Die Summen der Zeilen ($n_{i.}$) bzw. Spalten ($n_{.j}$), welche die univariaten Verteilungen der einzelnen Merkmale $X$ und $Y$ repräsentieren.

Wie berechnet man die erwartete Häufigkeit $e_{ij}$ für eine Zelle bei Annahme der Unabhängigkeit?
?
$e_{ij} = \frac{\text{Zeilensumme} \cdot \text{Spaltensumme}}{\text{Gesamtzahl } n}$.

Warum sind absolute Zellhäufigkeiten ($n_{ij}$) oft schwer direkt zu vergleichen, wenn man nach Abhängigkeiten sucht?
?
Weil die Randhäufigkeiten (Gruppengrößen) meist unterschiedlich sind. Ein direkter Vergleich ist nur über **bedingte relative Häufigkeiten** (z. B. Prozentanteile innerhalb einer Zeile) sinnvoll, um den Einfluss der unterschiedlichen Gruppengrößen zu eliminieren.

Welche Bedingung muss für alle Zellen einer Kontingenztabelle erfüllt sein, damit $X$ und $Y$ als empirisch unabhängig gelten?
?
Für alle Zellen muss gelten: $n_{ij} = e_{ij}$. Das bedeutet, die beobachtete Häufigkeit entspricht exakt der theoretisch erwarteten Häufigkeit unter Unabhängigkeit. In der Praxis wird die Abweichung hiervon über den $\chi^2$-Koeffizienten gemessen.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Kontingenztabelle]]
SORT file.mtime DESC
```