#Note

2026-06-24

Tags: [[Unsupervised Learning]], [[Uncertainty Estimation]], [[MC Dropout]], [[OOD Detection]]
#UL

---

## Kapitel 7 – Uncertainty Estimation

> *"I know that I know nothing."*

### The Why

Neuronale Netze machen Vorhersagen mit hoher Konfidenz – auch auf unbekannten Eingaben. Softmax normalisiert auf 1, unabhängig davon ob die Eingabe im Trainingsbereich liegt. **Uncertainty Estimation** macht dieses Problem quantifizierbar.

**Anwendungen:**
- Autonomes Fahren: Out-of-Distribution (OOD) Input erkennen
- Medizin: Unsichere Diagnosen an Experten weiterleiten
- Anomaly Detection: Ungewöhnliche Inputs flaggen
- Drift Detection: Verteilungsverschiebung im Deployment

**Lernziele:**
- Aleatoric vs. Epistemic Uncertainty unterscheiden
- MC Dropout und Deep Ensembles anwenden
- Graceful Degradation-Strategien entwerfen

---

### Theorie

#### Zwei Arten von Unsicherheit

| | Aleatoric | Epistemic |
|---|---|---|
| **Quelle** | Inhärentes Rauschen in den Daten | Modell-Unwissenheit (fehlende Daten) |
| **Reduzierbar?** | **Nein** | **Ja** (mehr Daten helfen) |
| **Beispiel** | Sensor-Rauschen, überlappende Klassen | Seltene Ereignisse, neue Domänen |
| **Reaktion** | Ambiguität kommunizieren | Mehr Daten sammeln |

**Aleatoric Ceiling:** Selbst ein perfektes Modell mit unendlich Daten kann aleatoric uncertainty nicht eliminieren.

---

#### Monte Carlo Dropout (MC Dropout)

**Idee:** Dropout während der Inferenz aktiviert lassen → jeder Forward Pass benutzt ein anderes Sub-Netzwerk → Ensemble von $T$ Vorhersagen.

**Algorithmus:**
```
Gegeben: Input x, Netzwerk f_θ mit Dropout, Anzahl Passes T
Für t = 1 bis T:
  ŷ_t = f_θ(x)  // Forward Pass mit aktiviertem Dropout
ȳ = (1/T) Σ ŷ_t         // Mittlere Vorhersage
Var(ŷ) = (1/T) Σ (ŷ_t - ȳ)²  // Prädiktive Varianz
```

**Interpretation:**
- Kleine Varianz → Modell ist sicher (In-Distribution)
- Große Varianz → Modell ist unsicher (OOD-Indikator)

**Theoretische Grundlage (Gal & Ghahramani 2016):** MC Dropout approximiert variationelle Inferenz in einem Bayesianischen Neuronalen Netz.

---

#### Deep Ensembles

**Idee:** $M$ unabhängige Modelle trainieren, Vorhersagen aggregieren:

$$p(y|x) = \frac{1}{M} \sum_{m=1}^{M} p_m(y|x)$$

**Disagreement** zwischen Ensemble-Mitgliedern = Maß für epistemic uncertainty.

| | MC Dropout | Deep Ensembles |
|---|---|---|
| Trainingskosten | 1× | $M$× |
| Inferenzkosten | $T$ Forward Passes | $M$ Forward Passes |
| Diversität | Durch Masken (gleiche Weights) | Durch unabhängige Initialisierung |
| Kalibrierung | Gut | Besser |

---

#### Calibration

Ein Modell ist **kalibriert** wenn die ausgegebene Konfidenz mit der empirischen Genauigkeit übereinstimmt:
- 90% Konfidenz → 90% Richtig-Rate

**Reliability-Diagrams** visualisieren Kalibrierung; **Temperature Scaling** ist eine einfache Post-hoc-Korrektur:
$$p_T(y|x) = \text{softmax}(z / T)$$

---

#### Graceful Degradation

**Routing-Strategien:**
1. **Abstain:** Wenn Unsicherheit > Schwelle → keine Vorhersage, an Menschen weiterleiten
2. **Fallback:** Sicherere (aber weniger genaue) Fallback-Strategie
3. **Human-in-the-Loop:** Unsichere Fälle für menschliche Annotation flaggen
4. **Drift Monitor:** Verteilung der Unsicherheiten über Zeit überwachen

---

### Übungen

#### Aufgabe 1
Ein Modell hat auf einem OOD-Input via MC Dropout folgende 5 Vorhersagen: $[0.9, 0.4, 0.7, 0.5, 0.8]$. Berechne Mittelwert und Varianz. Was bedeutet das?

**Lösung:**
$\bar{y} = (0.9+0.4+0.7+0.5+0.8)/5 = 0.66$
$\text{Var} = \frac{1}{5}[(0.9-0.66)^2 + (0.4-0.66)^2 + (0.7-0.66)^2 + (0.5-0.66)^2 + (0.8-0.66)^2]$
$= \frac{1}{5}[0.058 + 0.068 + 0.002 + 0.026 + 0.020] = 0.035$

Hohe Varianz (0.035 >> 0.001 für In-Distribution) → Modell ist unsicher → OOD-Indikator.

#### Aufgabe 2
Warum kann der Softmax-Output allein keine Uncertainty-Schätzung liefern?

**Lösung:**
Softmax normalisiert immer auf 1, unabhängig von der Eingabe. Ein Modell das nie diesen Input-Typ gesehen hat, gibt trotzdem eine zuversichtliche (aber zufällige) Wahrscheinlichkeitsverteilung aus. Die Konfidenz-Zahl trägt keine Information darüber, ob der Input im Trainingsbereich liegt.

---

#### Flashcards

Was ist der Unterschied zwischen aleatoric und epistemic Uncertainty?
?
- **Aleatoric:** Inhärentes Rauschen im Datengenerationsprozess. Nicht reduzierbar – auch mit unendlich Daten bleibt sie.
- **Epistemic:** Modell-Unwissenheit durch fehlende Trainingsdaten. Reduzierbar – mehr relevante Daten senken sie.

Wie funktioniert MC Dropout?::Dropout während der Inferenz aktiviert lassen, $T$ Forward Passes durchführen. Die Varianz der $T$ Vorhersagen ist ein Maß für epistemic Uncertainty.

Was ist der Vorteil von Deep Ensembles gegenüber MC Dropout?::Ensemble-Mitglieder sind unabhängig initialisiert und trainiert → echte Diversität der Repräsentationen. MC Dropout-Masken operieren auf demselben trainierten Netzwerk → weniger Diversität. Ensembles sind besser kalibriert, aber $M$× teurer im Training.

Was bedeutet Calibration bei einem Klassifikationsmodell?::Ein kalibriertes Modell ist genau so oft richtig, wie seine angegebene Konfidenz vermuten lässt. Bei 80% Konfidenz sollte es in 80% der Fälle richtig liegen. Visualisiert durch Reliability Diagrams.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[07 Uncertainty Estimation]]
SORT file.mtime DESC
```
