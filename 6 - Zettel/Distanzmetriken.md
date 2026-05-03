
#Note

2026-05-03

Tags: [[Metrik]], [[Mathematik]], [[Lineare Algebra]], [[Unsupervised learning]], [[Machine Learning]], [[Feature-Transformation]]
#UL

---
Da es im Unsupervised Learning keine Labels gibt, brauchen wir eine andere Art, Daten voneinander zu unterscheiden. Das Fundament dafür ist die Definition von Distanzmetriken $d(x, y)$. 
In unserem Datenraum, dem Feature Space, repräsentiert jeder Datenpunkt einen Vektor. Die Wahl der Distanzmetrik kodiert die Annahme darüber, was im jeweiligen Kontext als „ähnlich“ gilt. Jede [[Metrik]] muss Nicht-Negativität, Identität, Symmetrie und die Dreiecksungleichung erfüllen ([[Axiome]]).

### Euklidische Distanz
Misst die direkte "Luftlinie" zwischen zwei Punkten. Sie nimmt an, dass alle Dimensionen gleich wichtig sind und in den selben Einheiten gemessen werden.

$$d_{Euclidean}(x, y) = \sqrt{\sum_{i=1}^d (x_i - y_i)^2}$$
### Manhattan Distanz ($L_1$-Norm)
Misst den achsenparallelen Pfad (Taxicab-Distanz). Besonders nützlich, wenn Bewegungen an Achsen gebunden sind oder eine Robustheit gegenüber Ausreißern in einzelnen Dimensionen gefordert ist.
$$d_{Manhattan}(x,y) = \sum_{i=1}^{d}|x_i - y_i|$$
### Cosine Similarity (Magnitude irrelevant)
Misst den Winkel zwischen zwei Vektoren, wobei deren absolute Länge (Magnitude) ignoriert wird. Das ist besonders nützlich, wenn die Korrelation der Features wichtiger ist als ihre absoluten Werte, wie beispielsweise bei der Textanalyse.
$$sim(x, y) = \frac{x \cdot y}{||x|| ||y||} = \frac{\sum_i x_i y_i}{\sqrt{\sum_i x_i^2} \sqrt{\sum_i y_i^2}}$$
### Mahalanobis Distanz
Generalisiert die euklidische Distanz durch Einbeziehung der [[Kovarianz]]struktur $\Sigma$ der Daten. Sie kompensiert unterschiedliche [[Varianz]]en und [[Korrelation]]en, indem sie den Raum so transformiert, dass Distanzen in Einheiten der [[Standardabweichung]] gemessen werden.
$$d_{Mahalanobis}(x, y) = \sqrt{(x-y)^T \Sigma^{-1} (x-y)}$$


---
#### Flashcards

Warum ist die Mahalanobis Distanz gegenüber der Euklidischen Distanz bei korrelierten Features vorzuziehen? :: Sie de-korreliert die Features durch die inverse Kovarianzmatrix $\Sigma^{-1}$ und skaliert sie anhand ihrer Varianz, sodass die Distanz unabhängig von unterschiedlichen Messeinheiten und Linearkombinationen wird.

Wann sollte die Cosine Similarity anstelle der Manhattan- oder Euklidischen Distanz angewendet werden?
?
Wenn die Magnitude (Länge) der Vektoren irrelevant ist und ausschließlich die Verteilung bzw. das Verhältnis der Features (die Richtung des Vektors) von Bedeutung ist (z. B. relative Worthäufigkeiten in unterschiedlich langen Textdokumenten).


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Distanzmetriken]]
SORT file.mtime DESC
```