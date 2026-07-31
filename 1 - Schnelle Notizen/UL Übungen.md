#Note

2026-06-24

Tags: [[Unsupervised Learning]], [[Übungen]], [[Prüfungsvorbereitung]]
#UL

---

# Unsupervised Learning – Kapitelübergreifende Übungen

> Alle Aufgaben aus dem Skript + Notebook-Aufgaben (konzeptuell). Reine Code-Syntax ist weggelassen; zentrale API-Muster sind aber enthalten.

---

## Kapitel 1 – Similarity and Distance

### Aufgabe 1.1 – Distanzberechnung
Gegeben: $A = (1, 2)$, $B = (4, 6)$.
Berechne **(a)** Euklidische Distanz, **(b)** Manhattan-Distanz, **(c)** Cosinus-Ähnlichkeit.

<details><summary>Lösung</summary>

**(a)** $d_2 = \sqrt{(4-1)^2 + (6-2)^2} = \sqrt{9+16} = \sqrt{25} = 5$

**(b)** $d_1 = |4-1| + |6-2| = 3 + 4 = 7$

**(c)** $\cos(A,B) = \frac{A \cdot B}{\|A\|\|B\|} = \frac{1\cdot4 + 2\cdot6}{\sqrt{5}\cdot\sqrt{52}} = \frac{16}{\sqrt{260}} \approx 0.992$
</details>

---

### Aufgabe 1.2 – Skalierungs-Problem (Coffee Lab)
Du hast drei Features: **Acidity** (pH, Bereich 4.3–6.3), **Bitterness** (1–10), **Brew Strength** (7–24 mg/mL). Du berechnest euklidische Distanzen direkt auf diesen Rohdaten.

**(a)** Welches Feature dominiert die Distanzberechnung und warum?
**(b)** Welche Normalisierung würdest du wählen und warum?

<details><summary>Lösung</summary>

**(a)** Brew Strength dominiert: Spannbreite ~17 mg/mL vs. ~2 pH-Einheiten (Acidity) und ~9 (Bitterness). Euklidische Distanz summiert quadrierte Differenzen – der Feature mit dem größten numerischen Range überwiegt unabhängig von seiner inhaltlichen Relevanz.

**(b)** Z-Score-Normalisierung: $x' = (x - \mu)/\sigma$. Alle Features bekommen Mittelwert 0 und Std 1. Damit werden alle gleichwertig behandelt. Min-Max-Skalierung wäre auch möglich, ist aber sensitiver gegenüber Ausreißern.
</details>

---

### Aufgabe 1.3 – Mahalanobis vs. Euklidisch
Zwei Punkte $p = (3, 3)$ und $q = (5, 5)$ in einem Raum in dem die Daten entlang der Hauptdiagonale ausgerichtet sind (starke positive Korrelation). Welche Distanzmetrik ist angemessener und warum?

<details><summary>Lösung</summary>

Mahalanobis-Distanz: $d_M = \sqrt{(p-q)^T \Sigma^{-1} (p-q)}$.

Bei starker Korrelation gibt die Euklidische Distanz den gleichen Abstand an wie für unkorrellierte Daten. Mahalanobis berücksichtigt $\Sigma^{-1}$: entlang der Hauptachse der Korrelation ist der Abstand "kleiner" (die Datenvarianz entschuldigt ihn), senkrecht dazu ist er "größer". Mahalanobis ist invariant unter linearen Transformationen des Feature-Raums.
</details>

---

### Aufgabe 1.4 – Metriken & Eigenschaften
Ist Cosinus-Ähnlichkeit eine Metrik im mathematischen Sinne? Begründe.

<details><summary>Lösung</summary>

Nein. Cosinus-Ähnlichkeit verletzt die Nicht-Negativität: $\cos(x,y) \in [-1,1]$. Cosinus-Distanz $= 1 - \cos(x,y) \in [0,2]$ ist nicht-negativ, aber verletzt die Dreiecksungleichung in manchen Formulierungen. Streng genommen ist auch $d(x,x) = 0$ nur erfüllt wenn der Null-Vektor ausgeschlossen ist (da $\cos(0,0)$ undefiniert ist).
</details>

---

## Kapitel 2 – Centroid Clustering (K-Means)

### Aufgabe 2.1 – K-Means Trace
Gegeben: $x_1=(2,2), x_2=(4,2), x_3=(2,4), x_4=(8,8), x_5=(10,8)$. Startzentroiden: $\mu_1=(2,3), \mu_2=(9,8)$. $K=2$.

Führe eine vollständige K-Means-Iteration durch (Assignment + Update).

<details><summary>Lösung</summary>

**Assignment:**
- $x_1$: $d(\mu_1)=1, d(\mu_2)=\sqrt{85}$ → $C_1$
- $x_2$: $d(\mu_1)=\sqrt{5}, d(\mu_2)=\sqrt{61}$ → $C_1$
- $x_3$: $d(\mu_1)=1, d(\mu_2)=\sqrt{97}$ → $C_1$
- $x_4$: $d(\mu_1)=\sqrt{61}, d(\mu_2)=\sqrt{4}=2$ → $C_2$
- $x_5$: $d(\mu_1)=\sqrt{113}, d(\mu_2)=1$ → $C_2$

