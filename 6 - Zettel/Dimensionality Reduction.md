#Note

2026-06-24

Tags: [[Unsupervised Learning]], [[Dimensionality Reduction]], [[PCA]], [[t-SNE]]
#UL

---

## Kapitel 5 – Dimensionality Reduction

> *"Folding and Unfolding Space."*

### The Why

Reale Daten $\mathbf{X} \in \mathbb{R}^{n \times d}$ sind hochdimensional (Bilder: Millionen Pixel, Text: Tausende Embedding-Dim.), aber die **intrinsische Dimensionalität** ist oft viel kleiner. MNIST-Ziffern ($784$ Dim.) haben $k \approx 12$–$14$ effektive Dimensionen.

**Warum reduzieren?**
- **Curse of Dimensionality:** Abstände werden ununterscheidbar, Cluster-Methoden verlieren ihre Kraft
- **Rechenkosten:** Distanzen $O(nd)$, Kovarianzmatrizen $O(d^2)$, Eigendekomposition $O(d^3)$
- **Redundanz:** Korrelierte Features tragen gleiche Info
- **Interpretierbarkeit:** Visualisierung in 2D/3D

**Lernziele:**
- Naïve Varianz-basierte Feature-Selektion und ihre Grenzen
- PCA-Zielfunktion und Verbindung zu SVD
- t-SNE und UMAP für Visualisierung; korrekte Interpretation

---

### Theorie

#### Naïve Baseline: Varianz-basierte Feature-Selektion

$$\text{Var}(x^{(j)}) = \frac{1}{n} \sum_{i=1}^n \bigl(x_i^{(j)} - \bar{x}^{(j)}\bigr)^2$$

Behalte die $k$ Features mit höchster Varianz. **Funktioniert nur**, wenn die Signal-Richtungen mit den Koordinatenachsen ausgerichtet sind.

**Versagt:** Wenn Signal diagonal liegt – beide Features haben gleiche Varianz, kein kann sinnvoll verworfen werden.

---

#### Principal Component Analysis (PCA)

**Idee:** Finde neue Richtungen (Hauptkomponenten) die die Varianz maximieren.

**Schritt-für-Schritt:**

1. **Zentrierung:** $\tilde{X} = X - \bar{x}$
2. **Kovarianzmatrix:** $\Sigma = \frac{1}{n} \tilde{X}^T \tilde{X} \in \mathbb{R}^{d \times d}$
3. **Eigendekomposition:** $\Sigma = V \Lambda V^T$ (oder SVD von $\tilde{X}$)
4. **Projektion:** $Z = \tilde{X} V_k$ (die $k$ größten Eigenvektoren)

**Zielfunktion:** Maximiere projizierte Varianz = minimiere Rekonstruktionsfehler.

$$\text{PCA} = \arg\max_V \text{Var}(\tilde{X} V) = \arg\min_V \|\tilde{X} - \tilde{X} V V^T\|_F^2$$

**Erklärte Varianz:** $\frac{\lambda_j}{\sum_i \lambda_i}$ für Komponente $j$.

**Eigenschaften:**
- Linear, deterministisch, global
- Erhält euklidische Abstände maximal
- Linearer Autoencoder ohne Aktivierungsfunktionen → gleicher Unterraum wie PCA

**Grenzen:** Kann nur lineare Strukturen erfassen; curved manifolds, diskrete Cluster → nicht optimal.

---

#### t-SNE (t-distributed Stochastic Neighbor Embedding)

**Für Visualisierung** (2D/3D), nicht für Preprocessing.

**Idee:**
1. Im Hochdimensionalen: definiere Ähnlichkeit als Gauß-Wahrscheinlichkeit $p_{ij}$
2. Im Niedrigdimensionalen: definiere Ähnlichkeit mit t-Verteilung $q_{ij}$ (schwerere Tails)
3. Minimiere KL-Divergenz: $\text{KL}(P \| Q) = \sum_{ij} p_{ij} \log \frac{p_{ij}}{q_{ij}}$

