#Note

2026-06-24

Tags: [[Unsupervised Learning]], [[Transfer Learning]], [[Foundation Models]], [[CLIP]]
#UL

---

## Kapitel 8 – Transfer Learning & Foundation Models

> *"Standing on the Shoulders of Giants."*

### The Why

Training von Scratch ist teuer: GPT-3 = $4.6M, Gemini = $191M. Zudem reichen Daten für spezialisierte Tasks oft nicht aus. **Transfer Learning** nutzt bereits gelerntes Wissen aus datenreichen Quelldomänen für datensparse Zieldomänen.

**Lernziele:**
- Inductive vs. Transductive Transfer verstehen
- Fine-Tuning vs. Frozen Backbone vs. Prompt-Engineering anwenden
- CLIP und kontrastives multimodales Training erklären
- Zero-Shot und Few-Shot Inference durchführen

---

### Theorie

#### Transfer Learning Definitionen

**Domäne** $\mathcal{D} = (\mathcal{X}, P(X))$: Feature-Raum + Marginalverteilung.
**Task** $\mathcal{T} = (\mathcal{Y}, f)$: Label-Raum + Vorhersagefunktion.

**Transfer Learning:** Nutze Wissen aus $(\mathcal{D}_S, \mathcal{T}_S)$ um $f_T$ auf $(\mathcal{D}_T, \mathcal{T}_T)$ zu verbessern, wobei $\mathcal{D}_S \neq \mathcal{D}_T$ oder $\mathcal{T}_S \neq \mathcal{T}_T$.

#### Transfer-Strategien

| Strategie | Wann | Methode |
|---|---|---|
| **Frozen Backbone** | Viel Quell-Daten, wenig Ziel-Daten, ähnliche Domain | Nur neuen Kopf trainieren |
| **Fine-Tuning** | Genug Ziel-Daten, Source ≠ Target Domain | Alle Layer mit kleiner LR trainieren |
| **Linear Probing** | Zuerst evaluieren ob Features gut passen | Nur lineare Schicht auf Embeddings |
| **Prompt Engineering** | Foundation Model + Zero/Few-Shot | Kein Training, nur Prompt designen |

#### Negative Transfer

Wenn $\mathcal{D}_S$ und $\mathcal{D}_T$ zu verschieden sind, kann Transfer die Performance **verschlechtern**. Symptome: Quelle-Training auf sehr anderen Daten (z.B. Medizin-Bilder → Comic-Stil).

---

#### Foundation Models

**Definition:** Modelle trainiert auf breiten, diversen Daten (Web-Scale) die durch Adaptation an viele Downstream-Tasks angepasst werden können.

**Beispiele:** GPT-4, CLIP, DALL-E, Gemini, Segment Anything (SAM).

**Emergenz:** Fähigkeiten die nicht explizit trainiert wurden entstehen ab einer kritischen Modellgröße (z.B. Chain-of-Thought, Arithmetic).

---

#### CLIP (Contrastive Language-Image Pre-Training)

**Idee:** Bild- und Text-Encoder gemeinsam trainieren, sodass zusammengehörende Bild-Text-Paare im Embedding-Raum nah beieinander liegen.

**Training:** Kontrastiver Verlust auf $N \times N$ Bild-Text-Paaren:
- Positive Paare: $(I_i, T_i)$ diagonal
- Negative Paare: alle anderen Kombinationen

$$\mathcal{L} = -\frac{1}{N} \sum_{i=1}^N \log \frac{\exp(\text{sim}(I_i, T_i)/\tau)}{\sum_{j=1}^N \exp(\text{sim}(I_i, T_j)/\tau)}$$

**Zero-Shot Klassifikation:** Ohne jedes Task-spezifisches Training:
1. Formuliere Klassen als Text: *"a photo of a cat"*
2. Berechne Cosinus-Ähnlichkeit zwischen Bild-Embedding und Text-Embeddings
3. Nimm Klasse mit höchster Ähnlichkeit

---

#### Zero-Shot vs. Few-Shot vs. Fine-Tuning

| | Trainingsdaten nötig | Anpassungsaufwand |
|---|---|---|
| **Zero-Shot** | Keine | Prompt designen |
| **Few-Shot** | 1–50 Beispiele | In-Context Learning |
| **Fine-Tuning** | Viele Task-Beispiele | Gradient-Updates |

---

### Übungen

#### Aufgabe 1
Du hast ein medizinisches Bildklassifikations-Problem (500 Trainingsbilder, 10 Klassen). Welche Transfer-Strategie wählst du und warum?

**Lösung:**
Frozen ImageNet-Backbone + neuer Klassifikationskopf. Warum: 500 Bilder reichen nicht für Fine-Tuning des ganzen Netzwerks (Overfitting). ImageNet-Features (Kanten, Texturen, Strukturen) sind auch für medizinische Bilder nützlich. Falls Performance noch nicht ausreichend: schrittweises Fine-Tuning nur der letzten Blöcke.

#### Aufgabe 2
Erkläre wie CLIP Zero-Shot Klassifikation ohne gelabelte Zieldaten ermöglicht.

**Lösung:**
CLIP lernt einen gemeinsamen Embedding-Raum für Bilder und Texte. Klassen-Labels werden als natürlichsprachige Prompts formuliert (*"a photo of a [class]"*) und durch den Text-Encoder in Embeddings umgewandelt. Das Bild-Embedding wird mit allen Klassen-Embeddings verglichen (Cosinus-Ähnlichkeit). Die Klasse mit dem nächsten Text-Embedding ist die Vorhersage – ohne ein einziges gelabeltes Beispiel der Zielklasse.

---

#### Flashcards

Was ist der Unterschied zwischen Fine-Tuning und Frozen Backbone?::**Frozen Backbone:** Nur der neue Aufgabenkopf wird trainiert, alle vortrainierten Layer bleiben eingefroren. **Fine-Tuning:** Alle (oder zumindest die hinteren) Layer werden mit kleiner Lernrate gemeinsam trainiert. Frozen: besser bei wenig Zieldaten. Fine-Tuning: besser bei ausreichend Zieldaten, andere Domain.

Wie funktioniert CLIP Zero-Shot Klassifikation?
?
1. Formuliere jede Klasse als Text-Prompt: *"a photo of a {class}"*
2. Kodiere Bild und alle Text-Prompts mit den jeweiligen Encodern
3. Berechne Cosinus-Ähnlichkeit zwischen Bild-Embedding und allen Text-Embeddings
4. Klasse mit höchster Ähnlichkeit = Vorhersage

Was ist Negative Transfer?::Wenn Transfer Learning die Zielaufgaben-Performance schlechter macht als Training von Scratch. Tritt auf wenn Quell- und Zieldomäne zu verschieden sind (entgegengesetzte Bias-Strukturen, grundlegend andere visuelle Merkmale).

Was sind Emergent Capabilities?::Fähigkeiten die in Foundation Models entstehen ohne explizit trainiert zu werden (z.B. Arithmetic, Code-Generierung in Sprachmodellen). Treten ab kritischer Modellgröße auf. Nicht vollständig verstanden.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[08 Transfer Learning]]
SORT file.mtime DESC
```