**Update:**
- $\mu_1 = \frac{1}{3}((2,2)+(4,2)+(2,4)) = (2.67, 2.67)$
- $\mu_2 = \frac{1}{2}((8,8)+(10,8)) = (9, 8)$
</details>

---

### Aufgabe 2.2 – Elbow-Methode
Du plottest Inertia $J$ für $K = 1, \ldots, 8$ und siehst folgende Werte: 1800, 900, 400, 310, 290, 275, 268, 262. Welches $K$ wählst du und warum?

<details><summary>Lösung</summary>

$K=3$ oder $K=4$. Die größten Inertia-Sprünge: 1800→900 (−900), 900→400 (−500), 400→310 (−90). Ab $K=4$ nimmt die Inertia kaum noch ab (marginal returns). Der "Elbow" liegt bei $K=3$. Damit: $K=3$.
</details>

---

### Aufgabe 2.3 – Silhouette
Ein Punkt $x_i$ hat mittlere Distanz $a(i)=2.0$ zu den Punkten im eigenen Cluster und mittlere Distanz $b(i)=6.0$ zum nächsten fremden Cluster. Berechne $s(i)$.

<details><summary>Lösung</summary>

$s(i) = \frac{b(i) - a(i)}{\max(a(i), b(i))} = \frac{6-2}{\max(2,6)} = \frac{4}{6} = 0.67$

Gut zugeordnet (nahe 1).
</details>

---

### Aufgabe 2.4 – K-Means Grenzen
Warum versagt K-Means auf Ring-förmigen Clustern? Nenne eine Alternative.

<details><summary>Lösung</summary>

K-Means nimmt sphärische, konvexe Cluster an (minimiert WCSS = quadratische Distanzen zum Centroid). Bei einem Ring liegt der Centroid im Zentrum, wo keine Datenpunkte sind. K-Means teilt den Ring daher in Halbbögen. Alternative: DBSCAN (dichte-basiert, keine Centroid-Annahme).
</details>

---

### 🔑 Zentrale Python-API (K-Means)
```python
from sklearn.cluster import KMeans

km = KMeans(n_clusters=3, init='k-means++', n_init=10, random_state=42)
km.fit(X)
labels = km.labels_          # Clusterzuordnung
centers = km.cluster_centers_  # Zentroiden
inertia = km.inertia_        # WCSS

# Silhouette
from sklearn.metrics import silhouette_score
s = silhouette_score(X, labels)
```

---

## Kapitel 3 – Hierarchical Clustering

### Aufgabe 3.1 – Dendrogramm lesen
Ein Dendrogramm zeigt Merge-Höhen: 0.8, 1.2, 1.4, 5.7, 5.9. Wie viele natürliche Cluster gibt es und warum?

<details><summary>Lösung</summary>

Zwischen Höhe 1.4 und 5.7 liegt ein großer Gap (Δ=4.3). Man schneidet das Dendrogramm in diesem Gap → 2 Cluster. Die vier niedrigen Merges (unter 1.4) passieren innerhalb der Cluster; die zwei hohen (5.7, 5.9) fusionieren die Cluster miteinander.
</details>

---

### Aufgabe 3.2 – Linkage-Vergleich
Erkläre an einem Beispiel warum Single Linkage bei verrauschten Daten problematisch ist.

<details><summary>Lösung</summary>

Single Linkage misst den minimalen Abstand zwischen zwei Clustern. Ein einzelner Ausreißer-Punkt der "zufällig" zwischen zwei eigentlich getrennten Clustern liegt, kann beide früh zusammenführen ("Chaining"). Der gesamte restliche Abstand zwischen den Clustern wird ignoriert. Complete oder Ward's Linkage sind robuster: sie messen den maximalen Abstand bzw. den WCSS-Zuwachs.
</details>

---

### Aufgabe 3.3 – Cophenetic Correlation
Was ist die Cophenetic Correlation und wozu dient sie?

<details><summary>Lösung</summary>

Die Cophenetic Correlation misst wie gut das Dendrogramm die paarweisen Abstände der Originaldaten repräsentiert. Berechnung: Korrelation zwischen paarweisen Originaldistanzen und den Merge-Höhen im Dendrogramm (cophenetic distances). Wert nahe 1 = gute Dendrogramm-Repräsentation der Daten.
</details>

---

### 🔑 Zentrale Python-API (Hierarchical)
```python
from scipy.cluster.hierarchy import linkage, dendrogram, fcluster
from scipy.spatial.distance import pdist

D = pdist(X)                          # Paarweise Distanzen
Z = linkage(D, method='ward')         # Dendrogramm (ward/single/complete/average)
dendrogram(Z)                         # Visualisierung
labels = fcluster(Z, t=3, criterion='maxclust')  # Flache Partition: K=3
```

---

## Kapitel 4 – Density-Based Clustering

### Aufgabe 4.1 – Punkt-Klassifikation
$\varepsilon = 2.0$, $n_{\min} = 4$. Punkt $p$ hat 6 Punkte in seiner $\varepsilon$-Nachbarschaft (inkl. sich selbst). Punkt $q$ hat 2 Punkte in seiner $\varepsilon$-Nachbarschaft, ist aber in der $\varepsilon$-Nachbarschaft von $p$. Punkt $r$ hat 1 Nachbarn und liegt in keiner $\varepsilon$-Nachbarschaft eines Core Points.

