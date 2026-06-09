#Note

2026-05-15

Tags: [[Statistik]], [[Kausalität]], [[Bivariate Daten]], [[Machine Learning]]
#deskriptive_statistik

---
Eine **Scheinkorrelation** (Spurious Correlation) liegt vor, wenn zwischen zwei Variablen $X$ und $Y$ ein statistischer Zusammenhang (hoher Korrelationskoeffizient) gemessen wird, der jedoch nicht auf einer direkten ursächlichen Beziehung beruht.

### Ursache: Die Drittvariable (Confounder)

In den meisten Fällen wird der Zusammenhang durch eine dritte Variable $Z$ induziert, die sowohl $X$ als auch $Y$ kausal beeinflusst.

- **Struktur:** $X \leftarrow Z \rightarrow Y$
- **Klassiker:** "Anzahl der Störche" ($X$) und "Geburtenrate" ($Y$). Die Drittvariable $Z$ ist der "Ländlichkeitsgrad" der Region.

### Mathematische Auflösung: Partialkorrelation

Um zu prüfen, ob die Korrelation zwischen $X$ und $Y$ "echt" ist, berechnet man die Korrelation, während der Einfluss von $Z$ konstant gehalten (herausgerechnet) wird.

$$r_{xy.z} = \frac{r_{xy} - r_{xz} \cdot r_{yz}}{\sqrt{(1-r_{xz}^2)(1-r_{yz}^2)}}$$

- Ist $r_{xy.z} \approx 0$, war die ursprüngliche Korrelation $r_{xy}$ eine reine Scheinkorrelation.

### Abgrenzung: Nonsense Correlation

Bei der Nonsense Correlation korrelieren Variablen rein zufällig oder aufgrund technischer Artefakte (z. B. zwei unabhängige Zeitreihen mit Trends), ohne dass überhaupt eine gemeinsame Drittvariable existieren muss.

- **Beispiel:** "Pro-Kopf-Verbrauch von Käse" korreliert mit "Anzahl der Toten durch Verheddern in Bettlaken". Hier liegt oft _Data Dredging_ vor (man sucht so lange in riesigen Datenmengen, bis man zufällige Muster findet).

### Bedeutung für Machine Learning

Modelle, die auf Scheinkorrelationen basieren, sind **nicht robust**. Wenn sich die Verteilung der Drittvariable $Z$ in der Produktion ändert (Distribution Shift), bricht die Vorhersagekraft des Modells zusammen, da keine echte kausale Kette gelernt wurde.

---

### Flashcards

Warum führt eine hohe Korrelation zwischen dem Eisverkauf und der Anzahl an Hai-Angriffen nicht zu einer Kausalität?::Es liegt eine Scheinkorrelation vor. Die Drittvariable "Außentemperatur/Sommer" beeinflusst beide: Bei Hitze gehen mehr Menschen schwimmen (Hai-Gefahr) und essen mehr Eis.
<!--SR:!2026-06-11,3,250-->

Was ist das Ziel der Partialkorrelation $r_{xy.z}$?::Den linearen Einfluss einer Drittvariable $Z$ auf die Variablen $X$ und $Y$ statistisch zu eliminieren, um den "reinen" Zusammenhang zwischen $X$ und $Y$ zu isolieren.
<!--SR:!2026-06-09,1,230-->

Warum sind Zeitreihen besonders anfällig für Scheinkorrelationen?
?
Da viele Zeitreihen einen gemeinsamen Trend (z. B. Bevölkerungswachstum, Inflation) aufweisen. Dieser Gleichlauf über die Zeit führt zu hohen Korrelationskoeffizienten, selbst wenn die zugrunde liegenden Prozesse physikalisch völlig unabhängig sind.

Was passiert mathematisch mit der Partialkorrelation $r_{xy.z}$, wenn der ursprüngliche Zusammenhang $r_{xy}$ vollständig durch $Z$ erklärt werden kann?
?
Die Partialkorrelation sinkt auf **Null** ($r_{xy.z} = 0$), da der Zähler der Formel ($r_{xy} - r_{xz} \cdot r_{yz}$) unter der Bedingung der totalen Konfundierung Null ergibt.



---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Scheinkorrelation]]
SORT file.mtime DESC
```