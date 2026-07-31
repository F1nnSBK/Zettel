#Note

2026-06-24

Tags: [[Unsupervised Learning]], [[Weak Supervision]], [[Snorkel]], [[Label Functions]]
#UL

---

## Kapitel 10 – Weak Supervision

> *"Trusting the Crowd."*

### The Why

Für viele Anwendungen gilt: Unlabeled Data ist billig (Logs, Sensor-Streams, Web), Labeled Data ist teuer (medizinische Experten, Juristen, Annotation). Weak Supervision nutzt **programmatische, laute Quellen** statt einzelner Ground-Truth-Labels.

**Beispiele schwacher Quellen:**
- Heuristische Regeln (*"if 'excellent' in text → positive"*)
- Knowledge Bases
- Crowdsourcing (Amazon Mechanical Turk)
- Distantly supervised labels (Wikipedia-Entitäten)
- Andere (schwächere) Modelle

**Lernziele:**
- Label Functions (LFs) entwerfen und evaluieren
- Label-Modell (Snorkel, Dawid-Skene) erklären
- Grenzen und Annahmen von Weak Supervision verstehen

---

### Theorie

#### Label Functions

Eine **Label Function** $\lambda_i: X \to \{-1, 0, 1, \ldots\}$ weist jedem Datenpunkt ein Label oder Abstention zu:
- $+1$: positiv
- $-1$: negativ
- $0$: abstain (keine Aussage)

**Eigenschaften einer guten LF:**
- Hohe Coverage (nicht zu viele Abstentions)
- Gute Accuracy (nicht zu viele Fehler)
- Disagreement mit anderen LFs (Diversität)

**LF-Metriken:**
- **Coverage:** Anteil Datenpunkte mit $\lambda_i \neq 0$
- **Empirical Accuracy:** $P(\lambda_i(x) = y)$ auf gelabelten Test-Daten

---

#### Das Label-Modell

**Problem:** $m$ Label Functions geben $m$ (laute, korrelierte) Labels pro Datenpunkt. Wie kombiniert man sie?

**Naïv:** Majority Vote → ignoriert unterschiedliche Qualität, Korrelationen.

**Label-Modell (Snorkel):** Lerne Accuracy und Korrelationen der LFs unüberwacht aus ihren Mustern.

$$P(\Lambda, Y) = \prod_{i=1}^m P(\lambda_i | Y) \cdot P(Y)$$

Annahme: LFs konditionell unabhängig gegeben $Y$.

**Training:** Maximiere Likelihood auf den beobachteten LF-Outputs ohne Ground Truth.

**Output:** Probabilistische Labels $\tilde{p}(y_i = 1)$ für jeden Datenpunkt → End-Modell trainieren.

---

#### Dawid-Skene Modell

**Für Crowdsourcing:** Jeder Worker $w$ hat eine **Confusion Matrix** $\pi_w$:
$$\pi_w^{jk} = P(\text{Worker w sagt } k \mid \text{True Label } j)$$

**EM-Algorithmus:**
- **E-Step:** Schätze True Labels gegeben Worker-Antworten und Confusion Matrices
- **M-Step:** Aktualisiere Confusion Matrices gegeben geschätzte True Labels

→ Konvergiert zu Maximum-Likelihood-Lösung.

---

#### Generative vs. Diskriminative Supervision

| | Generatives Label-Modell | End-Modell |
|---|---|---|
| **Training auf** | LF-Outputs (unlabeled) | Probabilistic Labels |
| **Zweck** | Kombination der LFs | Eigentliche Vorhersage |
| **Features** | Nur LF-Votes | Alle Input-Features |

---

### Übungen

#### Aufgabe 1
Entwirf 3 Label Functions für Sentiment-Analyse von Produktrezensionen.

**Lösung:**
```python
def lf_positive_words(x):
    if any(w in x.text for w in ["excellent", "amazing", "perfect"]):
        return POSITIVE
    return ABSTAIN

def lf_negative_words(x):
    if any(w in x.text for w in ["terrible", "broken", "awful", "waste"]):
        return NEGATIVE
    return ABSTAIN

def lf_star_rating(x):
    if x.stars >= 4:
        return POSITIVE
    elif x.stars <= 2:
        return NEGATIVE
    return ABSTAIN
```

#### Aufgabe 2
Warum ist Majority Vote bei Label Functions oft schlechter als ein Label-Modell?

**Lösung:**
Majority Vote behandelt alle LFs als gleich gut (gleiche Accuracy) und als unabhängig. In der Praxis:
1. **Unterschiedliche Qualität:** Manche LFs haben 60% Accuracy, andere 90%. Majority Vote ignoriert das.
2. **Korrelationen:** Zwei LFs die auf denselben Wörtern basieren stimmen systematisch überein – Majority Vote überschätzt deren kombinierten Beweis. Das Label-Modell lernt diese Struktur explizit.

---

#### Flashcards

Was ist eine Label Function?::Eine Heuristik oder Regel $\lambda: X \to \{-1, 0, +1, \ldots\}$ die Datenpunkten schwache Labels zuweist. $0$ = Abstention (keine Aussage). LFs können Regeln, externe DBs, andere Modelle sein.

Was ist der Vorteil des Label-Modells (Snorkel) gegenüber Majority Vote?
?
Das Label-Modell lernt die **Accuracy** und **Korrelationen** der LFs unüberwacht aus ihren Übereinstimmungsmustern. Damit werden:
- Bessere LFs stärker gewichtet
- Korrelierte LFs nicht doppelt gezählt
Majority Vote behandelt alle LFs als gleich gut und unabhängig.

Was ist die Hauptannahme des Label-Modells?::Konditionelle Unabhängigkeit der LFs gegeben dem True Label: $P(\Lambda|Y) = \prod_i P(\lambda_i|Y)$. Verletzt wenn LFs auf denselben Features basieren.

Was ist das Dawid-Skene Modell?::Ein probabilistisches Modell für Crowdsourcing. Jeder Worker hat eine Confusion Matrix die beschreibt wie oft er jede Klasse als andere klassifiziert. EM-Algorithmus schätzt True Labels und Confusion Matrices gleichzeitig ohne Gold-Standard.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[10 Weak Supervision]]
SORT file.mtime DESC
```
