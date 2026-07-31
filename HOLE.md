
---

## Übersicht: Die HOLE-Architektur-Pipeline

Das folgende kompakte Diagramm visualisiert den Datenfluss vom rohen Narrow Angle Camera (NAC) Bildausschnitt bis hin zur Berechnung der kontrastiven und task-spezifischen Verluste.

### Strukturschema

```text
┌────────────────────────────────────────────────────────┐
│                       NAC Tile                         │
│                    (3 x 224 x 224)                     │
└───────────────────────────┬────────────────────────────┘
                            │
                            ▼
┌────────────────────────────────────────────────────────┐
│                   Patch Projection                     │
│                   (14 x 14 x 384)                      │
└───────────────────────────┬────────────────────────────┘
                            │
                            ▼
┌────────────────────────────────────────────────────────┐
│             DINOv3 ViT-S/16 + LoRA (r=32)              │
└───────────────────────────┬────────────────────────────┘
                            │
                            ▼
┌────────────────────────────────────────────────────────┐
│                  CLS Token Extraction                  │
│                         (384d)                         │
└───────┬───────────────┬───────────────┬───────────────┘
        │               │               │               │
        ▼               ▼               ▼               ▼
   [Path 1]        [Path 2]        [Path 3]        [Path 4]
   MLP 192         MLP 256         MLP 512         MLP 768
      │               │               │               │
      ▼               ▼               ▼               ▼
   MLP 96          MLP 128         MLP 256         MLP 384
      │               │               │               │
      ▼               ▼               ▼               ▼
    Head 1          Head 2          Head 3       Primary Head
    (64d)          (128d)          (256d)          (384d)
      │               │               │               │
      ├───────────────┼───────────────┼───────────────┤
      │               │               │               │
      ▼               ▼               ▼               ▼
┌──────────────────────────────────────────────┐┌──────────────┐
│         Heterogeneous NT-Xent Loss           ││ Hinge Triplet│
│             (Self-Supervised)                ││     Loss     │
└──────────────────────────────────────────────┘└──────────────┘
```

---

## 1. Input & Patch-Projektion

HOLE verarbeitet hochauflösende lunare Oberflächendaten (Narrow Angle Camera Tiles):

> [!abstract] Mathematische Darstellung des Inputs
> - **Eingangskachel:** $X \in \mathbb{R}^{C \times H \times W}$ mit $C=3$ Kanälen und einer Kachelgröße von $H = W = 224\text{ Pixel}$.
> - **Patch-Partitionierung:** Der Vision Transformer (ViT-S/16) unterteilt das Bild in nicht-überlappende Patches der Größe $P \times P = 16 \times 16\text{ Pixel}$.
> - **Patch-Grid-Dimension:**
>   $$N = \left(\frac{H}{P}\right) \times \left(\frac{W}{P}\right) = 14 \times 14 = 196\text{ Patches}$$
> - **Projektion:** Die Patches werden linear in den $D$-dimensionalen Einbettungsraum von ViT-S ($D = 384$) projiziert:
>   $$X_{\text{patch}} \in \mathbb{R}^{196 \times 384}$$

---

## 2. DINOv3 ViT-S/16 Backbone & LoRA-Anpassung

Zur effizienten Anpassung des gefrorenen Metas DINOv3-Modells an die lunare Domäne wird ein Low-Rank Adapter (LoRA) in die Selbstaufmerksamkeits-Schichten (Self-Attention) integriert.

> [!info] Parameter-Effiziente Feinabstimmung (PEFT)
> Für eine eingefrorene Gewichtsprojektion $W_0 \in \mathbb{R}^{D \times D}$ der Attention-Schichten (z. B. Query/Value-Projektionen) wird das inkrementelle Update durch zwei niedrigdimensionale Matrizen parametrisiert:
> $$W = W_0 + \Delta W = W_0 + \frac{\alpha}{r} (B \cdot A)$$
> Wobei:
> - **LoRA-Rang:** $r = 32$
> - **Down-Projektion:** $A \in \mathbb{R}^{r \times D}$ (initialisiert mit Kaiming-Normalverteilung)
> - **Up-Projektion:** $B \in \mathbb{R}^{D \times r}$ (initialisiert mit Nullen, sodass $\Delta W = 0$ zu Trainingsbeginn)
> - **Skalierungsfaktor:** $\alpha$ (konstanter Hyperparameter)
> 
> Dies ermöglicht die Repräsentationsänderung des Modells bei nur minimalem Speicher- und Rechen-Overhead während des rückwärtsgerichteten Gradientenflusses.

