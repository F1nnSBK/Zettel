#Note

2026-06-24

Tags: [[Unsupervised Learning]], [[Self-Supervised Learning]], [[Contrastive Learning]], [[BERT]]
#UL

---

## Kapitel 9 – Self-Supervised Learning

> *"You shall know a word by the company it keeps."*

### The Why

Gelabelte Daten sind teuer. Self-Supervised Learning erzeugt **Pretext-Aufgaben** aus den Daten selbst – automatisch generierte "Labels" ohne menschliche Annotation. Das Ziel: universell nützliche Repräsentationen die an viele Downstream-Tasks angepasst werden können.

**Schlüsselidee:** Die Struktur der Daten selbst liefert das Supervisionssignal.

**Lernziele:**
- Pretext Tasks vs. Downstream Tasks unterscheiden
- Kontrastives Lernen (SimCLR, InfoNCE) formal herleiten
- BERT und masked language modeling erklären
- JEPA und predictive SSL Frameworks verstehen

---

### Theorie

#### Pretext Tasks (generative Ansätze)

| Pretext Task | Eingabe | Ziel |
|---|---|---|
| **Rotation Prediction** | Rotiertes Bild | Rotationswinkel vorhersagen |
| **Jigsaw Puzzles** | Umgeordnete Patches | Originale Reihenfolge vorhersagen |
| **Colorization** | Graustufen-Bild | Farben vorhersagen |
| **Masked Autoencoding (MAE)** | 75% maskierte Patches | Fehlende Pixel rekonstruieren |
| **Masked Language Modeling** | 15% maskierte Tokens | Fehlende Wörter vorhersagen |

**Problem:** Pretext Tasks können zu oberflächlichen Repräsentationen führen wenn der Pretext Task zu einfach ist.

---

#### Kontrastives Lernen

**Kernannahme:** Zwei Augmentierungen desselben Datenpunkts sollen ähnliche Repräsentationen erhalten; Repräsentationen verschiedener Datenpunkte sollen unähnlich sein.

**Augmentierungen (Bilder):** Zuschneiden, Farb-Jitter, Graustufen, Gaußsches Rauschen, Horizontales Spiegeln.

##### SimCLR

1. Erzeuge zwei Augmentierungen $\tilde{x}_i, \tilde{x}_i'$ für jedes $x_i$
2. Kodiere beide: $h_i = f(\tilde{x}_i)$, $h_i' = f(\tilde{x}_i')$
3. Projiziere: $z_i = g(h_i)$ (Projektionskopf, wird nach Training verworfen)
4. Minimiere NT-Xent Loss:

$$\mathcal{L} = -\log \frac{\exp(\text{sim}(z_i, z_i')/\tau)}{\sum_{k \neq i} \exp(\text{sim}(z_i, z_k)/\tau)}$$

**Wichtig:** Großes Batch (4096–8192) und starke Augmentierungen für gute Performance.

##### InfoNCE Loss (verallgemeinert)

$$\mathcal{L}_{\text{InfoNCE}} = -\mathbb{E}\left[\log \frac{\exp(f(x)^T f(x^+)/\tau)}{\exp(f(x)^T f(x^+)/\tau) + \sum_{j=1}^K \exp(f(x)^T f(x_j^-)/\tau)}\right]$$

Maximiert mutual information zwischen positiven Paaren.

---

#### BERT – Masked Language Modeling

**Trainingsziel:** 15% der Tokens werden maskiert, Modell muss fehlende Tokens vorhersagen.

**Aufbau:**
- 80% der Zeit: Token durch `[MASK]` ersetzen
- 10%: Token durch zufälliges anderes Token ersetzen
- 10%: Token unverändert lassen (Modell soll es trotzdem "prüfen")

**Resultierende Repräsentationen:** Bidirektionaler Kontext → besser für Verständnis als GPT (unidirektional, aber besser für Generierung).

---

#### JEPA (Joint Embedding Predictive Architecture)

**Idee (LeCun et al.):** Nicht Pixel rekonstruieren, sondern Repräsentationen vorhersagen.

$$\mathcal{L} = \|f(x_{\text{target}}) - g(f(x_{\text{context}}), M)\|^2$$

- $f$: Encoder
- $g$: Predictor (nimmt Kontext + Positionen der fehlenden Regions)
- $M$: Positionen der Target-Regions

**Vorteil:** Keine Rekonstruktion von irrelevanten Details (z.B. Textur, Rauschen) → abstraktere, semantisch reichhaltigere Features. Verhindert Collapse durch Predictor-Architektur (kein negativer Loss-Term nötig).

---

### Übungen

#### Aufgabe 1
Warum braucht SimCLR einen großen Batch?

**Lösung:**
Der NT-Xent Loss kontrastiert jeden Anker gegen **alle anderen** Beispiele im Batch als Negative. Mehr Negative → informativere Gradienten → bessere Repräsentationen. Kleiner Batch → nur wenige leichte Negative → Modell lernt kaum Unterscheidung.

#### Aufgabe 2
Was ist der Unterschied zwischen BERT und GPT beim Pre-Training?

**Lösung:**
**BERT:** Bidirektional, masked language modeling (15% Token-Maskierung). Sieht linken und rechten Kontext gleichzeitig → gut für Verstehens-Tasks (Classification, NER, QA).
**GPT:** Unidirektional (links→rechts), nächstes Token vorhersagen. Kein Zugriff auf rechten Kontext → gut für Generierungsaufgaben.

#### Aufgabe 3
Was ist der Nachteil von Pixel-Rekonstruktion als Pretext-Task?

**Lösung:**
Die meisten Pixel in natürlichen Bildern tragen wenig semantische Information (Hintergründe, Texturen, Rauschen). Ein Modell das Pixel rekonstruiert, verschwendet Kapazität auf irrelevante Details. JEPA adressiert das indem es Repräsentationen vorhersagt, nicht Rohpixel.

---

#### Flashcards

Was ist ein Pretext Task?::Eine selbst-überwachte Aufgabe die automatisch aus den Daten generiert wird (ohne menschliche Labels). Das Supervisionssignal entsteht aus der Datenstruktur selbst (z.B. welches Patch gehört wohin, welches Wort ist maskiert).

Erkläre den NT-Xent Loss von SimCLR.
?
Für jede positive Paare $(z_i, z_i')$ wird der Nenner durch alle anderen $2(N-1)$ Paare im Batch gebildet:
$$\mathcal{L} = -\log \frac{\exp(\text{sim}(z_i, z_i')/\tau)}{\sum_{k \neq i} \exp(\text{sim}(z_i, z_k)/\tau)}$$
Ziel: Positive Paare näher zusammenbringen (Zähler ↑), Negative auseinandertreiben (Nenner ↑).

Was ist der Vorteil von JEPA gegenüber Masked Autoencoders (MAE)?::JEPA sagt abstrakte Repräsentationen vorher, nicht Rohpixel. Das verhindert dass das Modell Kapazität auf irrelevante Details (Textur, Rauschen) verschwendet, und fördert semantisch reichhaltigere Repräsentationen.

Was ist Representation Collapse und wie wird es verhindert?::Collapse: Alle Inputs werden auf denselben Embedding-Punkt abgebildet → Loss = 0, keine Information. Verhindert durch: Negative Paare (SimCLR), Stop-Gradient + Momentum Encoder (MoCo, BYOL), oder Predictor-Architektur (JEPA).

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[09 Self-Supervised Learning]]
SORT file.mtime DESC
```
