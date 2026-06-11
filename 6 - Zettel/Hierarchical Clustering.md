#Note

2026-05-03

Tags: [[Hierarchical Clustering]], [[Agglomerative Clustering]], [[Dendrogram]], [[Linkage Criteria]], [[Unsupervised Learning]]
#UL

---
Hierarchisches Clustering bildet eine Verschachtelung von Partitionen ab und vermeidet so die Festlegung auf ein einzelnes $K$ zu Beginn des Prozesses. Während K-Means eine flache Partition erzwingt, liefert dieses Verfahren eine Baumstruktur (Dendrogramm), die alle Ebenen von $K=n$ bis $K=1$ enthält.

### Agglomerativer Algorithmus (Bottom-Up)

Das gängigste Verfahren ist die schrittweise Verschmelzung:

1. **Initialisierung:** Jeder Punkt startet als eigenes Cluster (Singleton).
2. **Distanztabelle:** Berechne die paarweisen Distanzen aller Punkte.
3. **Merge-Loop:** Suche das Paar mit der geringsten Distanz und verschmelze es zu einem neuen Cluster.
4. **Update:** Berechne die Distanzen vom neuen Cluster zu allen verbleibenden Clustern basierend auf dem gewählten **Linkage-Kriterium**.
5. Wiederhole, bis nur noch ein Cluster existiert (nach $n-1$ Merges).

### Linkage-Kriterien (Kern-Hyperparameter)

Das Linkage-Kriterium bestimmt, wie die Distanz zwischen zwei Punktmengen (Clustern) $C_i$ und $C_j$ gemessen wird.

- **Single Linkage (Min):** Distanz der nächsten Nachbarn. Kann langgezogene, nicht-konvexe Formen finden, leidet aber unter **Chaining** (einzelne Punkte bilden Brücken zwischen eigentlich getrennten Gruppen).
$$D_{single}(C_i, C_j) = \min_{x \in C_i, y \in C_j} d(x, y)$$
- **Complete Linkage (Max):** Distanz der am weitesten entfernten Punkte. Erzeugt kompakte Cluster mit ähnlichem Durchmesser.
$$D_{complete}(C_i, C_j) = \max_{x \in C_i, y \in C_j} d(x, y)$$
- **Average Linkage:** Mittelwert aller paarweisen Distanzen zwischen den Clustern. Ein Kompromiss zwischen Single und Complete.

- **Ward's Method:** Verschmilzt die Cluster, die den geringsten Zuwachs an der totalen Varianz innerhalb der Cluster (Inertia) verursachen. Ward's neigt dazu, sehr klare "Gaps" im Dendrogramm zu erzeugen, was die Wahl von $K$ erleichtert.
$$D_{Ward}(C_a, C_b) = \frac{n_a \cdot n_b}{n_a + n_b} ||\mu_a - \mu_b||^2$$

### Das Dendrogramm interpretieren

Ein horizontaler Schnitt durch das Dendrogramm liefert eine flache Partitionierung. Die vertikale Achse (Merge Height) zeigt die Distanz, bei der die Verschmelzung stattfand. Ein großer vertikaler Sprung zwischen zwei Merges signalisiert eine natürliche Anzahl von Clustern.

### Systemgrenzen

- **Greedy & Irreversibel:** Einmal verschmolzene Cluster können nicht mehr getrennt werden. K-Means kann Fehler korrigieren, HC nicht.

- **Komplexität:** Der Speicherbedarf liegt bei $O(n^2)$ für die Distanzmatrix, was bei sehr großen Datensätzen (z. B. $n > 100.000$) ohne Kompression (wie BIRCH) zum Abbruch führt.


---
#### Flashcards

Was versteht man unter dem "Chaining"-Effekt beim Hierarchical Clustering? :: Bei Single Linkage reicht ein einzelner Datenpunkt aus, der wie eine Brücke zwischen zwei eigentlich separaten, dichten Clustern liegt, um diese vorzeitig zu verschmelzen.
<!--SR:!2026-06-08,0,230-->

Wie wird die Anzahl der Cluster $K$ nach einem hierarchischen Clustering-Lauf bestimmt?
?
Durch einen horizontalen Schnitt durch das Dendrogramm. Die Anzahl der geschnittenen vertikalen Linien entspricht dem resultierenden $K$. Ein großer Abstand zwischen zwei Verschmelzungshöhen (Merge Height Gap) deutet dabei auf ein stabiles $K$ hin.
<!--SR:!2026-06-08,0,230-->

Inwiefern unterscheidet sich Ward's Method mathematisch von K-Means?
?
Beide minimieren die Varianz innerhalb der Cluster (Inertia). K-Means optimiert dies jedoch iterativ durch Re-Assignment von Punkten, während Ward's Method eine gierige (greedy), hierarchische Verschmelzung durchführt, die einmal getroffene Entscheidungen nicht mehr rückgängig machen kann.
<!--SR:!2026-06-11,1,210-->


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Hierarchical Clustering]]
SORT file.mtime DESC
```