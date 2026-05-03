email
LoRa Mond Datensatz ESA (FFT um dunkle Flecken zu finden?)
$n_{min}$ = 3 auf S. 64 Fig. 57 beißt sich mit S. 63 Fig. 53 $n_{min}$= 2 wegen Hinzufügen von $x_8$



Hierarchical Clustering

Hierarchical Clustering Algorithm nach Ward
-> bottom up (Agglomerative Hierarchical Clustering)
1. Jeder Punkt wird ein Cluster
2. Für alle Punkte die Distanzen berechnen
3. Punkte mit den niedrigsten Distanzen kommen in ein Cluster
4. Entferne die Punkte aus der active cluster Menge
5. Wiederhole bis $|active| = 1$
-> Es wird immer global alle DistanzPen betrachten
Man kann also am Anfang alle Distanzen der Punkte einmal berechnen und am Ende muss man sie nur noch nachschauen (lookup)
Nachteil ist sehr greedy aber findet nicht unbedingt die minimale Distanz

K Means kann sich korrigieren aber HC nicht
HC weiß er merged n-1 mal
Single linkage
man nimmt den punkt im cluster, der die niedrigste distanz hat zu allen anderen punkten außerhalb des clusters (muss nicht fix ein Punkt sind)
Complete Linkage
Max statt Min -> funktioniert gleich
Average Linkage
Distanzen der Cluster über ihre Zentroide (bzw. heißt es Average weil man die Distanzen zu den Punkten im Cluster mittel) -> Man kauft sich Accuracy durch Compute
Ward's Method
Statt Average euklidisch nimmt er die Average quadrierte Distanzen
Chaining and Bridging kann das Clustering zerstören (Max Distanz)
Entscheiden zwischen Distanzen tut immer der arg min aber welche Distanz (Linkage) man wählt kann unterschiedlich sein (max, min, average, k-nearest?)

## Density Based Clustering

Dichte meint Punkte pro Fläche/Volumen/Hypervolumina
punkte, die viel in ihrer Nachbarschaft haben und punkte, die wengier oder nur sich selbst in ihrer Nachbarschaft haben.
Wenn ein noise point in seiner Nachbarschaft einen core point hat, dann zählt er trotzdem noch mit dazu (Heuristik, er heißt dann border point)
Die Frage ist, wie man sein $n_{min}$ setzt

Algo:
Radius setzen, 
...
n_min setzen, epsilon setzen
DB schlägt fehl, wenn die Dichten sehr stark variieren (Skalierung / Mahalanobis löst es) und es gibt hier auch das Problem mit Bridging & Chaining

OPTICS, DBSCAN, HDBSCAN
Verständnis bis S.76
### Dimensionality Reduction
Wertebereich ist tückisch, wenn Daten nicht normiert und skaliert sind. Hier ist wieder die Varianz bzw. dann die Mahalanobisdistanz wetvoll.

Sinn, wieso müssen wir die Dimensionen reduzieren? -> zu viele Dimensionen erschweren uns die Verarbeitung und nehmen uns die Möglichkeit, via Generalisierung Aussagen über neue Datenpunkte zu treffen.
(Triviales 1:1 Mapping)

In der Welt sind Daten oft hochdimensional, wobei der Großteil der Dimensionen nicht maßgeblich zur Information beitragen. Man geht von einer **intrinsischen Dimensionalität** aus. Diese ist viel kleiner, als die tatsächliche Anzahl der Dimensionen.
In hohen Dimensionen schwindet unsere Fähgikeit, Cluster zu bilden -> Curse of Dimensionality. 
Bei hohen Dimensionen wird Information oft mehrfach (redundant) oder voneinander abhängig (entangled) dargestellt. 
Bei hohen Dimensionen sind Daten extrem schwer zu interpretieren -> wir können uns 1000D nicht vorstellen, aber 2D schon

Wie reduziert man nun Dimensionen? 
Man braucht ein Muster, das alle Informationen behält, die für die "Essenz" wichtig sind, aber den Rest wegwirft.
Dieses Muster muss Dimensionen enthalten, die nicht auf das Original beschränkt sind, sodass versteckte Informationen sichtbar werden.
Es gibt verschiedene Muster/Arten Dimensionen zu reduzieren, bei jedem trifft man utnerschiedliche Annahmen, die zu unterscheidlichen Use Cases passen. 

Curse of Dimensionality
Variance-Based Feature Selection
Principal Component Analysis
(Auf einer Datenpunktauflösung -> danach wie es mit Vektorisierung geht)

29.04.

---

30.04.

Schickes Embedding durch Beta-Scheduling von KL (bzw. Ränge von LoRA)

### Uncertainty Estimation
Anomaly Detection