**Wichtige Hyperparameter:**
- **Perplexity** (~5–50): effektive Nachbarzahl, bestimmt lokale vs. globale Struktur
- **Learning rate, Iterations**

**Korrekte Interpretation:**
- ✓ Lokale Cluster sind aussagekräftig
- ✗ Abstände zwischen Clustern NICHT interpretieren
- ✗ Clustergröße NICHT interpretieren
- ✗ Nicht deterministisch

---

#### UMAP (Uniform Manifold Approximation and Projection)

Schneller als t-SNE, skaliert besser, bewahrt mehr globale Struktur.

| | t-SNE | UMAP |
|---|---|---|
| Geschwindigkeit | Langsam ($O(n^2)$ naïv) | Schnell |
| Globale Struktur | Schlecht | Besser |
| Deterministisch | Nein | Nein |
| Für Preprocessing | Nein | Eingeschränkt |

---

### Curse of Dimensionality – Quantitativ

Mittlerer Nächster-Nachbar-Abstand: $d_{NN} \propto N^{-1/d}$

Bei $N=100$ Punkten und $d=50$ ist jeder Punkt fast gleich weit von jedem anderen entfernt. **Johnson-Lindenstrauss-Lemma:** $n$ Punkte können auf $O(\log n / \varepsilon^2)$ Dim. projiziert werden unter Beibehaltung paarweiser Abstände auf $(1\pm\varepsilon)$.

---

### Übungen

#### Aufgabe 1
Wann reicht Varianz-basierte Feature-Selektion? Wann braucht man PCA?

**Lösung:**
Varianz-Selektion reicht wenn Signalrichtungen mit Koordinatenachsen übereinstimmen (ein Feature nahe konstant, das andere trägt Signal). PCA wird gebraucht wenn das Signal diagonal oder anders kombiniert in mehreren Features liegt – dann konstruiert PCA neue Richtungen.

#### Aufgabe 2
Wie viele Hauptkomponenten wählt man bei PCA?

**Lösung:**
Plot der kumulativen erklärten Varianz gegen $k$. Typisch: Elbow-Methode oder ein Schwellenwert (z.B. 95% der Gesamtvarianz). Alternativ: Cross-Validation auf dem Downstream-Task.

#### Aufgabe 3
Darf man aus einem t-SNE-Plot schließen, dass Cluster A und B weit voneinander entfernt sind?

**Lösung:**
Nein. t-SNE minimiert KL-Divergenz, die stark auf lokale Abstände fokussiert. Globale Abstände zwischen Clustern sind artifiziell und hängen stark von Perplexity und Zufallsinitialisierung ab. Nur lokale Cluster-Zugehörigkeit ist aussagekräftig.

---

#### Flashcards

Was ist der Unterschied zwischen Feature-Selektion und Feature-Extraktion?::**Selektion** behält existierende Features (z.B. Varianz-Ranking). **Extraktion** konstruiert neue Features als Kombination der Originalen (z.B. PCA, Autoencoder).

Was optimiert PCA?
?
PCA maximiert die projizierte Varianz (äquivalent: minimiert Rekonstruktionsfehler). Die Projektionsrichtungen sind die Eigenvektoren der Kovarianzmatrix $\Sigma = \frac{1}{n}\tilde{X}^T\tilde{X}$, geordnet nach absteigendem Eigenwert.

Warum verwendet t-SNE eine t-Verteilung im niedrigdimensionalen Raum?::Die t-Verteilung hat schwerere Tails als die Gauß-Verteilung. Das verhindert, dass mittlere Distanzen im niedrigdimensionalen Raum zusammengedrängt werden (Crowding Problem). Weit entfernte Punkte werden explizit auseinandergedrückt.

Welche Aussagen aus einem t-SNE-Plot sind valide?::Nur lokale Cluster-Zugehörigkeit. Abstände zwischen Clustern, Clustergröße und Ausreißerstatus sind NICHT interpretierbar.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[05 Dimensionality Reduction]]
SORT file.mtime DESC
```
