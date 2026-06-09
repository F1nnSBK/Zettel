#Note

2026-05-03

Tags: [[Autoencoder]], [[VAE]], [[Representation Learning]], [[Probabilistische Einbettung]], [[Unsupervised Learning]], [[Ebenen]], [[Dimensionsreduktion]]
#UL

---
Während die PCA eine lineare Projektion darstellt, erlauben **Autoencoder (AE)** das Lernen hochgradig nicht-linearer Repräsentationen durch neuronale Netze. Das Ziel ist die Kompression von Daten in einen niederdimensionalen **Latent Space** (Bottleneck), aus dem das Original möglichst originalgetreu rekonstruiert werden kann.

### Der Autoencoder (AE)

Ein AE besteht aus zwei gekoppelten Netzwerken:

1. **Encoder ($\theta_E$):** Komprimiert den Input $x \in \mathbb{R}^d$ in einen Code $z \in \mathbb{R}^k$ (wobei $k \ll d$).
2. **Decoder ($\theta_D$):** Versucht, den Code $z$ zurück in die ursprüngliche Form $\hat{x}$ zu transformieren.

**Zielfunktion:** Minimierung des quadratischen Rekonstruktionsfehlers:

$$\mathcal{L}_{AE} = ||x - \theta_D(\theta_E(x))||^2$$

Hinweis: Ein linearer Autoencoder ohne Aktivierungsfunktionen lernt denselben Unterraum wie eine PCA.

### Variational Autoencoder (VAE)

Ein Standard-AE lernt diskrete Punkte im Raum, was zu "Lücken" im latenten Raum führt. Der VAE löst dies, indem er den latenten Raum als kontinuierliche Wahrscheinlichkeitsverteilung modelliert.

- **Probabilistisches Mapping:** Der Encoder gibt keinen fixen Vektor $z$ aus, sondern Parameter einer Normalverteilung: Mittelwert $\mu$ und Standardabweichung $\sigma$.

- **Reparameterisierungstrick:** Um Backpropagation durch den stochastischen Sampling-Schritt zu ermöglichen, wird $z$ wie folgt berechnet:

$$z = \mu + \sigma \odot \epsilon \quad \text{mit} \quad \epsilon \sim \mathcal{N}(0, I)$$
    Dies verschiebt die Zufälligkeit in einen externen Knoten $\epsilon$, sodass die Gradienten durch $\mu$ und $\sigma$ fließen können.


### Die Loss-Funktion (ELBO)

Der VAE-Loss (Evidence Lower Bound) balanciert zwei Ziele:

$$\mathcal{L}_{VAE} = \underbrace{\mathbb{E}_{q(z|x)}[\log p(x|z)]}_{\text{Rekonstruktion}} - \underbrace{KL(q(z|x) || p(z))}_{\text{Regularisierung}}$$

1. **Reconstruction Loss:** Erzwingt Informationstreue (Datenqualität).

2. **KL-Divergenz:** Erzwingt, dass die gelernte Verteilung $q(z|x)$ dem Prior $p(z)$ (meist $\mathcal{N}(0, I)$) ähnelt. Dies verhindert, dass der Encoder Punkte isoliert "versteckt" und sorgt für einen glatten, kontinuierlichen Raum.


### Eigenschaften des latenten Raums

- **Interpolation:** Durch den kontinuierlichen Raum kann man zwischen zwei Punkten $z_a$ und $z_b$ wandern (Slerp/Lerp), wobei der Decoder einen glatten Übergang der Merkmale erzeugt.

- **Generierung:** Neue Daten können erzeugt werden, indem einfach ein Vektor $z$ aus der Normalverteilung gezogen und durch den Decoder geschickt wird.




---
#### Flashcards

Warum ist der Reparameterisierungstrick für das Training von VAEs essenziell? :: Er macht den Sampling-Prozess differenzierbar. Indem $z = \mu + \sigma \cdot \epsilon$ gesetzt wird, bleibt die Zufälligkeit ($\epsilon$) isoliert, während die Parameter $\mu$ und $\sigma$ für den Gradientenfluss der Backpropagation zugänglich bleiben.
<!--SR:!2026-06-09,1,230-->

Welche Aufgabe übernimmt die KL-Divergenz im ELBO-Loss eines VAE?
?
Sie wirkt als Regularisierer, der die Verteilung im latenten Raum gegen eine Standardnormalverteilung drückt. Dies verhindert Overfitting und sorgt dafür, dass der Raum "gefüllt" und glatt ist, was Sampling und Interpolation erst ermöglicht.
<!--SR:!2026-06-11,3,250-->

Was beschreibt das Phänomen des "Posterior Collapse" bei der Wahl von $\beta$ (in einem $\beta$-VAE)?
?
Wenn die Regularisierung (KL-Term) gegenüber der Rekonstruktion zu stark gewichtet wird ($\beta \gg 1$), ignoriert der Encoder den Input $x$ und kollabiert auf den Prior $p(z)$. Die latenten Dimensionen tragen dann keine Information mehr über die Daten.
<!--SR:!2026-06-09,1,230-->

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Probabilistic Embeddings]]
SORT file.mtime DESC
```