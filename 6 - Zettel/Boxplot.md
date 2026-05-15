#Note

2026-05-15

Tags: [[Statistik]], [[Deskriptive Statistik]], [[Visualisierung]], [[Quantile]]
#

---
### Aufbau und Komponenten

Ein Boxplot visualisiert die **Fünf-Punkte-Zusammenfassung**:

1. **Minimum:** Der kleinste Wert (der kein Ausreißer ist).
2. **Unteres Quartil ($Q_1$):** 25% der Daten liegen darunter.
3. **Median ($Q_2$):** 50% der Daten liegen darunter.
4. **Oberes Quartil ($Q_3$):** 75% der Daten liegen darunter.
5. **Maximum:** Der größte Wert (der kein Ausreißer ist).

### Die Box und der IQR

Die zentrale Box reicht von $Q_1$ bis $Q_3$. Ihre Länge entspricht dem **Interquartilsabstand (IQR)**:
$$IQR = Q_3 - Q_1$$
In dieser Box befinden sich exakt die mittleren 50% der Beobachtungen.

### Whiskers (Antennen) und Ausreißer

Die Whiskers erstrecken sich von der Box nach außen.
- **Standard-Regel (Tukey):** Die Whiskers enden am weitesten entfernten Datenpunkt, der noch innerhalb der Schranken liegt:

    - Untere Schranke: $Q_1 - 1,5 \cdot IQR$
    
    - Obere Schranke: $Q_3 + 1,5 \cdot IQR$
- **Ausreißer:** Werte außerhalb dieser Schranken werden als einzelne Punkte dargestellt.

### Interpretation der Verteilungsform

- **Symmetrie:** Wenn der Median mittig in der Box liegt und die Whiskers gleich lang sind.
- **Rechtsschiefe (linksgipflig):** Der Median liegt näher an $Q_1$, der obere Whisker ist länger als der untere.
- **Linksschiefe (rechtsgipflig):** Der Median liegt näher an $Q_3$, der untere Whisker ist länger als der obere.


```text
Min ---- Q1 |====== Median ======| Q3 ---- Max
```

---

### Flashcards

Was repräsentiert die Länge der Box in einem Boxplot?::Den Interquartilsabstand ($IQR = Q_3 - Q_1$), also die Spannweite der zentralen 50% der Daten.

Wie berechnet man die theoretische Grenze, ab der ein Wert in einem Boxplot als Ausreißer markiert wird?::Oberhalb von $Q_3 + 1,5 \cdot IQR$ oder unterhalb von $Q_1 - 1,5 \cdot IQR$.

Ein Boxplot zeigt einen Median, der sehr nah am oberen Quartil ($Q_3$) liegt, während der untere Whisker sehr lang ist. Welche Verteilungsform liegt vor?
?
Eine **linksschiefe** (rechtsgipflige) Verteilung. Die Daten sind im oberen Bereich konzentriert (hohe Dichte), während sie nach unten hin weit auslaufen.

Welchen wesentlichen Nachteil hat der Boxplot gegenüber einem Histogramm bei multimodalen Verteilungen?
?
Der Boxplot kann keine "Dellen" oder mehrere Gipfel in der Verteilung anzeigen. Er abstrahiert die Daten so stark, dass eine bimodale Verteilung fälschlicherweise wie eine unimodale Verteilung mit hoher Varianz wirken kann.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Boxplot]]
SORT file.mtime DESC
```