#Note

2026-04-09

Tags: [[Unsupervised Learning]], [[Clustering]], [[Machine Learning]], [[Statistik]], [[Curse of Dimensionality]]
#UL

---
Im Unsupervised Learning ist die Anzahl der Cluster oft mehrdeutig. Ohne Ground Truth ist jede Partitionierung eine Modellentscheidung – ob man 2, 3 oder 6 Cluster sieht, hängt von der Ebene der Abstraktion ab (die „Geschichte“, die man über die Daten erzählen möchte).

### K-Means
K-Means ist ein Algorithmus zur harten Partitionierung, bei dem jeder Punkt genau einem Cluster zugeordnet wird.

**Anforderungen & Annahmen:**

- **Sphärische Cluster:** K-Means geht davon aus, dass Cluster rund und etwa gleich groß sind.
- **Gleiche Dichte:** Es scheitert oft bei Clustern mit stark variierender Punktdichte.
- **Sensitivität:** Sehr anfällig für Ausreißer, da der Mittelwert (Zentroid) stark verzerrt wird.

**Inertia (Trägheit):** Das mathematische Ziel ist die Minimierung der **Within-Cluster Sum of Squares (WCSS)**.

$$I = \sum_{k=1}^{K} \sum_{x_i \in C_k} ||x_i - \mu_k||^2$$

$\mu_k$ ist dabei der Zentroid (Massenschwerpunkt) des Clusters $C_k$.

**Der Algorithmus (Lloyd's Algorithmus):**

1. **Step 1: Initialisierung:** Wähle $K$ initiale Zentroiden $\mu_1, ..., \mu_K$.
2. **Step 2: Assignment:** Weise jeden Punkt $x_i$ dem Zentroiden mit der geringsten quadratischen Distanz zu:
$$c_i \leftarrow \arg \min_k ||x_i - \mu_k||^2$$

3. **Step 3: Update:** Berechne die Zentroiden neu als arithmetisches Mittel aller zugeordneten Punkte:
$$\mu_k \leftarrow \frac{1}{|C_k|} \sum_{x_i \in C_k} x_i$$

	Wiederholung bis zur Konvergenz (Zuweisungen ändern sich nicht mehr).

### K-Means++ & Optimierungen

Da das Optimierungsproblem NP-hart ist und K-Means oft in lokalen Optima stecken bleibt, sind Initialisierung und Recheneffizienz kritisch.

- **Educated Initialization (K-Means++):** Zentroiden werden nicht rein zufällig gewählt. Der erste Zentroid ist zufällig; jeder weitere wird mit einer Wahrscheinlichkeit gewählt, die proportional zum Quadrat der Distanz zum nächsten bereits existierenden Zentroiden ist ($p(x_i) \propto D(x_i)^2$). Dies sorgt für eine bessere Verteilung im Raum.

- **Mini-Batch K-Means:** Nutzt kleine zufällige Teilmengen (Batches) der Daten für die Updates, um auf Millionen von Datenpunkten zu skalieren.

- **Monte Carlo & Bengio:** Bezieht sich auf die Erkenntnis (oft zitiert nach Bengio), dass intelligentes „Raten“ (Random Restarts oder Random Search) effizienter ist als ein Brute-Force-Versuch, den gesamten Parameterraum für das globale Optimum der Inertia abzusuchen.






---
#### Flashcards

Warum führt K-Means bei ringförmigen (nicht-konvexen) Clustern zu Fehlern? :: Da K-Means die Distanz zum Zentrum (Zentroid) minimiert, erzwingt es eine lineare Trennung (Voronoi-Zellen). Ringe teilen sich jedoch dasselbe Zentrum, was eine korrekte Zuweisung über die Euklidische Distanz unmöglich macht.
<!--SR:!2026-06-09,1,230-->

Wie ist die mathematische Zielfunktion von K-Means definiert?
?
$$I = \sum_{k=1}^{K} \sum_{x_i \in C_k} ||x_i - \mu_k||^2$$
Es wird die Summe der quadrierten Abstände aller Punkte zu ihrem jeweiligen Cluster-Zentroiden minimiert (Inertia).
<!--SR:!2026-06-09,1,230-->

Was ist der Kernvorteil von K-Means++ gegenüber einer rein zufälligen Initialisierung?
?
Durch die distanzabhängige Wahrscheinlichkeitsverteilung beim Seeding liegen die initialen Zentroiden weiter auseinander, was die Wahrscheinlichkeit erhöht, nahe am globalen Optimum zu starten und die Konvergenz beschleunigt.
<!--SR:!2026-06-09,1,230-->


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Centroid-Based Clustering]]
SORT file.mtime DESC
```
