# Übungsaufgaben: Unsupervised Learning

Dieses Dokument enthält alle Übungen, Hands-on-Erfahrungen und Reflexionsfragen aus den Vorlesungsnotizen, gruppiert nach Themen.

---

## 1. Ähnlichkeit und Distanz (Similarity and Distance)

### Hands-On Experience: Punktgruppen finden
Betrachte sechs Datenpunkte in zwei Dimensionen (Abbildungen im Dokument).
- Welche Punkte scheinen zusammenzugehören? Warum denkst du das?
- Wie viele Gruppen siehst du?
- Welcher Gruppe würdest du neue Punkte zuweisen? Zeichne Bereiche um jede Gruppe.
- **Ambivalenz:** Füge den Punkt (3,7) hinzu. Zu welcher Gruppe gehört er jetzt? Wie ändert das deine Annahmen über das ursprüngliche Muster?

### Rechenübungen (Manuelle Berechnung)
Gegeben sind die Punkte $A=(2,5,1)$, $B=(6,1,3)$ und $C=(4,5,2)$.
1. Berechne die **Euklidische Distanz** $d_E(A,B)$.
2. Berechne die **Manhattan-Distanz** $d_M(A,C)$.
3. Berechne die **Kosinus-Ähnlichkeit** $sim(A,B)$ und die entsprechende Kosinus-Distanz.

### Szenario-basierte Auswahl der Metrik
Entscheide, welche Distanzmetrik für die folgenden Szenarien am besten geeignet ist und begründe deine Wahl:
- **News-Plattform:** 10.000 Artikel als Wortfrequenz-Vektoren (unterschiedliche Längen).
- **Lieferdienst:** Routenplanung im Straßennetz von Manhattan (Koordinaten: Straße, Avenue).
- **Kaffee-Qualitätslabor:** Messung von Säure (0-200) und Bitterkeit (0-500) pro Charge.

### Mahalanobis-Distanz
Gegeben sind drei Kaffeechargen: $P_1=(80,400)$, $P_2=(200,160)$, $P_3=(110,220)$.
1. Berechne die Stichproben-Kovarianzmatrix $\Sigma$.
2. Berechne die Mahalanobis-Distanz zwischen $P_1$ und $P_3$.
3. Vergleiche das Ergebnis mit der Euklidischen Distanz. Warum ist die Mahalanobis-Distanz hier kleiner/anders?

### Effekt der Standardisierung
Gegeben sind drei Cafés mit (verkaufte Tassen, Kundenbewertung 1-10): $C_1=(300,7), C_2=(500,6), C_3=(700,3)$.
1. Berechne die Euklidische Distanz auf den Rohdaten zwischen den Paaren.
2. Führe eine **Z-Score-Normalisierung** durch.
3. Berechne die Distanzen erneut. Wie verschiebt sich die Ähnlichkeit zwischen $C_2$ zu $C_1$ vs. $C_3$?

### Selbstreflexion
- Wie unterscheidet man zwischen Supervised und Unsupervised Learning?
- Erläutere den Unterschied zwischen $	ilde{y}$, $\hat{y}$ und $y$.
- Was sind die Schlüsseleigenschaften einer Distanzmetrik?
- Was passiert, wenn Merkmale sehr unterschiedliche Skalen oder Größenordnungen haben?

---

## 2. Centroid Clustering (K-Means)

### Hands-On Experience: Zentroid-Platzierung
Betrachte zwölf Datenpunkte in 2D.
- Wie viele Cluster siehst du? Könnte man für 1, 2 oder 6 Cluster argumentieren?
- Wo würdest du einen repräsentativen Punkt (Zentroid) für jeden Cluster platzieren?

### Rechenübungen (Algorithmus-Trace)
Gegeben sind drei Punkte: $x_1=(1,1), x_2=(3,1), x_3=(8,7)$. Führe eine vollständige K-Means Iteration mit $K=2$ durch. Startzentroiden: $c_1=(0,3), c_2=(6,5)$.
1. **Assignment-Schritt:** Weise jeden Punkt dem nächsten Zentroiden zu (quadrierte Distanzen nutzen).
2. **Update-Schritt:** Berechne die neuen Zentroiden $\mu_1'$ und $\mu_2'$ als Mittelwert der zugewiesenen Punkte.
3. **Konvergenz:** Prüfe, ob sich die Zuweisung in einer weiteren Iteration ändern würde.
4. **Trägheit (Inertia):** Berechne die Inertia $J$ für das Ergebnis.

### Wahl von K
1. **Elbow-Methode:** Gegeben sind Inertia-Werte für $K=1 (J=50), K=2 (J=2), K=3 (J=0)$. Skizziere die Kurve und identifiziere den "Ellbogen". Welches K wählst du?
2. **Silhouette Score:** Berechne die Silhouette-Werte $s(i)$ für die drei Punkte aus der obigen Übung bei $K=2$. Hinweis: $s(x_1)$ für einen Single-Cluster wird per Konvention auf 0 gesetzt.

