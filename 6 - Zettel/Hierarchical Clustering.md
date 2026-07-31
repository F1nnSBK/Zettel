#Note

2026-06-24

Tags: [[Unsupervised Learning]], [[Clustering]], [[Hierarchical Clustering]]
#UL

---

## Kapitel 3 – Hierarchical Clustering

> *"Ich springe von Level zu Level zu Level."*

### The Why

K-Means hat drei grundlegende Probleme:
1. **Centroid-Annahme** → nur konvexe, sphärische Cluster
2. **Initialisierungs-Sensitivität** → nicht-deterministisch
3. **Eine einzige Skalenstufe** → K muss vorab gewählt werden

**Hierarchical Clustering** löst Problem 3: Es produziert **alle** Partitionen von $K=1$ bis $K=n$ in einer einzigen Struktur: dem **Dendrogramm**.

**Lernziele:**
- Agglomeratives Clustering und Dendrogramm-Aufbau verstehen
- Single, Complete und Ward's Linkage anwenden und unterscheiden
- Erkennen wann Hierarchical Clustering K-Means übertrifft und wo es versagt

---

### Theorie

#### Agglomeratives Clustering (Bottom-Up)

**Idee:** Starte mit $n$ Singleton-Clustern, fasse schrittweise die zwei nächsten Cluster zusammen.

```
Initialisiere: C_i = {x_i} für alle i; active = {C_1,...,C_n}
Berechne Distanzmatrix D[i,j] = d(x_i, x_j)
Solange |active| > 1:
  (i*, j*) = argmin_{i≠j} D[i,j]
  Merge: C_m = C_i* ∪ C_j*  (Eintrag im Dendrogramm mit Höhe D[i*,j*])
  Aktualisiere D[m,k] = L(C_m, C_k) für alle aktiven Cluster
  Entferne C_i*, C_j*, füge C_m hinzu
```

**Determinismus:** Vollständig deterministisch (keine Initialisierung). Bei gleichem Datensatz → immer gleicher Baum.

#### Linkage-Kriterien

| Linkage | Formel | Charakteristik |
|---|---|---|
| **Single** | $\min_{p \in A, q \in B} d(p,q)$ | Nearest-Neighbor; neigt zu Ketten (Chaining) |
| **Complete** | $\max_{p \in A, q \in B} d(p,q)$ | Farthest-Neighbor; kompakte, gleichgroße Cluster |
| **Average** | $\frac{1}{\|A\|\|B\|} \sum_{p,q} d(p,q)$ | Kompromiss; robust |
| **Ward** | Minimiert $\Delta J = J(C_m) - J(C_A) - J(C_B)$ | Minimiert WCSS-Zuwachs; ähnlich wie K-Means |

#### Dendrogramm lesen

- **Horizontaler Schnitt** bei Höhe $h$ → Flat Partition mit $K$ Clustern
- **Großer Sprung** zwischen zwei Merge-Höhen = natürliche Clusteranzahl
- Blätter = einzelne Datenpunkte, innere Knoten = Merge-Zeitpunkte

#### Komplexität

- Naïv: $O(n^3)$ Zeit, $O(n^2)$ Speicher
- **BIRCH** (Balanced Iterative Reducing and Clustering using Hierarchies): Approximation für große Datensätze, $O(n)$

---

### Trace-Beispiel (6 Punkte, Single Linkage)

Punkte: $x_1=(1,2), x_2=(2,3), x_3=(3,1), x_4=(6,8), x_5=(8,7), x_6=(8,9)$

| Merge | Distanz | Ergebnis |
|---|---|---|
| 1 | $d(x_1,x_2) = \sqrt{2} \approx 1.41$ | $\{x_1,x_2\}$ |
| 2 | $d(x_5,x_6) = 2$ | $\{x_5,x_6\}$ |
| 3 | $d(x_4,x_5) \approx 2.83$ | $\{x_4,x_5,x_6\}$ |
| 4 | $d(x_2,x_3) \approx 2.24$ | $\{x_1,x_2,x_3\}$ |
| 5 | $d(x_2,x_4) \approx 6.40$ | $\{x_1,...,x_6\}$ |

Der große Sprung von ~2.24 auf ~6.40 deutet $K=2$ als natürliche Clusteranzahl.

---

### Übungen

#### Aufgabe 1
Was ist der Unterschied zwischen Single Linkage und Ward's Linkage?

**Lösung:**
**Single Linkage** misst den minimalen Abstand zwischen zwei Clustern (Nearest-Neighbor). Tendenz zur Kettenbildung – ein Ausreißer kann zwei weit entfernte Cluster verbinden.
**Ward's Linkage** minimiert den Zuwachs der Inertia beim Merge: $\Delta J = J(A \cup B) - J(A) - J(B)$. Produziert kompakte, ähnlich große Cluster, ähnlich wie K-Means, aber deterministisch und hierarchisch.

#### Aufgabe 2
Warum ist agglomeratives Clustering deterministisch, K-Means aber nicht?

**Lösung:**
Agglomeratives Clustering startet immer von den gleichen $n$ Singleton-Clustern – es gibt nichts zu initialisieren. K-Means hingegen braucht Startzentroiden, die zufällig gewählt werden, was zu verschiedenen lokalen Minima führt.

#### Aufgabe 3
Wie liest man die natürliche Clusteranzahl aus einem Dendrogramm?

**Lösung:**
Man sucht den größten vertikalen Abstand (Gap) zwischen zwei aufeinanderfolgenden Merge-Höhen. Schneidet man das Dendrogramm genau in diesem Gap horizontal, erhält man die natürliche Partition.

---

#### Flashcards

Was ist ein Dendrogramm?::Ein Binärbaum, dessen Blätter einzelne Datenpunkte sind und dessen innere Knoten die Merge-Höhe (Distanz beim Zusammenführen) kodieren. Enthält alle Partitionen von K=1 bis K=n.

Was ist der Unterschied zwischen agglomerativ und divisiv?
?
**Agglomerativ (Bottom-Up):** Startet mit n Singleton-Clustern, führt schrittweise die zwei nächsten zusammen.
**Divisiv (Top-Down):** Startet mit einem Cluster, teilt schrittweise den größten auf. Seltener – teurer und noisier.

Welches Linkage-Kriterium neigt zu Chaining und warum?::Single Linkage, weil es nur den kürzesten Abstand zwischen zwei Clustern misst. Ein einzelner Brücken-Punkt kann zwei weit entfernte Gruppen verbinden.

Wie erkennt man die natürliche Clusteranzahl im Dendrogramm?::Am größten Gap (vertikaler Sprung) zwischen zwei aufeinanderfolgenden Merge-Höhen. Der horizontale Schnitt direkt unter diesem Gap liefert die natürliche Partition.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[03 Hierarchical Clustering]]
SORT file.mtime DESC
```
