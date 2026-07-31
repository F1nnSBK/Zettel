#Note

2026-06-24

Tags: [[Unsupervised Learning]], [[Reinforcement Learning]], [[MDP]], [[DQN]]
#UL

---

## Kapitel 11 – Reinforcement Learning

> *"Trial and Error – formalized."*

### The Why

Reinforcement Learning (RL) ist die dritte Lernparadigma neben Supervised und Unsupervised Learning. Statt Labels oder Datenmuster gibt es:
- Einen **Agent** der Aktionen ausführt
- Eine **Umwelt** die auf Aktionen reagiert
- Ein **Reward-Signal** das angibt wie gut eine Aktion war

**Schlüssel-Idee:** Nicht direkt lernen was zu tun ist (kein Label), sondern durch Ausprobieren herausfinden welche Aktionen langfristig maximalen Reward erzeugen.

**Anwendungen:** Spielen (AlphaGo, Atari), Robotik, Empfehlungssysteme, RLHF (Sprachmodelle), Ressourcenoptimierung.

**Lernziele:**
- MDP formal definieren und Bellman-Gleichung herleiten
- Q-Learning Algorithmus tracen
- Deep Q-Network (DQN) und seine Stabilisierungstricks erklären
- Policy Gradient (REINFORCE) von Value-Based-Methoden abgrenzen

---

### Theorie

#### Markov Decision Process (MDP)

Ein MDP wird durch das Tupel $(S, A, P, R, \gamma)$ definiert:

| Symbol | Bedeutung |
|---|---|
| $S$ | Zustandsraum |
| $A$ | Aktionsraum |
| $P(s'\|s,a)$ | Übergangswahrscheinlichkeit |
| $R(s,a,s')$ | Reward-Funktion |
| $\gamma \in [0,1)$ | Discount-Faktor |

**Markov-Eigenschaft:** $P(s_{t+1}|s_t, a_t) = P(s_{t+1}|s_0, a_0, \ldots, s_t, a_t)$ – nur der aktuelle Zustand zählt.

**Ziel:** Policy $\pi(a|s)$ finden die den erwarteten kumulierten Reward maximiert:
$$G_t = \sum_{k=0}^{\infty} \gamma^k R_{t+k+1}$$

---

#### Value Functions

**State-Value Function:**
$$V^\pi(s) = \mathbb{E}_\pi[G_t | s_t = s] = \mathbb{E}_\pi\left[R_{t+1} + \gamma V^\pi(s_{t+1}) | s_t = s\right]$$

**Action-Value Function (Q-Function):**
$$Q^\pi(s,a) = \mathbb{E}_\pi[G_t | s_t = s, a_t = a]$$

**Bellman Optimality Equation:**
$$Q^*(s,a) = \mathbb{E}\left[R_{t+1} + \gamma \max_{a'} Q^*(s_{t+1}, a') | s_t=s, a_t=a\right]$$

---

#### Q-Learning (Tabular)

```
Initialisiere Q(s,a) = 0 für alle s,a
Für jede Episode:
  s ← Startzustand
  Solange nicht terminal:
    a ← ε-greedy: mit Prob ε zufällig, sonst argmax_a Q(s,a)
    Führe a aus, beobachte r, s'
    Q(s,a) ← Q(s,a) + α [r + γ max_a' Q(s',a') - Q(s,a)]
    s ← s'
```

**TD-Target:** $r + \gamma \max_{a'} Q(s', a')$
**TD-Error:** $\delta = r + \gamma \max_{a'} Q(s', a') - Q(s, a)$
**$\varepsilon$-Greedy Exploration:** Exploration (zufällig) vs. Exploitation (greedy) balancieren.

**Konvergenz:** Garantiert zum Optimum $Q^*$ wenn alle State-Action-Paare unendlich oft besucht, LR $\alpha$ korrekt annealiert.

---

#### Deep Q-Network (DQN)

**Problem bei tabularem Q-Learning:** $|S| \times |A|$ kann astronomisch groß sein (z.B. Pixel-Zustand im Atari-Spiel).

**Lösung:** Approximiere $Q(s,a) \approx Q_\theta(s,a)$ mit einem neuronalen Netz.

**Update:**
$$\theta \leftarrow \theta + \alpha \cdot \delta \cdot \nabla_\theta Q_\theta(s,a)$$

**Stabilitätsprobleme:** Korrelierte Erfahrungen, nicht-stationäres TD-Target → Training divergiert.

**DQN-Tricks:**

| Trick | Problem das er löst |
|---|---|
| **Experience Replay** | Korrelierte Erfahrungen aufbrechen: $D$ speichert Transitions, zufälliges Mini-Batch |
| **Target Network** | Nicht-stationäres TD-Target: separates $\theta^-$ das alle $C$ Schritte geupdated wird |
| **Reward Clipping** | Numerische Stabilität |
| **Frame Stacking** | Markov-Eigenschaft für pixel-basierte Zustände herstellen |

**Loss:**
$$\mathcal{L}(\theta) = \mathbb{E}_{(s,a,r,s') \sim D}\left[(r + \gamma \max_{a'} Q_{\theta^-}(s',a') - Q_\theta(s,a))^2\right]$$

---

#### Policy Gradient (REINFORCE)

Statt Value-Function direkt $\pi_\theta(a|s)$ parametrisieren:

$$\nabla_\theta J(\theta) = \mathbb{E}_\pi\left[G_t \cdot \nabla_\theta \log \pi_\theta(a_t|s_t)\right]$$

**Algorithmus:**
```
Für jede Episode:
  Führe ganze Episode mit π_θ durch: s0,a0,r1,...,sT
  Für jeden Zeitschritt t:
    G_t ← Σ γ^k r_{t+k+1}
    θ ← θ + α G_t ∇_θ log π_θ(a_t|s_t)
```

**Vorteil gegenüber Q-Learning:** Kontinuierliche Aktionsräume, stochastische Policies.
**Nachteil:** Hohe Varianz der Gradienten → langsame Konvergenz.

**PPO (Proximal Policy Optimization):** State-of-the-art Policy Gradient; begrenzt Policy-Updates um Stabilitätsprobleme zu vermeiden. Standard für RLHF.

---

### Übungen

#### Aufgabe 1
Gegeben: Q-Tabelle mit $Q(s_1, a_1) = 5$. Beobachte Transition $(s_1, a_1, r=2, s_2)$ mit $\max_{a'} Q(s_2, a') = 8$, $\gamma = 0.9$, $\alpha = 0.1$. Berechne neues $Q(s_1, a_1)$.

**Lösung:**
TD-Target $= r + \gamma \max_{a'} Q(s_2, a') = 2 + 0.9 \cdot 8 = 9.2$
TD-Error $= 9.2 - 5 = 4.2$
$Q(s_1, a_1) \leftarrow 5 + 0.1 \cdot 4.2 = 5.42$

#### Aufgabe 2
Warum braucht DQN ein separates Target Network?

**Lösung:**
Das TD-Target $r + \gamma \max_{a'} Q_\theta(s', a')$ hängt von $\theta$ ab, dem gleichen Parameter der geupdated wird. Das ist äquivalent dazu, ein sich bewegendes Ziel zu verfolgen – der Update verändert gleichzeitig Target und Prediction → instabiles Training, Divergenz. Das Target Network $Q_{\theta^-}$ wird nur alle $C$ Schritte mit $\theta$ synchronisiert → quasi-stationäres Target für stabile Gradient-Updates.

#### Aufgabe 3
Was ist der Unterschied zwischen On-Policy und Off-Policy Lernen?

**Lösung:**
- **On-Policy (z.B. SARSA, PPO):** Lernt die Werte der Policy die aktuell ausgeführt wird. Muss Daten mit der aktuellen Policy sammeln.
- **Off-Policy (z.B. Q-Learning, DQN):** Lernt optimale Policy unabhängig von der Exploration-Policy. Experience Replay möglich (alte Daten nutzbar).

---

#### Flashcards

Was ist ein MDP und aus welchen Komponenten besteht es?
?
Markov Decision Process: $(S, A, P, R, \gamma)$
- $S$: Zustandsraum
- $A$: Aktionsraum
- $P(s'|s,a)$: Übergangswahrscheinlichkeit
- $R(s,a,s')$: Reward-Funktion
- $\gamma$: Discount-Faktor

Wie lautet das Q-Learning Update?
?
$$Q(s,a) \leftarrow Q(s,a) + \alpha \underbrace{[r + \gamma \max_{a'} Q(s',a') - Q(s,a)]}_{\text{TD-Error}}$$
TD-Target: $r + \gamma \max_{a'} Q(s', a')$

Was sind die zwei Stabilitätstricks von DQN?::**Experience Replay:** Zufälliges Mini-Batch aus Replay-Buffer $D$ statt korrelierter sequentieller Erfahrungen. **Target Network:** Separates $Q_{\theta^-}$ mit seltenen Updates → quasi-stationäres TD-Target.

Was ist $\varepsilon$-greedy Exploration?::Mit Wahrscheinlichkeit $\varepsilon$ wähle zufällige Aktion (Exploration), mit Wahrscheinlichkeit $1-\varepsilon$ wähle greedy $\arg\max_a Q(s,a)$ (Exploitation). $\varepsilon$ wird typisch über die Zeit annealiert (von ~1.0 auf ~0.05).

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[11 Reinforcement Learning]]
SORT file.mtime DESC
```