Klassifiziere $p$, $q$ und $r$.

<details><summary>Lösung</summary>

- $p$: $|N_\varepsilon(p)| = 6 \geq 4$ → **Core Point**
- $q$: $|N_\varepsilon(q)| = 2 < 4$, aber $q \in N_\varepsilon(p)$ (Core Point) → **Border Point**
- $r$: $|N_\varepsilon(r)| = 1 < 4$, kein Core Point in Reichweite → **Noise Point**
</details>

---

### Aufgabe 4.2 – k-Distance-Plot
Erkläre Schritt für Schritt wie man $\varepsilon$ aus dem k-Distance-Plot bestimmt.

<details><summary>Lösung</summary>

1. Wähle $k = n_{\min} - 1$ (oder $n_{\min}$, je nach Konvention)
2. Berechne für jeden Punkt $x_i$ die Distanz zu seinem $k$-ten Nachbarn: $d_k(x_i)$
3. Sortiere alle $d_k(x_i)$ absteigend und plotte
4. Suche den "Elbow" (Knick) – den Punkt wo die Kurve stark ansteigt
5. Der $d_k$-Wert am Knick ist ein gutes $\varepsilon$

Hintergrund: Punkte in dichten Clustern haben kleines $d_k$; Punkte im Raum zwischen Clustern oder Noise haben großes $d_k$.
</details>

---

### Aufgabe 4.3 – DBSCAN vs K-Means
Nenne drei Situationen wo DBSCAN K-Means übertrifft und eine wo K-Means besser ist.

<details><summary>Lösung</summary>

**DBSCAN besser:**
- Beliebig geformte Cluster (Ringe, Halbmonde, Spiralen)
- Daten mit Ausreißern (DBSCAN labelt sie als Noise, K-Means weist sie erzwungen zu)
- Unbekannte Cluster-Anzahl (DBSCAN bestimmt K automatisch)

**K-Means besser:**
- Sphärische, gleichgroße Cluster ohne Rauschen
- Sehr große Datensätze ($O(nKd)$ pro Iter. vs. $O(n^2)$ für DBSCAN ohne Index)
- Wenn K bekannt und sinnvoll definierbar ist
</details>

---

### 🔑 Zentrale Python-API (DBSCAN)
```python
from sklearn.cluster import DBSCAN
from sklearn.neighbors import NearestNeighbors

# k-Distance-Plot zur eps-Wahl
nbrs = NearestNeighbors(n_neighbors=min_samples).fit(X)
distances, _ = nbrs.kneighbors(X)
k_dists = np.sort(distances[:, -1])[::-1]  # absteigende Sortierung

# DBSCAN
db = DBSCAN(eps=0.5, min_samples=5)
labels = db.fit_predict(X)
# labels == -1: Noise
n_clusters = len(set(labels)) - (1 if -1 in labels else 0)
```

---

## Kapitel 5 – Dimensionality Reduction

### Aufgabe 5.1 – Varianz-Selektion
Du hast zwei Features: $F_1$ mit $\text{Var}=0.02$ und $F_2$ mit $\text{Var}=8.5$. Du wirfst $F_1$ weg. Wann ist das korrekt, wann falsch?

<details><summary>Lösung</summary>

**Korrekt:** Wenn $F_1$ tatsächlich konstantes Rauschen ohne Signalanteil ist und $F_2$ das gesamte Signal trägt.

**Falsch:** Wenn das Signal in einer Linearkombination beider Features liegt (z.B. $y \propto F_1 + F_2$ bei skaliertem $F_1$). In diesem Fall ist PCA besser – es findet die maximale Varianzrichtung auch wenn sie diagonal liegt.
</details>

---

### Aufgabe 5.2 – PCA Schritt für Schritt
Gegeben: $X = \begin{pmatrix} 2 & 4 \\ 4 & 8 \\ 6 & 6 \end{pmatrix}$. Berechne (a) Mittelwert, (b) zentrierte Matrix $\tilde{X}$, (c) Kovarianzmatrix $\Sigma$.

<details><summary>Lösung</summary>

**(a)** $\bar{x} = (4, 6)$

**(b)** $\tilde{X} = \begin{pmatrix} -2 & -2 \\ 0 & 2 \\ 2 & 0 \end{pmatrix}$

**(c)** $\Sigma = \frac{1}{3}\tilde{X}^T\tilde{X} = \frac{1}{3}\begin{pmatrix} 8 & 4 \\ 4 & 8 \end{pmatrix} = \begin{pmatrix} 2.67 & 1.33 \\ 1.33 & 2.67 \end{pmatrix}$
</details>

---

### Aufgabe 5.3 – Erklärte Varianz
Eigenwerte einer PCA: $\lambda_1 = 12, \lambda_2 = 6, \lambda_3 = 2$. Wie viel Varianz erklärt die erste Komponente? Wie viele Komponenten braucht man für 90%?

<details><summary>Lösung</summary>

