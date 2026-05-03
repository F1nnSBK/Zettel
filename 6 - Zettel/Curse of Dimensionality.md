#Note

2026-05-03

Tags: [[Curse of Dimensionality]], [[Dimensionsreduktion]], [[Distanzmetriken]], [[Unsupervised Learning]]
#UL

---
Der _Curse of Dimensionality_ (Fluch der Dimensionalität) beschreibt den exponentiellen Anstieg des Volumens eines mathematischen Raumes bei linearer Hinzunahme neuer Dimensionen $d$. Für maschinelles Lernen bedeutet dies, dass eine feste Anzahl von Datenpunkten $N$ in hohen Dimensionen überall extrem spärlich (sparse) wird.

### Das mathematische Kernproblem (Distanzkonzentration)

In niedrigen Dimensionen gibt es nahe und ferne Punkte – dieser Kontrast macht Distanzmetriken und Clustering überhaupt erst möglich. Wächst $d$, verschwindet dieser Kontrast: Alle paarweisen Distanzen konvergieren gegen denselben Wert.

- Die mittlere Nächste-Nachbar-Distanz skaliert mit:

$$d_{NN} \propto N^{-1/d}$$

- Bei $d=50$ ist fast jeder Punkt annähernd so weit von seinem nächsten Nachbarn entfernt wie von der Grenze des Hyperwürfels. Die Punkte rücken nicht physisch auseinander, der Raum unter ihnen wächst.

### Auswirkungen auf Algorithmen

- **Dichtebasiertes Clustering (z.B. DBSCAN):** Fatal. Das Volumen einer $\epsilon$-Hypersphäre schrumpft im Verhältnis zum Gesamtvolumen ($V_{sphere}/V_{cube} \rightarrow 0$). Entweder muss $\epsilon$ so riesig werden, dass alles ein Cluster ist, oder es bleibt klein und jeder Punkt wird zu Noise ($p_n$).

- **Computational Cost:** Steigt enorm. Distanzberechnungen skalieren $O(nd)$, Kovarianzmatrizen benötigen $O(d^2)$ Speicher und Eigendecompositions kosten $O(d^3)$.

- **Informationsgehalt:** In hohen Dimensionen sind Features oft redundant oder stark miteinander verwoben (entangled).


### Die Lösung: Manifold Hypothesis & Dimensionalitätsreduktion

Das Problem ist nur dann fatal, wenn alle $d$ Dimensionen unabhängige Informationen tragen, was in der Realität fast nie der Fall ist.

- **Manifold Hypothesis:** Hochdimensionale Daten konzentrieren sich auf einer niederdimensionalen Mannigfaltigkeit (Manifold) $\mathcal{M} \subset \mathbb{R}^d$ mit einer intrinsischen Dimensionalität $k \ll d$.

- **Feature-Extraktion:** Reduktion von $d$ auf $k$ "reversiert" den Fluch. Methoden wie PCA, t-SNE oder VAEs extrahieren exakt jene neuen, transformierten Dimensionen, welche die Signalvarianz tragen und das Rauschen/die Redundanz verwerfen.


---
#### Flashcards

Warum versagen distanzbasierte Algorithmen (wie K-Means oder DBSCAN) typischerweise in sehr hochdimensionalen Räumen? :: Aufgrund der Distanzkonzentration (Curse of Dimensionality) konvergieren alle paarweisen Distanzen gegen denselben Wert. Der Kontrast zwischen "nah" und "fern" verschwindet, wodurch Dichte- oder Zentroid-basierte Zuordnungen bedeutungslos werden.

Wie skaliert die mittlere Distanz zum nächsten Nachbarn ($d_{NN}$) in Abhängigkeit von der Dimension $d$ und der Anzahl der Datenpunkte $N$?
?
$$d_{NN} \propto N^{-1/d}$$Je größer $d$, desto mehr strebt der Exponent gegen $0$, was bedeutet, dass Punkte im Hypervolumen extrem spärlich (sparse) verteilt sind.

Was besagt die "Manifold Hypothesis" (Mannigfaltigkeitshypothese) als Begründung für den Erfolg von Dimensionalitätsreduktionen wie VAEs oder PCA?
?
Sie besagt, dass reale, hochdimensionale Daten (z. B. im $\mathbb{R}^d$) sich auf einer niederdimensionalen, oft gekrümmten Mannigfaltigkeit (Manifold) mit der intrinsischen Dimensionalität $k \ll d$ konzentrieren.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Curse of Dimensionality]]
SORT file.mtime DESC
```