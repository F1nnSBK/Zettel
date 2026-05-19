#Note

2026-05-19

Tags: [[Data Science]], [[Mathematik]], [[Stochastik]], [[Inferenzstatistik]]
#statistik

---
Die **Statistik** ist die Wissenschaft vom Sammeln, Aufbereiten, Analysieren und Interpretieren von Daten. Sie bildet das mathematische und methodische Rückgrat der Data Science, der künstlichen Intelligenz und der empirischen Forschung.

Das Gesamtgebiet teilt sich klassischerweise in drei fundamentale Säulen auf:

### 1. Deskriptive Statistik (Beschreibende Statistik)

Die deskriptive Statistik befasst sich mit der Zusammenfassung und Beschreibung eines vorliegenden Datensatzes. Die Aussagen gelten ausschließlich für die untersuchten Datenobjekte selbst.

- **Kernwerkzeuge:** Lagemaße (Median, Mittelwert), Streuungsmaße (Varianz, IQR), Formmaße (Schiefe, Kurtosis) sowie bivariate Analysen (Korrelation, einfache lineare Regression).
    
- **Ziel:** Komplexitätsreduktion und Mustererkennung ohne Verallgemeinerung über die Datenbasis hinaus.
    

### 2. Wahrscheinlichkeitsrechnung (Stochastik)

Die Stochastik fungiert als Bindeglied und theoretischer Unterbau. Sie modelliert den Zufall mit mathematischen Mitteln (Mengenlehre, Axiomatik von Kolmogorow).

- **Kernwerkzeuge:** Mengenkalkül, bedingte Wahrscheinlichkeiten, der Satz von Bayes sowie die Theorie der Zufallsvariablen und Wahrscheinlichkeitsverteilungen (Binomial-, Normalverteilung).
    
- **Ziel:** Deduktive Ableitung von Wahrscheinlichkeiten für zukünftige Ereignisse auf Basis bekannter theoretischer Modelle.
    

### 3. Induktive Statistik (Inferenzstatistik / Schließende Statistik)

Die induktive Statistik nutzt die Stichprobendaten der deskriptiven Statistik und die Gesetzmäßigkeiten der Stochastik, um induktive Rückschlüsse auf eine unbekannte Grundgesamtheit zu ziehen.

- **Kernwerkzeuge:** Schätzverfahren (Punkt- und Intervallschätzung wie Konfidenzintervalle) und Hypothesentests ($t$-Test, ANOVA, Chi-Quadrat-Tests).
    
- **Ziel:** Quantifizierung von Unsicherheit und Absicherung von Verallgemeinerungen gegen den reinen Zufall.



---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Statistik]]
SORT file.mtime DESC
```