### Fehlermodi
- Überlege dir Szenarien, in denen K-Means versagt (nicht-konvexe Formen, unterschiedliche Dichte, Ausreißer). Wie beeinflussen diese das Ergebnis?

### Selbstreflexion
- Was minimiert die K-Means Zielfunktion genau?
- Warum garantiert Konvergenz nicht die beste Lösung?
- Wie können wir den Effekt von Ausreißern abschwächen? (Hinweis: K-Medoids).

---

## 3. Hierarchisches Clustering

### Hands-On Experience: Bottom-Up Aufbau
Betrachte die sechs kanonischen Punkte.
- Baue eine Hierarchie bottom-up auf: Welche Punkte sind sich am nächsten? Verbinde sie. Was ist das nächste Paar?
- Auf welcher Distanz-Ebene würdest du den Baum schneiden, um 2 oder 3 Gruppen zu erhalten?

### Rechenübungen (Agglomeratives Clustering)
Nutze dieselben drei Punkte wie bei K-Means: $x_1=(1,1), x_2=(3,1), x_3=(8,7)$.
1. **Distanztabelle:** Berechne alle paarweisen Euklidischen Distanzen.
2. **Single Linkage:** Führe die Merges schrittweise durch und dokumentiere die Merge-Höhe.
3. **Ward-Linkage Update:** Berechne nach dem ersten Merge von $x_1$ und $x_2$ die Ward-Distanz zum verbleibenden Punkt $x_3$. Hinweis: $D_{Ward}(C_a, C_b) = rac{n_a \cdot n_b}{n_a + n_b} ||\mu_a - \mu_b||^2$.

### Dendrogramm-Analyse
- Wie liest man die Anzahl der Cluster aus einem Dendrogramm ab?
- Was bedeutet ein großer vertikaler Abstand ("Gap") zwischen zwei Merges?

### Selbstreflexion
- Was ist der Vorteil der deterministischen Natur des hierarchischen Clusterings gegenüber K-Means?
- Erkläre "Chaining" bei Single Linkage.
- Warum ist die Speicherkomplexität $O(n^2)$ ein Problem für große Datensätze?

---

## 4. Dichtebasiertes Clustering (DBSCAN)

### Hands-On Experience: Kreise ziehen
Betrachte die sieben kanonischen Punkte (inkl. $x_7=(4,5)$).
- Zeichne Kreise mit Radius $\epsilon=2.5$ um jeden Punkt.
- Zähle, wie viele Punkte in jedem Nachbarschaftsbereich liegen.
- Welche Punkte liegen in "dichten" Regionen, welcher liegt in einer "spärlichen" Region?

### Rechenübungen (DBSCAN Trace)
Gegeben sind sieben Punkte $x_1$ bis $x_7$ (siehe Koordinaten in Kapitel 4). Parameter: $\epsilon=2.5, n_{min}=2$.
1. **Klassifizierung:** Bestimme für jeden Punkt, ob er ein Core Point ($p_c$), Border Point ($p_b$) oder Noise Point ($p_n$) ist.
2. **Cluster-Zuweisung:** Identifiziere die resultierenden Cluster $C_1, C_2$ und die Rauschmenge.
3. **Parameter-Sensitivität:** Was passiert, wenn du $\epsilon$ auf 4.5 erhöhst? Wird $x_7$ dann Teil eines Clusters?

### Dichte-Konzepte
1. **Core Distance:** Berechne für einen Datensatz mit $n_{min}=3$ den kleinsten Radius $\epsilon_c(x_i)$, der mindestens 3 Punkte einschließt.
2. **Mutual Reachability:** Berechne $d_{mreach}(x_4, x_5) = \max\{\epsilon_c(x_4), \epsilon_c(x_5), d(x_4, x_5)\}$.

### Fluch der Dimensionalität
- Berechne den mittleren Abstand zum nächsten Nachbarn $d_{NN} \propto N^{-1/d}$ für $N=100$ bei $d=2, 10, 50, 100$. Ab welcher Dimension überschreitet der Abstand 0.9? Was bedeutet das für DBSCAN?

### Selbstreflexion
- Warum muss man bei DBSCAN das K nicht im Voraus wählen?
- Wie unterscheidet sich die Behandlung von Ausreißern bei DBSCAN im Vergleich zu K-Means?

---

## 5. Dimensionsreduktion (PCA & t-SNE)

### Hands-On Experience: Merkmalswahl
Betrachte Datenpunkte, die stark entlang der y-Achse variieren, aber kaum entlang der x-Achse.
- Welches Merkmal würdest du behalten? Wie viel Information geht verloren?
- Was passiert, wenn die Daten diagonal ($y=x$) verlaufen? Funktioniert einfaches Weglassen eines Merkmals dann noch gut?