Gesamt-Varianz = $12+6+2=20$.
- PC1: $12/20 = 60\%$
- PC1+PC2: $18/20 = 90\%$

→ **2 Komponenten** für 90%.
</details>

---

### Aufgabe 5.4 – t-SNE Interpretation
Du siehst in einem t-SNE-Plot drei Cluster: A ist groß, B ist klein, C und D liegen weit voneinander entfernt. Was kannst du valide schlussfolgern, was nicht?

<details><summary>Lösung</summary>

**Valide:**
- Punkte innerhalb von A sind ähnlich (lokale Struktur)
- B enthält eng verwandte Punkte

**Nicht valide:**
- Clustergröße sagt nichts über die Anzahl Datenpunkte aus (t-SNE verzerrt)
- Der große Abstand zwischen C und D ist kein zuverlässiges Maß für ihre echte Unähnlichkeit
- Absolute Positionen im Plot sind durch die Zufallsinitialisierung und Perplexity bestimmt
</details>

---

### 🔑 Zentrale Python-API (PCA, t-SNE)
```python
from sklearn.decomposition import PCA
from sklearn.manifold import TSNE

# PCA
pca = PCA(n_components=2)
Z = pca.fit_transform(X)
explained = pca.explained_variance_ratio_   # Anteil je Komponente
components = pca.components_               # Eigenvektoren (Zeilenvektoren)

# Über NumPy (manuell, wie im Notebook):
X_c = X - X.mean(axis=0)
U, S, Vt = np.linalg.svd(X_c, full_matrices=False)
V_k = Vt[:k].T          # Top-k Eigenvektoren
Z = X_c @ V_k            # Projektion

# t-SNE
tsne = TSNE(n_components=2, perplexity=30, random_state=42)
Z_2d = tsne.fit_transform(X)
```

---

## Kapitel 6 – Variational Inference / VAE

### Aufgabe 6.1 – ELBO
Schreibe die ELBO-Formel auf und erkläre jeden Term.

<details><summary>Lösung</summary>

$$\text{ELBO} = \underbrace{\mathbb{E}_{q_\phi(z|x)}[\log p_\theta(x|z)]}_{\text{Rekonstruktion}} - \underbrace{D_{\text{KL}}(q_\phi(z|x) \| p(z))}_{\text{Regularisierung}}$$

- **Rekonstruktionsterm:** Wie gut kann der Decoder den Input $x$ aus dem Sample $z \sim q_\phi(z|x)$ wiederherstellen? Wird maximiert (weniger Verlust).
- **KL-Term:** Wie nah ist der Posterior $q_\phi(z|x) = \mathcal{N}(\mu(x), \sigma^2(x))$ am Prior $p(z) = \mathcal{N}(0, I)$? Wird minimiert → regularisiert, verhindert Kollaps zu Punktmassen.
</details>

---

### Aufgabe 6.2 – Reparametrisierungstrick
Warum kann man nicht einfach $z \sim \mathcal{N}(\mu, \sigma^2)$ sampeln und Backpropagation anwenden?

<details><summary>Lösung</summary>

Das Sampeln ist eine stochastische, nicht-differenzierbare Operation. Backpropagation benötigt Gradienten, die durch alle Operationen im Berechnungsgraph fließen. Ein Sampling-Schritt hat keinen Gradienten gegenüber $\mu$ und $\sigma$.

**Lösung (Reparametrisierung):** Schreibe $z = \mu + \sigma \odot \varepsilon$ mit $\varepsilon \sim \mathcal{N}(0,I)$. Der Zufall ist jetzt in $\varepsilon$ (kein Parameter), und der Gradient fließt durch die deterministischen Terme $\mu$ und $\sigma$.
</details>

---

### Aufgabe 6.3 – KL Divergenz berechnen
Berechne $D_{\text{KL}}(\mathcal{N}(\mu, \sigma^2) \| \mathcal{N}(0,1))$ für $\mu = 1, \sigma^2 = 2$.

<details><summary>Lösung</summary>

$$D_{\text{KL}} = \frac{1}{2}(\mu^2 + \sigma^2 - \log\sigma^2 - 1) = \frac{1}{2}(1 + 2 - \log 2 - 1) = \frac{1}{2}(2 - 0.693) \approx 0.654$$
</details>

---

### 🔑 Zentrale Python-API (VAE)
```python
# KL Divergenz (geschlossene Form für Gauß vs. N(0,I))
def kl_divergence(mu, log_var):
    # mu, log_var: Tensoren der Form (batch, latent_dim)
    return -0.5 * np.sum(1 + log_var - mu**2 - np.exp(log_var))

# Reparametrisierung
def reparameterize(mu, log_var, rng):
    eps = rng.standard_normal(mu.shape)
    return mu + np.exp(0.5 * log_var) * eps   # z = μ + σ·ε
```

---

## Kapitel 7 – Uncertainty Estimation

### Aufgabe 7.1 – Aleatoric vs. Epistemic
Ordne zu: (a) Ein Sensor misst Temperatur mit ±0.5°C Rauschen. (b) Ein Modell wurde nur auf Katzen und Hunde trainiert, bekommt jetzt ein Pferd. (c) Zwei Ärzte sind uneinig über eine Diagnose anhand eines CT-Scans. (d) Ein Sprachmodell wurde nie mit medizinischen Texten trainiert, soll aber Diagnosen stellen.

