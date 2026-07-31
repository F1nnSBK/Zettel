#Note

2026-06-24

Tags: [[Unsupervised Learning]], [[VAE]], [[Variational Inference]], [[Deep Learning]]
#UL

---

## Kapitel 6 – Variational Inference & VAE

> *"Embeddings and latent feature spaces."*

### The Why

PCA ist linear und kann Strukturen auf gekrümmten Mannigfaltigkeiten nicht erfassen. **Autoencoders** schließen diese Lücke mit nichtlinearen Encoder-Decoder-Architekturen. Das Problem: Der latente Raum hat keine Struktur → gaps, unvollständig, nicht generierbar.

**VAEs** fügen eine probabilistische Formulierung hinzu: Der latente Raum wird zu einer glatten, vollständigen Verteilung (Prior + Reparametrisation).

**Lernziele:**
- Autoencoder-Architektur und Training
- Warum Rekonstruktion allein keinen strukturierten latenten Raum erzeugt
- ELBO als Trainingsziel (Rekonstruktion + KL-Regularisierung)
- Reparametrisierungstrick

---

### Theorie

#### Autoencoder

**Architektur:**
$$x \xrightarrow{\theta_E} z \xrightarrow{\theta_D} \hat{x}$$

- **Encoder** $\theta_E: \mathbb{R}^d \to \mathbb{R}^k$ mit $k \ll d$
- **Decoder** $\theta_D: \mathbb{R}^k \to \mathbb{R}^d$
- **Rekonstruktionsverlust:** $\mathcal{L} = \|x - \hat{x}\|^2 = \|x - \theta_D(\theta_E(x))\|^2$

**Bottleneck:** Weil $k \ll d$ kann der Encoder nicht kopieren → lernt kompakte Repräsentation.

**Training:** Standard Backpropagation durch beide Netzwerke.

**Verbindung zu PCA:** Linearer Autoencoder (keine Aktivierungsfunktionen) + MSE = PCA-Unterraum. Nichtlineare Aktivierungen erlauben gekrümmte Mannigfaltigkeiten.

---

#### Von Autoencoder zu VAE

**Problem:** Der latente Raum hat Lücken – Interpolation zwischen zwei Punkten kann unplausible Ausgaben erzeugen, weil nicht jede Region des Raums einem Trainingsbeispiel entspricht.

**Lösung:** Encoder gibt keine Punkte aus, sondern **Verteilungen**: $q_\phi(z|x) = \mathcal{N}(\mu(x), \sigma^2(x))$

**Prior:** $p(z) = \mathcal{N}(0, I)$

---

#### ELBO (Evidence Lower Bound)

Das VAE-Trainingsziel maximiert den ELBO:

$$\text{ELBO} = \underbrace{\mathbb{E}_{q_\phi(z|x)}[\log p_\theta(x|z)]}_{\text{Rekonstruktion}} - \underbrace{D_{\text{KL}}(q_\phi(z|x) \| p(z))}_{\text{Regularisierung}}$$

- **Rekonstruktionsterm:** Wie gut wird $x$ rekonstruiert?
- **KL-Divergenz-Term:** Wie nah ist der posterior an unserem prior $\mathcal{N}(0,I)$?

Für Gauß-Verteilungen:
$$D_{\text{KL}}(\mathcal{N}(\mu, \sigma^2) \| \mathcal{N}(0,I)) = \frac{1}{2}\sum_j \bigl(\mu_j^2 + \sigma_j^2 - \log\sigma_j^2 - 1\bigr)$$

---

#### Reparametrisierungstrick

**Problem:** Man kann nicht durch eine Stichprobe $z \sim q_\phi(z|x)$ backpropagieren (stochastische Operation hat keinen Gradienten).

**Lösung:** Schreibe $z = \mu + \sigma \odot \varepsilon$ mit $\varepsilon \sim \mathcal{N}(0,I)$.

→ Der Gradient fließt durch $\mu$ und $\sigma$ (deterministische Funktionen von $x$), nicht durch $\varepsilon$.

---

#### VAE-Varianten

| Variante | Änderung |
|---|---|
| $\beta$-VAE | KL-Term mit $\beta > 1$ gewichtet → stärkere Disentanglement |
| VQ-VAE | Diskreter latenter Raum (Codebook) |
| Conditional VAE | Label $y$ als Bedingung an Encoder und Decoder |

---

### Übungen

#### Aufgabe 1
Erkläre den Reparametrisierungstrick in einem Satz.

**Lösung:**
Statt $z$ direkt zu sampeln, schreiben wir $z = \mu + \sigma \odot \varepsilon$ mit $\varepsilon \sim \mathcal{N}(0,I)$, sodass der Gradient durch die deterministischen Parameter $\mu, \sigma$ fließen kann.

#### Aufgabe 2
Was ist der Unterschied zwischen Autoencoder und VAE im latenten Raum?

**Lösung:**
**Autoencoder:** Deterministischer latenter Punkt $z = \theta_E(x)$. Kein Prior → unstrukturierter Raum mit Lücken. Kein Generieren aus beliebigen $z$ möglich.
**VAE:** Stochastischer latenter Raum $z \sim q_\phi(z|x) = \mathcal{N}(\mu, \sigma^2)$. KL-Term zwingt Verteilung nah an $\mathcal{N}(0,I)$ → glatter, vollständiger Raum. Neue Samples durch $z \sim \mathcal{N}(0,I)$ → Decoder.

#### Aufgabe 3
Was passiert wenn $\beta$ in einem $\beta$-VAE sehr groß gewählt wird?

**Lösung:**
Der KL-Term dominiert → starke Regularisierung → der latente Raum wird maximal nah am Prior. Das fördert Disentanglement (jede Dimension kontrolliert einen unabhängigen Faktor), aber verschlechtert die Rekonstruktionsqualität.

---

#### Flashcards

Was bedeutet ELBO?
?
Evidence Lower Bound. Das VAE-Trainingsziel: $\text{ELBO} = \mathbb{E}[\log p_\theta(x|z)] - D_{KL}(q_\phi(z|x) \| p(z))$. Rekonstruktionsterm - KL-Regularisierung. Maximierung des ELBO entspricht der Maximierung der Log-Likelihood mit Regularisierung.

Was ist der Reparametrisierungstrick und warum braucht man ihn?::Man schreibt $z = \mu + \sigma \odot \varepsilon, \varepsilon \sim \mathcal{N}(0,I)$. Der Sampling-Schritt wird aus dem Berechnungsgraphen herausgezogen, sodass Gradienten durch $\mu$ und $\sigma$ fließen können.

Was erzwingt der KL-Term im VAE-Loss?::Der KL-Term zwingt den posterior $q_\phi(z|x)$ nah an den Prior $p(z) = \mathcal{N}(0,I)$. Das erzeugt einen glatten, vollständig belegten latenten Raum ohne Lücken, aus dem man generieren kann.

Warum ist ein linearer Autoencoder äquivalent zu PCA?::Beide maximieren die erklärte Varianz in einem $k$-dimensionalen Unterraum. Mit linearen Encoder/Decoder und MSE-Verlust lernt der Autoencoder exakt den gleichen Unterraum wie PCA. Nichtlineare Aktivierungen brechen diese Äquivalenz.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[06 Variational Inference]]
SORT file.mtime DESC
```
