#Note

2026-05-03

Tags: [[DBSCAN]], [[Clustering]], [[Machine Learning]], [[Dichte]], [[Mathematik]]
#UL

---
Im Gegensatz zu zentroid-basierten Verfahren definiert **Density-Based Clustering** Cluster als Gebiete mit einer hohen Dichte an Punkten, die durch Gebiete niedrigerer Dichte (Rauschen) getrennt sind. Dichte beschreibt hierbei die Anzahl der Punkte pro Fläche, Volumen oder Hypervolumen.

### Punkt-Klassifizierung in DBSCAN

DBSCAN (Density-Based Spatial Clustering of Applications with Noise) klassifiziert jeden Datenpunkt basierend auf seiner lokalen $\epsilon$-Nachbarschaft $N_\epsilon(p)$:

- **Kernpunkt ($p_c$):** Ein Punkt ist ein Kernpunkt, wenn sich in seiner Nachbarschaft (Radius $\epsilon$) mindestens $n_{min}$ Punkte befinden (inklusive ihm selbst).

- **Grenzpunkt ($p_b$):** Ein Punkt, der weniger als $n_{min}$ Nachbarn hat, aber in der $\epsilon$-Nachbarschaft eines Kernpunkts liegt. Er gehört zum Cluster, kann diesen aber nicht erweitern.

- **Rauschpunkt ($p_n$):** Ein Punkt, der weder Kern- noch Grenzpunkt ist. Er wird keinem Cluster zugeordnet.

### Mathematische Konzepte der Konnektivität

Cluster entstehen durch das Wachstum von Kernpunkt-Nachbarschaften.

- **Dichte-Erreichbarkeit (Asymmetrisch):** Ein Punkt $q$ ist dichte-erreichbar von $p$, wenn $q \in N_\epsilon(p)$ und $p$ ein Kernpunkt ist.

- **Dichte-Verbundenheit (Symmetrisch):** Zwei Punkte $p$ und $q$ sind dichte-verbunden, wenn es einen gemeinsamen Kernpunkt $o_c$ gibt, von dem beide dichte-erreichbar sind.

### Hyperparameter-Wahl

Die Wahl von $(\epsilon, n_{min})$ bestimmt die Qualität der Partitionierung maßgeblich.

- **$n_{min}$:** Faustregel $n_{min} > d + 1$ (Dimension des Raums). Ein zu kleiner Wert behandelt Rauschen fälschlicherweise als dichte Cluster.

- **$\epsilon$:** Bestimmung über den **k-Distance Plot**. Man sortiert die Distanzen jedes Punktes zu seinem $k$-nächsten Nachbarn ($k = n_{min} - 1$) aufsteigend. Der „Knick“ (Elbow) markiert den Übergang von dichter Struktur zu Rauschen und ist der ideale Wert für $\epsilon$.

### Grenzen und Weiterentwicklungen

- **Varying Density:** DBSCAN scheitert, wenn Cluster im Datensatz stark unterschiedliche Dichten aufweisen, da ein globales $\epsilon$ entweder die dichten Cluster verschmilzt oder die dünnen als Noise markiert.

- **Bridging & Chaining:** Dünne Ketten von Kernpunkten können eigentlich getrennte Cluster fälschlicherweise verschmelzen.

- **Lösungen:** **OPTICS** erzeugt einen Reachability-Plot für alle Skalen; **HDBSCAN** extrahiert die stabilsten Cluster aus einer Dichte-Hierarchie.




---
#### Flashcards

Warum ist die Dichte-Erreichbarkeit (Density-Reachability) in DBSCAN asymmetrisch? :: Ein Grenzpunkt $p_b$ kann von einem Kernpunkt $p_c$ erreicht werden, aber von einem Grenzpunkt aus kann die Cluster-Kette nicht fortgesetzt werden, da er selbst nicht genügend Nachbarn für die Kernpunkt-Bedingung besitzt.

Wie hilft der k-Distance Plot bei der Wahl des Radius $\epsilon$?
?
Durch das Sortieren der Distanzen zum $(n_{min}-1)$-ten Nachbarn wird sichtbar, ab welcher Distanz Punkte sprunghaft spärlicher verteilt sind. Dieser Übergangspunkt (Elbow) trennt signal-relevante Dichte von Rauschen.

Was ist der strukturelle Vorteil von HDBSCAN gegenüber dem klassischen DBSCAN?
?
HDBSCAN benötigt kein globales $\epsilon$. Es betrachtet alle Dichte-Ebenen gleichzeitig (Hierarchie) und wählt Cluster basierend auf ihrer Beständigkeit (Persistenz) über verschiedene Dichteschwellen hinweg aus.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Density-Based Clustering]]
SORT file.mtime DESC
```