<details><summary>Lösung</summary>

- (a) **Aleatoric** – inhärentes Sensor-Rauschen, nicht reduzierbar
- (b) **Epistemic** – Modell hat keine Trainingsdaten für Pferde, reduzierbar durch mehr Daten
- (c) **Aleatoric** – die Daten selbst (CT-Scan) sind mehrdeutig
- (d) **Epistemic** – fehlende Domain-Daten, reduzierbar durch Fine-Tuning
</details>

---

### Aufgabe 7.2 – MC Dropout
5 MC Dropout Passes auf einem In-Distribution-Input geben: $[0.91, 0.89, 0.92, 0.90, 0.93]$. Auf einem OOD-Input: $[0.31, 0.78, 0.55, 0.82, 0.44]$.

Berechne Mittelwert und Varianz für beide. Was schlussfolgert du?

<details><summary>Lösung</summary>

**In-Distribution:** $\bar{y} = 0.91$, $\text{Var} = 0.00024$ → sehr sicher, stabile Vorhersage

**OOD:** $\bar{y} = 0.58$, $\text{Var} \approx 0.041$ → hohe Varianz, Modell ist unsicher, OOD-Signal

→ MC Dropout funktioniert als OOD-Detektor wenn die Varianz deutlich erhöht ist.
</details>

---

### Aufgabe 7.3 – Calibration
Ein Modell gibt bei 100 Samples 80% Konfidenz aus. In Wirklichkeit ist es nur in 55 Fällen richtig. Ist das Modell kalibriert? In welche Richtung ist es fehlkalibriert?

<details><summary>Lösung</summary>

Nein. Kalibriert wäre: 80% Konfidenz → 80% richtig. Das Modell ist **überconfident**: es gibt 80% Konfidenz an, ist aber nur 55% der Zeit richtig. **Temperature Scaling** mit $T > 1$ kann die Softmax-Outputs kalibrieren (Verteilung aufweichen).
</details>

---

### 🔑 Zentrale Python-API (MC Dropout / Calibration)
```python
# MC Dropout: T Passes mit Dropout in Inferenz
def predictive_stats(samples):
    # samples: Array (T, n_classes)
    mean = samples.mean(axis=0)          # Mittlere Vorhersage
    variance = samples.var(axis=0)       # Prädiktive Varianz
    return mean, variance

# Calibration bins (aus Notebook 07)
def calibration_bins(confidence, correct, n_bins=10):
    edges = np.linspace(0, 1, n_bins + 1)
    bin_acc, bin_conf, bin_count = [], [], []
    for lo, hi in zip(edges[:-1], edges[1:]):
        mask = (confidence >= lo) & (confidence < hi)
        if mask.sum() > 0:
            bin_acc.append(correct[mask].mean())
            bin_conf.append(confidence[mask].mean())
            bin_count.append(mask.sum())
    return np.array(bin_acc), np.array(bin_conf), np.array(bin_count)
```

---

## Kapitel 8 – Transfer Learning

### Aufgabe 8.1 – Transfer-Strategien
Du hast folgende Szenarien. Wähle die beste Transfer-Strategie (Frozen Backbone / Fine-Tuning / Zero-Shot / Prompt Engineering):

(a) 10.000 gelabelte Bilder einer neuen Domain (Satelliten-Bilder), ImageNet-Backbone verfügbar.
(b) 50 gelabelte Bilder, gleiche Domain wie das vortrainierte Modell.
(c) Ein Foundation Model (CLIP) und du willst 10 neue Klassen ohne jegliche gelabelte Daten klassifizieren.
(d) Ein LLM und eine neue Task die sich gut als Prompt formulieren lässt.

<details><summary>Lösung</summary>

**(a) Fine-Tuning** – genug Daten, aber andere Domain (Satelliten ≠ ImageNet). Die unteren Layer bleiben evtl. frozen.

**(b) Frozen Backbone + linearer Kopf** – zu wenig Daten für Full Fine-Tuning (Overfitting-Risiko). Die vortrainierten Features sind gut genug für diese Domain.

**(c) Zero-Shot mit CLIP** – Klassen als Text-Prompts, Cosinus-Ähnlichkeit im gemeinsamen Embedding-Raum.

**(d) Prompt Engineering** – keine Gradient-Updates, nur Prompt-Design.
</details>

---

### Aufgabe 8.2 – Linear Probe
Was ist eine Linear Probe und warum ist sie ein guter Diagnostic?

<details><summary>Lösung</summary>

Ein Linear Probe ist eine logistische Regression (oder andere lineare Klassifikator) die auf den eingeforenen Embeddings eines Backbone trainiert wird. 

**Diagnostic:** Nur wenn die Embeddings die Klassen linear separieren, kann der lineare Kopf gut funktionieren. Schlechte Linear-Probe-Performance → Backbone-Features passen nicht zur Ziel-Task → Fine-Tuning nötig oder anderes Backbone wählen.
</details>

---

