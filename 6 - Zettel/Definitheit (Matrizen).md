#Note

2025-05-18

Tags: [[Definitheit (Matrizen)]], [[Matrizen]], [[Lineare Algebra]], [[Eigenwerte]], [[Symmetrische Matrix]], [[Optimierung]], [[Cholesky-Zerlegung]]

---

Die **Definitheit** ist eine [[Eigenschaften|Eigenschaft]] von [[Quadratische Matrix|quadratischen Matrizen]], die oft im Kontext von [[Symmetrische Matrix|symmetrischen Matrizen]] betrachtet wird. Sie beschreibt das Vorzeichen der **quadratischen Form** $\vec{x}^T A \vec{x}$ für alle Vektoren $\vec{x} \neq \vec{0}$.

**Verbindung zu [[Eigenwerte|Eigenwerten]] (für [[Symmetrische Matrix|symmetrische Matrizen]]):**

Für [[Symmetrische Matrix|symmetrische Matrizen]] kann die Definitheit direkt anhand der Vorzeichen ihrer [[Eigenwerte|Eigenwerte]] bestimmt werden. Dies ist oft die gebräuchlichste Definition in der Praxis.

**Arten der Definitheit (basierend auf [[Eigenwerte|Eigenwerten]]):**

Sei $A$ eine [[Symmetrische Matrix|symmetrische Matrix]] mit [[Eigenwerte|Eigenwerten]] $\lambda_1, \dots, \lambda_n$.

* **Positiv Definit (PD):** Alle [[Eigenwerte|Eigenwerte]] sind **strikt positiv**.
    $$ \lambda_i > 0 \quad \text{für alle } i $$
    Äquivalent: $\vec{x}^T A \vec{x} > 0$ für alle $\vec{x} \neq \vec{0}$.
* **Positiv Semi-Definit (PSD):** Alle [[Eigenwerte|Eigenwerte]] sind **größer oder gleich Null**.
    $$ \lambda_i \ge 0 \quad \text{für alle } i $$
    Äquivalent: $\vec{x}^T A \vec{x} \ge 0$ für alle $\vec{x}$.
* **Negativ Definit (ND):** Alle [[Eigenwerte|Eigenwerte]] sind **strikt negativ**.
    $$ \lambda_i < 0 \quad \text{für alle } i $$
    Äquivalent: $\vec{x}^T A \vec{x} < 0$ für alle $\vec{x} \neq \vec{0}$.
* **Negativ Semi-Definit (NSD):** Alle [[Eigenwerte|Eigenwerte]] sind **kleiner oder gleich Null**.
    $$ \lambda_i \le 0 \quad \text{für alle } i $$
    Äquivalent: $\vec{x}^T A \vec{x} \le 0$ für alle $\vec{x}$.
* **Indefinit:** Die Matrix hat sowohl **positive als auch negative** [[Eigenwerte|Eigenwerte]].
    Äquivalent: Es gibt $\vec{x}_1, \vec{x}_2$ ungleich Null, so dass $\vec{x}_1^T A \vec{x}_1 > 0$ und $\vec{x}_2^T A \vec{x}_2 < 0$.

**Bedeutung:**

Die Definitheit ist eine wichtige [[Eigenschaften|Eigenschaft]] von [[Matrizen]] mit Anwendungen in verschiedenen Bereichen:

* **[[Optimierung|Optimierung]]:** Die Definitheit der Hesse-Matrix wird verwendet, um zu bestimmen, ob ein kritischer Punkt ein lokales Minimum (Hesse-Matrix positiv definit), Maximum (negativ definit) oder Sattelpunkt (indefinit) ist.
* **[[Cholesky-Zerlegung]]:** Die [[Cholesky-Zerlegung]] $A=LL^T$ existiert genau dann, wenn $A$ [[Symmetrische Matrix|symmetrisch]] und positiv definit ist.
* Stabilität von Systemen.

---

## Verwendung:

```dataview
list from [[Definitheit (Matrizen)]]
```