### Rechenübungen (PCA Schritt für Schritt)
Nutze die sechs kanonischen Punkte (siehe Kapitel 5).
1. **Zentrierung:** Berechne den Mittelwert $ar{x}$ und subtrahiere ihn von allen Punkten.
2. **Kovarianzmatrix:** Berechne $\Sigma = 	ilde{X}^T 	ilde{X} / n$.
3. **Eigenwerte & Eigenvektoren:** Berechne die Eigenwerte $\lambda_1, \lambda_2$ der Kovarianzmatrix. Bestimme den Eigenvektor $w_1$ zum größten Eigenwert (PC1).
4. **Erklärte Varianz:** Welchen Anteil der Gesamtvarianz erklärt PC1?
5. **Projektion & Rekonstruktion:** Projiziere Punkt $x_1$ auf PC1 ($z_1 = 	ilde{x}_1^T w_1$). Rekonstruiere ihn zurück in den 2D-Raum ($\hat{x}_1 = z_1 \cdot w_1$). Berechnen den Rekonstruktionsfehler $||	ilde{x}_1 - \hat{x}_1||^2$.

### Selbstreflexion
- Was ist der Unterschied zwischen "Feature Selection" und "Feature Transformation"?
- Was besagt die "Manifold Hypothesis"?
- Warum sollte man t-SNE oder UMAP Einbettungen niemals als Features für einen nachgelagerten Klassifikator verwenden?

---

## 6. Variationale Inferenz (Autoencoder & VAE)

### Hands-On Experience: Das Encoder-Decoder Spiel
Bilde Zweiergruppen (Encoder & Decoder). Nutze Ziffernkarten 0, 1, 3, 7, 8.
1. **Feature Design:** Der Encoder wählt zwei Merkmale (z.B. "Anzahl geschlossener Schleifen", "Gerader vertikaler Strich").
2. **Spiel:** Der Encoder sieht eine Ziffer und schreibt nur die zwei Merkmalswerte $(z_1, z_2)$ auf. Der Decoder muss raten, welche Ziffer es ist.
3. **Stress-Tests:** - Reduziere auf nur ein Merkmal ($z_1$). 
   - Nutze nur binäre Merkmale (0 oder 1).
   - Füge mehr Ziffern hinzu (2, 4, 5, 9).
4. **Beobachtung:** Wann steigt der Rekonstruktionsverlust? Wie hilft ein gemeinsames "Codebuch" (Prior)?

### Rechenübungen (VAE Metriken)
1. **KL-Divergenz Penalty:** Berechne die KL-Divergenz für eine Gauß-Verteilung $q(z) = N(\mu, \sigma^2)$ gegenüber dem Standard-Normal-Prior $p(z) = N(0, 1)$. Teste $\mu=2, \sigma=1$ und $\mu=0, \sigma=2$. Welche Abweichung ist "teurer"?
2. **$eta$-VAE Balance:** Berechne den Gesamtverlust $L_eta = L_R + eta \cdot L_{KL}$ für $eta \in \{0.5, 1, 4\}$ bei gegebenen Teilverlusten.
3. **Aktive Einheiten zählen:** Analysiere eine Tabelle von per-Dimension KL-Werten (siehe Kap. 6). Welche Dimensionen sind "kollabiert", welche leisten Arbeit?

### Latente Interpolation
- Beschreibe den Pfad einer Interpolation im latenten Raum:
  - **Pfad 1:** Sanfter Übergang von einer 3 in eine 8.
  - **Pfad 2:** Die 3 bleibt lange gleich, springt dann plötzlich zur 8.
  - **Pfad 3:** Der Pfad führt über eine 2 und eine 5 zur 8.
- Was sagt uns jeder Pfad über die Qualität des gelernten latenten Raums?

### Selbstreflexion
- Warum versagt ein deterministischer Autoencoder als generatives Modell?
- Was bewirkt der "Reparameterization Trick" $z = \mu + \sigma \odot \epsilon$?
- Was ist "Posterior Collapse" und wie kann man ihn verhindern?

---

## 7. Weitere Themen (Reflexion)

### Transfer Learning
- Warum funktioniert One-Shot Learning auf einem vortrainierten "Backbone", aber nicht beim Training von Grund auf?
- Welche Rolle spielen Klassen-Zentroide als Ankerpunkte in der Einbettung?
- Warum wird der Klassifikationskopf ("Head") meist weggeworfen, wenn man auf eine neue Aufgabe transferiert?

### Self-Supervised Learning
- Was passiert, wenn eine "Pretext Task" zu einfach ist?
- Warum ist der Kontrastive Ansatz (ähnliche Ansichten desselben Bildes zusammenführen) oft stärker als handgefertigte Aufgaben wie Rotationsvorhersage?
- Erkläre das Prinzip des "Denoising" im Kontext von BERT oder Masked Autoencodern.

### Reinforcement Learning
- Warum erlaubt die Markov-Eigenschaft einem Agenten, über die Zukunft nachzudenken, ohne die gesamte Vergangenheit mitzuschleifen?
- Was ist der Unterschied zwischen wertbasierten (Value-based) und richtlinienbasierten (Policy-based) Methoden?
- Welches Problem löst der "Experience Replay Buffer" in DQN?