---

## 3. CLS-Token-Extraktion

Nach dem Durchlaufen der Transformer-Blöcke extrahiert HOLE den Class-Token (CLS), welcher die globale semantische Repräsentation der Kachel aggregiert.

> [!math] Mathematische Formulierung
> Sei $T \in \mathbb{R}^{197 \times 384}$ der ausgegebene Tensor des Encoders (196 Patch-Tokens + 1 CLS-Token):
> $$x_{\text{CLS}} = T_{0, \star} \in \mathbb{R}^{384}$$
> Dieser Vektor dient als komprimierte, kontinuierliche Eingabe für das nachgelagerte heterogene MLP-Ensemble.

---

## 4. Heterogenes MLP-Ensemble

Inspiriert von der DIVE-Methodik verwendet HOLE ein **heterogenes MLP-Ensemble**. Statt identischer Projektionsköpfe besitzt HOLE vier parallel geschaltete, asymmetrische Pfade mit unterschiedlichen Kapazitäten und Ausgangsdimensionen.

> [!settings] Ensemble-Spezifikationen
> Jeder Pfad $k \in \{1, 2, 3, 4\}$ verarbeitet $x_{\text{CLS}}$ unabhängig über zwei verdeckte Schichten (MLP1 $\rightarrow$ MLP2) hinweg und normalisiert die Ausgänge auf die Einheitskugel ($\mathbb{S}^{d_k - 1}$):
> 
> **Pfad 1 (Auxiliary Head 1):**
> - Dimensionen: $384 \rightarrow 192 \rightarrow 96 \rightarrow 64$
> - Ausgabekanal: $z^{(1)} \in \mathbb{S}^{63}$
> 
> **Pfad 2 (Auxiliary Head 2):**
> - Dimensionen: $384 \rightarrow 256 \rightarrow 128 \rightarrow 128$
> - Ausgabekanal: $z^{(2)} \in \mathbb{S}^{127}$
> 
> **Pfad 3 (Auxiliary Head 3):**
> - Dimensionen: $384 \rightarrow 512 \rightarrow 256 \rightarrow 256$
> - Ausgabekanal: $z^{(3)} \in \mathbb{S}^{255}$
> 
> **Pfad 4 (Primary Head - Ziel-Repräsentation):**
> - Dimensionen: $384 \rightarrow 768 \rightarrow 384 \rightarrow 384$
> - Ausgabekanal: $z^{(4)} \in \mathbb{S}^{383}$

---

## 5. Multi-Task Verlustfunktionen

Das Training von HOLE kombiniert die geomorphologische Constraint-Optimierung mit selbstüberwachter Regularisierung über zwei komplementäre Verlustfunktionen.

### A. Hinge Triplet Loss (Task-spezifisch)

Dieser Verlust wird **ausschließlich** auf den hochkapazitären **Primary Head ($z^{(4)}$)** angewendet, um die physikalischen Abstände von Kraterstrukturen im Vektorraum zu kalibrieren.

> [!math] Mathematische Formulierung
> Für ein Mini-Batch von Tripletts $\mathcal{B} = \{(q_i, p_i, n_i)\}_{i=1}^B$ (Query, positives Bild, negatives Bild) gilt:
> $$\mathcal{L}_{\text{triplet}} = \frac{1}{B} \sum_{i=1}^{B} \max\left(0, \; m - \Delta_i\right)$$
> Wobei der Ähnlichkeitsabstand $\Delta_i$ definiert ist als:
> $$\Delta_i = \left(z_{q, i}^{(4)} \cdot z_{p, i}^{(4)}\right) - \left(z_{q, i}^{(4)} \cdot z_{n, i}^{(4)}\right)$$
> Und $m > 0$ die geomorphologische Fehlertoleranz (Margin) beschreibt. Sobald $\Delta_i \ge m$, fällt der Gradientenfluss für dieses Triplett auf exakt Null ab (Selbstlimitierung).

### B. Heterogener NT-Xent Loss (Selbstüberwachtes Alignment)

Um ein Kollabieren der niedrigdimensionalen Köpfe zu verhindern und dichte Gradienten über alle Pfade hinweg zu erzeugen, wird ein modifizierter, dimensionsübergreifender NT-Xent-Verlust berechnet.

