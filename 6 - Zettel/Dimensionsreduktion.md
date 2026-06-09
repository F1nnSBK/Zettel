#Note

2026-05-03

Tags: [[Dimensionality Reduction]], [[PCA]], [[t-SNE]], [[UMAP]], [[Curse of Dimensionality]], [[Unsupervised learning]]
#UL

---
In der Realität sind Daten oft hochdimensional (z. B. Pixel, Genomsequenzen), doch die aussagekräftige Information konzentriert sich meist auf einer viel niederdimensionaleren Struktur, der **intrinsischen Dimensionalität** $k \ll d$. Dimensionalitätsreduktion extrahiert diesen signaltragenden Kern und verwirft Redundanz und Rauschen.

### Der Sinn: Warum Reduzieren?

- **Überwindung des Curse of Dimensionality:** In hohen Dimensionen konvergieren paarweise Abstände (Distanzkonzentration), wodurch Clustering-Algorithmen ihre Trennschärfe verlieren.
- **Kompression & Effizienz:** Reduziert Rechenaufwand (z. B. Distanzberechnungen in $O(nd)$) und Speicherbedarf.
- **Visualisierung:** Transformation komplexer Muster in interpretierbare 2D/3D-Räume.
- **Entwirrung (Disentanglement):** Korrelierte oder abhängige Features werden in unabhängige latente Faktoren überführt.

### Lineare Projektion: [[PCA]]

Die **[[Principal Component Analysis]] (PCA)** sucht orthogonale Richtungen maximaler Varianz.

- **Mathematik:** Entspricht der [[Eigenwertzerlegung]] der Kovarianzmatrix $\Sigma = \frac{1}{n} X^T X$. Die Eigenvektoren definieren die neuen Achsen (Hauptkomponenten).
- **Dualität:** Die Maximierung der Varianz auf den neuen Achsen minimiert gleichzeitig den quadratischen **Rekonstruktionsfehler**:

$$\mathcal{L}_{rec} = \sum_{i=1}^n ||x_i - WW^T x_i||^2$$


### Nicht-lineare Visualisierung: t-SNE & UMAP

Wenn Daten auf gekrümmten Manifolds liegen, versagt PCA aufgrund ihrer Linearität.

- **t-SNE (t-distributed Stochastic Neighbor Embedding):**
    - Erhält primär **lokale Strukturen**; nahe Punkte in High-D bleiben in Low-D nahe beieinander.
    - Nutzt eine Student-t-Verteilung im Zielraum, um das **Crowding-Problem** (Kollaps aller Punkte im Zentrum) zu verhindern.
    - **Nachteil:** Clustergrößen und Distanzen zwischen Clustern sind oft nicht interpretierbar; Ergebnisse variieren stark mit dem Random Seed.
- **UMAP (Uniform Manifold Approximation and Projection):**
    - Basiert auf Riemannscher Geometrie und algebraischer Topologie.
    - **Vorteile gegenüber t-SNE:** Skaliert besser auf große Datensätze ($O(n \log n)$), ist reproduzierbarer und bewahrt mehr von der **globalen Struktur**.


---
#### Flashcards

Warum sollte man t-SNE oder UMAP niemals als Vorverarbeitungsschritt für einen nachgeschalteten Klassifikator verwenden? :: Weil diese Methoden nicht-parametrisch sind (kein gelerntes Mapping für neue Daten) und lokale Distanzen im Zielraum keine stabilen semantischen Abstände für Generalisierungen garantieren. Verwende stattdessen PCA oder VAE-Encoder.
<!--SR:!2026-06-09,1,230-->

Was ist der entscheidende Unterschied zwischen t-SNE und UMAP hinsichtlich der globalen Datenstruktur?
?
t-SNE priorisiert fast ausschließlich die Erhaltung lokaler Nachbarschaften (Cluster). UMAP optimiert eine Cross-Entropy-Loss-Funktion, die sowohl das Auseinanderziehen von Nachbarn als auch das Zusammenschieben von Nicht-Nachbarn bestraft, wodurch die relative Anordnung entfernter Cluster (globale Struktur) besser erhalten bleibt.
<!--SR:!2026-06-09,1,230-->

Wie wird die Anzahl der zu behaltenden Hauptkomponenten in der PCA mathematisch begründet?
?
Über die **Explained Variance Ratio**. Man wählt $k$ Komponenten so, dass die Summe der zugehörigen Eigenwerte einen Schwellenwert (z. B. 95%) der Gesamtsumme aller Eigenwerte überschreitet:$$\frac{\sum_{i=1}^k \lambda_i}{\sum_{i=1}^d \lambda_i} \ge 0.95$$
<!--SR:!2026-06-09,1,230-->


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Dimensionsreduktion]]
SORT file.mtime DESC
```