#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Kryptographie]], [[Asymmetrische-Kryptographie]]
#it_security

---

### Diffie-Hellman Key Exchange (DHKE)

Der **Diffie-Hellman-Schlüsselaustausch (DHKE)** ist das erste asymmetrische kryptographische Protokoll (1976 veröffentlicht). Es ermöglicht zwei Parteien, über einen unsicheren (abhörbaren) Kanal einen gemeinsamen geheimen Schlüssel zu vereinbaren, ohne dass dieser selbst übertragen wird.

---

#### 1. Der mathematische Ablauf
Alice und Bob wollen sich auf einen Schlüssel einigen. Sie vereinbaren zunächst öffentlich zwei Parameter:
* Eine große Primzahl $p$ (heute mind. 2048 Bit)
* Einen Generator $\alpha$ (eine Primitivwurzel modulo $p$)

##### Ablauf der Berechnung
```
   Alice (Geheimnis: a)                          Bob (Geheimnis: b)
   ───────────────────                          ──────────────────
   Berechnet: A = α^a mod p                     Berechnet: B = α^b mod p
          │                                            │
          └─────────── Schickt A an Bob ───────────────┤
          ├─────────── Schickt B an Alice ─────────────┘
          │                                            │
   Berechnet: s = B^a mod p                     Berechnet: s = A^b mod p
```

##### Der mathematische Beweis (Warum erhalten beide denselben Wert?)
Da die modulare Exponentiation kommutativ ist, gilt:
$$s = B^a \equiv (\alpha^b)^a \equiv \alpha^{ab} \equiv (\alpha^a)^b \equiv A^b \pmod p$$
Dieser gemeinsame Wert $s$ wird als Master-Key für die symmetrische Verschlüsselung (z. B. [[AES]]) genutzt.

---

#### 2. Das Diskrete Logarithmusproblem (DLP)
Die Sicherheit von DHKE beruht auf der Einwegfunktion der modularen Exponentiation:
* **Einfach**: Die Berechnung von $A = \alpha^a \pmod p$ ist extrem schnell.
* **Schwer (DLP)**: Ein Angreifer (Eve) fängt die öffentlichen Parameter $p, \alpha$ sowie die übertragenen Schlüssel $A$ und $B$ ab. Um das Geheimnis $a$ zu berechnen, müsste sie folgende Gleichung lösen:
  $$a = \log_{\alpha}(A) \pmod p$$
  Dies ist das **Diskrete Logarithmusproblem**. Für ausreichend große, sorgfältig gewählte Primzahlen $p$ ist dieses Problem mit bekannten Algorithmen nicht in realistischer Zeit lösbar.

---

#### 3. Anforderungen an die Parameter
* **Primzahl $p$**: Muss eine *sichere Primzahl* (Safe Prime) sein, d. h. $p = 2q + 1$, wobei $q$ ebenfalls eine Primzahl ist. Dies verhindert Angriffe wie den *Pohlig-Hellman-Algorithmus*.
* **Generator $\alpha$**: Muss eine Primitivwurzel modulo $p$ sein, damit die erzeugte Untergruppe der Zahlen groß genug ist.

---
#### Flashcards

Wie berechnen die Parteien den gemeinsamen geheimen Schlüssel $s$ bei DHKE?::Alice berechnet $s = B^a \pmod p$ und Bob berechnet $s = A^b \pmod p$.

Welches mathematische Problem verhindert, dass ein Lauscher den geheimen Schlüssel berechnen kann?::Das Diskrete Logarithmusproblem (DLP): Es ist unmöglich, aus den abgefangenen Werten $A = \alpha^a \pmod p$ und $B = \alpha^b \pmod p$ die geheimen Exponenten $a$ oder $b$ effizient zu berechnen.

Warum darf die Primzahl $p$ nicht beliebig gewählt werden?::Weil sie eine sichere Primzahl ($p = 2q+1$) sein muss, um mathematische Angriffe (z. B. Pohlig-Hellman), die auf der Zerlegung der Gruppenordnung basieren, zu verhindern.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Diffie-Hellman Key Exchange]]
SORT file.mtime DESC
```