> [!math] Projektion in den Kontrastiv-Raum
> Da die vier Köpfe unterschiedliche Dimensionen aufweisen ($64, 128, 256, 384$), werden sie während des Trainings über lineare Hilfsprojektionen $W_c^{(k)} \in \mathbb{R}^{d_c \times d_k}$ in einen gemeinsamen, $d_c$-dimensionalen Kontrastiv-Raum ($d_c = 128$) überführt:
> $$\tilde{z}_i^{(k)} = \text{L2-Norm}\left(W_c^{(k)} z_i^{(k)}\right) \in \mathbb{S}^{d_c - 1}$$
> 
> Der Verlust zieht die unterschiedlichen Sichten (Heads) derselben lunaren Kachel im Kontrastiv-Raum zusammen und drückt Sichten unterschiedlicher Kacheln voneinander weg:
> $$\mathcal{L}_{\text{contrast}} = -\frac{1}{4 B} \sum_{i=1}^{B} \sum_{k=1}^{4} \log \frac{\sum_{j \neq k} \exp\left(\tilde{z}_i^{(k)} \cdot \tilde{z}_i^{(j)} / \tau\right)}{\sum_{l \neq i} \sum_{h=1}^{4} \exp\left(\tilde{z}_i^{(k)} \cdot \tilde{z}_l^{(h)} / \tau\right)}$$
> Wobei $\tau > 0$ der Temperaturparameter ist.

---

## 6. Trainings- und Inferenz-Asymmetrie

> [!success] Zero-Overhead bei der Inferenz
> Während des Trainings stabilisieren die drei Hilfsköpfe (Head 1 bis Head 3) die Repräsentation über dichte kontrastive Gradienten. 
> 
> Für die produktive Indizierung in der Monddatenbank werden die Hilfsköpfe komplett verworfen. Es wird **nur der Primary Head ($z^{(4)}$)** zur Generierung der $384$-dimensionalen Einbettung verwendet. Dies garantiert maximale geometrische Präzision ohne zusätzlichen Rechenaufwand im Orbit.

---

## 7. PyTorch-Implementierung

Hier ist die vollständige, modular aufgebaute PyTorch-Implementierung des HOLE-Modells:

```python
import torch
import torch.nn as nn
import torch.nn.functional as F
from typing import Dict, Tuple, Optional

class MLPBlock(nn.Module):
    """Standard MLP block with linear layer, batch normalization, and ReLU activation."""
    def __init__(self, in_dim: int, out_dim: int, use_bn: bool = True):
        super().__init__()
        self.linear = nn.Linear(in_dim, out_dim)
        self.bn = nn.BatchNorm1d(out_dim) if use_bn else nn.Identity()
        self.activation = nn.ReLU()

    def forward(self, x: torch.Tensor) -> torch.Tensor:
        return self.activation(self.bn(self.linear(x)))

class HeterogeneousEnsemble(nn.Module):
    """Ensemble of asymmetric MLP pathways producing multi-scale representations."""
    def __init__(self, input_dim: int = 384):
        super().__init__()
        # Path 1: 384 -> 192 -> 96 -> 64 (Auxiliary)
        self.path1 = nn.Sequential(
            MLPBlock(input_dim, 192),
            MLPBlock(192, 96),
            nn.Linear(96, 64)
        )
        
        # Path 2: 384 -> 256 -> 128 -> 128 (Auxiliary)
        self.path2 = nn.Sequential(
            MLPBlock(input_dim, 256),
            MLPBlock(256, 128),
            nn.Linear(128, 128)
        )
        
        # Path 3: 384 -> 512 -> 256 -> 256 (Auxiliary)
        self.path3 = nn.Sequential(
            MLPBlock(input_dim, 512),
            MLPBlock(512, 256),
            nn.Linear(256, 256)
        )
        
        # Path 4: 384 -> 768 -> 384 -> 384 (Primary)
        self.path4 = nn.Sequential(
            MLPBlock(input_dim, 768),
            MLPBlock(768, 384),
            nn.Linear(384, 384)
        )

    def forward(self, x: torch.Tensor) -> Tuple[torch.Tensor, torch.Tensor, torch.Tensor, torch.Tensor]:
        z1 = F.normalize(self.path1(x), p=2, dim=-1)
        z2 = F.normalize(self.path2(x), p=2, dim=-1)
        z3 = F.normalize(self.path3(x), p=2, dim=-1)
        z4 = F.normalize(self.path4(x), p=2, dim=-1)
        return z1, z2, z3, z4

class HOLE(nn.Module):
    """Hole Oriented Lunar Embedder.
    Integrates the DINOv3 backbone representation with the heterogeneous MLP head.
    """
    def __init__(self, d_cls: int = 384, contrastive_dim: int = 128):
        super().__init__()
        self.ensemble = HeterogeneousEnsemble(input_dim=d_cls)
        
        # Contrastive space projection layers (active only during training)
        self.proj1 = nn.Linear(64, contrastive_dim, bias=False)
        self.proj2 = nn.Linear(128, contrastive_dim, bias=False)
        self.proj3 = nn.Linear(256, contrastive_dim, bias=False)
        self.proj4 = nn.Linear(384, contrastive_dim, bias=False)

    def forward(self, x_cls: torch.Tensor, training: bool = False) -> Dict[str, torch.Tensor]:
        """Runs the CLS-tokens through the heterogeneous MLP pipeline."""
        z1, z2, z3, z4 = self.ensemble(x_cls)
        
        if not training:
            return {"primary_embedding": z4}
            
        # Align dimensionalities for NT-Xent computation
        tilde_z1 = F.normalize(self.proj1(z1), p=2, dim=-1)
        tilde_z2 = F.normalize(self.proj2(z2), p=2, dim=-1)
        tilde_z3 = F.normalize(self.proj3(z3), p=2, dim=-1)
        tilde_z4 = F.normalize(self.proj4(z4), p=2, dim=-1)
        
        return {
            "z1": z1, "z2": z2, "z3": z3, "z4": z4,
            "views": torch.stack([tilde_z1, tilde_z2, tilde_z3, tilde_z4], dim=1) # Shape: (B, 4, D_c)
        }

class HOLELoss(nn.Module):
    """Composite loss function executing Hinge Triplet Loss and Cross-Dimensional NT-Xent."""
    def __init__(self, margin: float = 0.5, temperature: float = 0.1, lambda_c: float = 0.2):
        super().__init__()
        self.margin = margin
        self.temperature = temperature
        self.lambda_c = lambda_c

    def _hinge_triplet_loss(self, q: torch.Tensor, p: torch.Tensor, n: torch.Tensor) -> torch.Tensor:
        sim_pos = torch.sum(q * p, dim=-1)
        sim_neg = torch.sum(q * n, dim=-1)
        return F.relu(self.margin - (sim_pos - sim_neg)).mean()

    def _nt_xent_loss(self, views: torch.Tensor) -> torch.Tensor:
        # views shape: (B, H, D) where H = 4
        B, H, D = views.shape
        flat_views = views.reshape(B * H, D)
        
        # Calculate cosine similarities
        similarity_matrix = torch.mm(flat_views, flat_views.t()) / self.temperature
        
        # Create masks to isolate positive pairs (different views of the same image)
        batch_indices = torch.arange(B, device=views.device).repeat_interleave(H)
        pos_mask = (batch_indices[:, None] == batch_indices[None, :])
        pos_mask.fill_diagonal_(False)
        
        # Exclude self-similarity from calculation
        similarity_matrix.fill_diagonal_(-1e9)
        
        log_softmax_sim = F.log_softmax(similarity_matrix, dim=1)
        loss = -(pos_mask * log_softmax_sim).sum(dim=1) / pos_mask.sum(dim=1).clamp(min=1)
        return loss.mean()

    def forward(self, q_out: Dict[str, torch.Tensor], 
                p_out: Dict[str, torch.Tensor], 
                n_out: Dict[str, torch.Tensor]) -> Tuple[torch.Tensor, torch.Tensor, torch.Tensor]:
        """Calculates combined loss. Inputs are dictionary outputs from HOLE forward pass with training=True."""
        # Task loss on primary head (z4)
        triplet_loss = self._hinge_triplet_loss(q_out["z4"], p_out["z4"], n_out["z4"])
        
        # Self-supervised view alignment on all heads
        contrast_loss = (
            self._nt_xent_loss(q_out["views"]) +
            self._nt_xent_loss(p_out["views"]) +
            self._nt_xent_loss(n_out["views"])
        ) / 3.0
        
        total_loss = triplet_loss + self.lambda_c * contrast_loss
        return total_loss, triplet_loss, contrast_loss
```