### 🔑 Zentrale Python-API (Transfer Learning)
```python
from sklearn.linear_model import LogisticRegression

# Linear Probe auf Embeddings
def linear_probe(emb_train, y_train, emb_test, y_test):
    clf = LogisticRegression(max_iter=2000).fit(emb_train, y_train)
    return clf.score(emb_test, y_test)

# Backbone: MLP hidden-layer Aktivierungen als Embeddings
def encode(X, mlp):
    # mlp: sklearn MLPClassifier
    # Aktivierungen der letzten Hidden-Layer
    activations = X.copy()
    for i, (W, b) in enumerate(zip(mlp.coefs_[:-1], mlp.intercepts_[:-1])):
        activations = np.maximum(0, activations @ W + b)  # ReLU
    return activations
```

---

## Kapitel 9 – Self-Supervised Learning

### Aufgabe 9.1 – Pretext Tasks
Erkläre für jede Pretext Task: Was ist das Supervisionssignal und welche Repräsentation lernt das Modell?

(a) Rotation Prediction, (b) Masked Language Modeling (BERT), (c) Contrastive Learning (SimCLR)

<details><summary>Lösung</summary>

**(a) Rotation Prediction:** Signal = Rotationswinkel (0°/90°/180°/270°, automatisch bekannt). Modell lernt: globale Bildorientierung und damit grobe Semantik (Objekte haben eine "richtige" Seite).

**(b) Masked LM:** Signal = maskierte Token (15% der Token, bekannt aus dem Text). Modell lernt: bidirektionalen Kontext, Wort-Bedeutungen und syntaktische Strukturen aus dem Füllen der Lücken.

**(c) SimCLR:** Signal = Augmentierungs-Identität (welche Paare kommen vom gleichen Bild, automatisch bekannt). Modell lernt: augmentierungs-invariante semantische Features – was bleibt gleich nach Crop, Farbe, Rotation.
</details>

---

### Aufgabe 9.2 – NT-Xent Loss
Warum braucht SimCLR einen großen Batch? Was ist das Problem mit kleinen Batches?

<details><summary>Lösung</summary>

Der NT-Xent Loss kontrastiert jeden Anchor gegen **alle anderen** Paare im Batch als Negative:

$$\mathcal{L} = -\log \frac{\exp(\text{sim}(z_i, z_i')/\tau)}{\sum_{k \neq i}\exp(\text{sim}(z_i, z_k)/\tau)}$$

Mit kleinem Batch gibt es wenig Negative → die meisten sind "easy negatives" (sehr verschiedene Punkte) → kleine informativen Gradienten → das Modell lernt nur grobe Unterscheidungen.

Mit großem Batch (4096–8192): viele Negative, darunter auch "hard negatives" (ähnliche Punkte aus anderen Klassen) → starke, informative Gradienten.
</details>

---

### Aufgabe 9.3 – BERT 80/10/10
Warum maskiert BERT nicht alle 15% Token einfach mit [MASK]?

<details><summary>Lösung</summary>

Wenn alle maskierten Token immer als [MASK] erscheinen, lernt das Modell nur [MASK]-Token vorherzusagen und vernachlässigt den unveränderten Text. Bei Inference gibt es kein [MASK] → Mismatch.

Die 80/10/10-Strategie: 80% [MASK], 10% zufälliges Token, 10% unverändertes Token. Das 10% "unverändertes Token" zwingt das Modell, **jeden** Token zu "prüfen" (ist das korrekt?), nicht nur maskierte – besser für Downstream-Tasks wie NER oder QA.
</details>

---

### 🔑 Zentrale Python-API (SSL)
```python
# Masked Token Loss (nur auf maskierten Positionen)
def masked_token_loss(logits, targets, mask_positions):
    # logits: (B, T, V), targets: (B, T), mask_positions: (B, T) bool
    # Nur Loss an maskierten Stellen
    loss = cross_entropy(logits[mask_positions], targets[mask_positions])
    return loss

# Attention (vereinfacht, aus Notebook 09)
def attention(Q, K, V, attn_mask=None):
    d_k = Q.shape[-1]
    scores = Q @ K.T / np.sqrt(d_k)       # (T, T) scaled dot product
    if attn_mask is not None:
        scores = np.where(attn_mask, scores, -1e9)  # Causal Mask
    weights = softmax(scores, axis=-1)
    return weights @ V

# Causal Mask (GPT-style)
def causal_mask(T):
    return np.tril(np.ones((T, T), dtype=bool))
```

---

## Kapitel 10 – Weak Supervision

### Aufgabe 10.1 – Label Function Design
Entwirf 3 Label Functions für die Klassifikation von E-Mails als Spam (1) vs. Kein-Spam (0). Implementiere als Pseudocode.

<details><summary>Lösung</summary>

```python
SPAM, HAM, ABSTAIN = 1, 0, -1

def lf_spam_words(email):
    keywords = ["WINNER", "FREE", "PRIZE", "CLICK HERE", "URGENT"]
    if any(k in email.text.upper() for k in keywords):
        return SPAM
    return ABSTAIN

def lf_many_caps(email):
    cap_ratio = sum(1 for c in email.text if c.isupper()) / len(email.text)
    if cap_ratio > 0.4:
        return SPAM
    return ABSTAIN

def lf_known_domain(email):
    trusted = ["company.com", "university.edu"]
    if any(d in email.sender for d in trusted):
        return HAM
    return ABSTAIN
```
</details>

---

### Aufgabe 10.2 – Majority Vote vs Label-Modell
Drei LFs geben folgende Votes für Datenpunkt $x$: $\lambda_1 = +1$, $\lambda_2 = 0$ (abstain), $\lambda_3 = -1$.

**(a)** Was gibt Majority Vote zurück?
**(b)** Warum ist das Label-Modell hier informationsreicher?

<details><summary>Lösung</summary>

**(a)** Tie: $+1$ und $-1$ je ein Vote (Abstain zählt nicht). Majority Vote gibt zufällig $+1$ oder $-1$ zurück, oder abstain.

**(b)** Das Label-Modell kennt die **Accuracy** von $\lambda_1$ und $\lambda_3$. Wenn $\lambda_1$ empirisch 90% Accuracy hat und $\lambda_3$ nur 60%, gewichtet das Label-Modell $\lambda_1$ stärker → probabilistisches Label nahe bei $P(y=+1)=0.75$ statt einem 50/50-Coin-Flip.
</details>

---

### Aufgabe 10.3 – Dawid-Skene
Was ist die Confusion Matrix in Dawid-Skene und was sagt sie aus?

<details><summary>Lösung</summary>

$\pi_w^{jk} = P(\text{Worker } w \text{ gibt Label } k \mid \text{True Label } j)$

Für einen binären Task (0/1) hat jeder Worker eine $2 \times 2$ Confusion Matrix. Ein guter Worker hat hohe Diagonalwerte (gibt oft das richtige Label). Ein Spammer hat $\pi_w^{jk} \approx 0.5$ (zufällig). Ein adversarialer Worker hat niedrige Diagonalwerte.

EM lernt diese Matrices ohne Gold-Standard Labels, nur aus dem Muster der Worker-Agreements und Disagreements.
</details>

---

## Kapitel 11 – Reinforcement Learning

### Aufgabe 11.1 – Bellman-Update
Q-Tabelle: $Q(s_1, a_1) = 3.0$. Transition: $s_1, a_1 \to r=1, s_2$. $\max_{a'} Q(s_2, a') = 6.0$, $\gamma = 0.9$, $\alpha = 0.2$.

Berechne neues $Q(s_1, a_1)$.

<details><summary>Lösung</summary>

TD-Target $= 1 + 0.9 \cdot 6.0 = 6.4$

TD-Error $= 6.4 - 3.0 = 3.4$

$Q(s_1, a_1) \leftarrow 3.0 + 0.2 \cdot 3.4 = 3.68$
</details>

---

### Aufgabe 11.2 – Exploration vs. Exploitation
Du verwendest $\varepsilon$-greedy mit $\varepsilon = 0.1$. In einem Zustand $s$ sind die Q-Werte: $Q(s, a_1)=5, Q(s, a_2)=3, Q(s, a_3)=1$.

Wie hoch ist die Wahrscheinlichkeit jede Aktion zu wählen?

<details><summary>Lösung</summary>

- Greedy-Aktion: $a_1$ (höchstes Q)
- Zufällig: je gleichverteilt mit $\varepsilon/|A| = 0.1/3 \approx 0.033$

$P(a_1) = (1 - \varepsilon) + \varepsilon/3 = 0.9 + 0.033 = 0.933$

$P(a_2) = P(a_3) = \varepsilon/3 = 0.033$
</details>

---

### Aufgabe 11.3 – DQN Stabilisierungstricks
Ein DQN-Training divergiert: Loss steigt nach 10.000 Steps stark an. Nenne drei mögliche Ursachen und Lösungen.

<details><summary>Lösung</summary>

1. **Kein/kleines Target Network Update-Intervall:** Das TD-Target verändert sich zu schnell. Lösung: Target Network $\theta^-$ alle $C = 1000$–$10000$ Schritte updaten.

2. **Kein Experience Replay:** Korrelierte sequentielle Erfahrungen stören das Mini-Batch-Training. Lösung: Replay Buffer $D$ der Größe 10K–1M, zufälliges Sampling.

3. **Zu hohe Lernrate:** Große Gradient-Updates destabilisieren die Q-Approximation. Lösung: $\alpha$ reduzieren (typisch $10^{-4}$ mit Adam).
</details>

---

### Aufgabe 11.4 – Policy Gradient vs. Q-Learning
Wann bevorzugst du Policy Gradient (REINFORCE/PPO) gegenüber Q-Learning/DQN?

<details><summary>Lösung</summary>

**Policy Gradient wählen wenn:**
- **Kontinuierliche Aktionsräume:** Q-Learning braucht $\arg\max_a Q(s,a)$ – über kontinuierliche Räume nicht trivial. Policy Gradient parametrisiert $\pi_\theta(a|s)$ direkt.
- **Stochastische Policies nötig:** Manche Tasks brauchen echte Stochastizität (z.B. Poker). Q-Learning ist deterministisch.
- **Stabilität wichtig:** PPO begrenzt Policy-Updates → stabiler.

**Q-Learning wählen wenn:**
- Diskreter kleiner Aktionsraum
- Off-Policy Learning erwünscht (Experience Replay, alte Daten nutzbar)
</details>

---

### 🔑 Zentrale Python-API (RL)
```python
# Q-Learning Update
def q_learning_update(Q, s, a, r, s_next, done, alpha, gamma):
    td_target = r + (1 - done) * gamma * Q[s_next].max()
    td_error = td_target - Q[s, a]
    Q[s, a] += alpha * td_error
    return Q

# ε-greedy Action Selection
def pick_epsilon_greedy(Q_row, eps, rng):
    if rng.random() < eps:
        return rng.integers(len(Q_row))   # zufällig
    return Q_row.argmax()                  # greedy

# REINFORCE Policy Gradient
def policy_gradient(theta, phis, actions, advantages):
    # theta: Policy-Parameter, phis: State-Features
    # Gradient: sum_t G_t * grad log pi(a_t|s_t)
    logits = phis @ theta
    probs = softmax(logits)
    grad = np.zeros_like(theta)
    for phi, a, adv in zip(phis, actions, advantages):
        p = softmax(phi @ theta)
        grad += adv * phi[:, None] * (np.eye(len(p))[a] - p)
    return grad
```

---

## Kapitelübergreifende Konzeptfragen

### Aufgabe K.1 – Paradigmen
Ordne zu: Supervised / Unsupervised / Self-Supervised / Reinforcement Learning:

(a) K-Means Clustering, (b) ImageNet-Training mit Labels, (c) SimCLR, (d) AlphaGo, (e) BERT Pre-Training, (f) Anomalie-Erkennung mit DBSCAN

<details><summary>Lösung</summary>

- (a) Unsupervised
- (b) Supervised
- (c) Self-Supervised (Contrastive)
- (d) Reinforcement Learning
- (e) Self-Supervised (Masked LM)
- (f) Unsupervised
</details>

---

### Aufgabe K.2 – Latenter Raum
Erkläre den Unterschied zwischen dem latenten Raum eines Autoencoders, eines VAE und eines SimCLR-Modells.

<details><summary>Lösung</summary>

- **Autoencoder:** Deterministisch, keine Prior-Annahme. Latenter Raum hat keine garantierte Struktur, kann Lücken haben. Nicht generierbar.
- **VAE:** Probabilistisch ($z \sim \mathcal{N}(\mu, \sigma^2)$, KL-Term erzwingt Prior $\mathcal{N}(0,I)$). Glatter, vollständiger Raum. Generierbar durch $z \sim p(z)$.
- **SimCLR:** Kein Decoder. Latenter Raum (nach Projektionskopf) ist so strukturiert dass augmentierte Versionen desselben Bilds nah beieinander liegen. Normalisiert auf Einheitssphäre (L2-Norm nach Projektion).
</details>

---

### Aufgabe K.3 – Wann welche Clustering-Methode?
Fülle die Tabelle aus:

| Szenario | Beste Methode | Begründung |
|---|---|---|
| Ringe und Spiralen, kein Rauschen | ? | ? |
| Hierarchische Struktur gewünscht, K unbekannt | ? | ? |
| Sehr großer Datensatz, K bekannt, sphärische Cluster | ? | ? |
| Unbekannte Clusteranzahl, Ausreißer erwartet | ? | ? |

<details><summary>Lösung</summary>

| Szenario | Beste Methode | Begründung |
|---|---|---|
| Ringe und Spiralen | DBSCAN | Dichte-basiert, keine Centroid-Annahme |
| Hierarchische Struktur, K unbekannt | Agglomeratives Clustering | Dendrogramm zeigt alle K, deterministisch |
| Groß, K bekannt, sphärisch | K-Means (K-Means++) | $O(nKd)$, skalierbar, optimal für sphärische Cluster |
| K unbekannt, Ausreißer | DBSCAN | Automatisches K + Noise-Label |
</details>

---

#### Flashcards (Kapitelübergreifend)

Was ist der Unterschied zwischen Supervised, Unsupervised und Self-Supervised Learning?
?
- **Supervised:** Labels $y$ vorhanden, Modell lernt $x \to y$
- **Unsupervised:** Keine Labels, Modell entdeckt Struktur in $x$ selbst
- **Self-Supervised:** Labels werden automatisch aus den Daten generiert (Pretext Tasks). Kein menschlicher Annotationsaufwand.

Nenne drei Maßnahmen gegen den Curse of Dimensionality.::(1) Dimensionality Reduction (PCA, Autoencoder), (2) Feature-Selektion (Varianz-Ranking), (3) Kernel-Methoden die implizit mit Distanzen arbeiten.

Was haben VAE, SimCLR und BERT gemeinsam?::Alle drei sind Self-Supervised / Generative Methoden die nützliche latente Repräsentationen aus unlabelten Daten lernen – ohne externe Labels. VAE durch Rekonstruktion, SimCLR durch kontrastives Lernen, BERT durch Masked Language Modeling.

Welche RL-Methode ist Standard für RLHF (Fine-Tuning von Sprachmodellen)?::PPO (Proximal Policy Optimization) – Policy Gradient Methode die Policy-Updates begrenzt (Clipping) um stabile, schrittweise Optimierung zu garantieren.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[UL Übungen]]
SORT file.mtime DESC
```
