#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Kryptographie]], [[Asymmetrische-Kryptographie]]
#it_security

---

### RSA-Verfahren

Das **RSA-Verfahren** (benannt nach Rivest, Shamir und Adleman, 1977) ist das am weitesten verbreitete asymmetrische Verschlüsselungs- und Signaturverfahren.

---

#### 1. Die Schlüsselerzeugung (Key Generation)
Die Generierung des Schlüsselpaares erfolgt in folgenden mathematischen Schritten:

1. **Primzahlwahl**: Wähle zwei sehr große, geheime Primzahlen $p$ und $q$ ($p \neq q$).
2. **Modul berechnen**: Berechne das Produkt $n = p \cdot q$.
   * *Hinweis*: $n$ (der RSA-Modul) wird veröffentlicht.
3. **Eulersche Phi-Funktion**: Berechne $\phi(n)$:
   $$\phi(n) = (p-1) \cdot (q-1)$$
4. **Öffentlicher Exponent ($e$)**: Wähle eine Zahl $e$, die teilerfremd zu $\phi(n)$ ist:
   $$\text{ggT}(e, \phi(n)) = 1 \quad \text{mit} \quad 1 < e < \phi(n)$$
   * *Praxis*: Häufig wird $e = 65537$ ($2^{16} + 1$) gewählt, da dies eine Primzahl mit wenigen Einsen in Binärform ist und dadurch modulare Exponentiationsberechnungen beschleunigt.
5. **Privater Exponent ($d$)**: Berechne das multiplikative Inverse zu $e$ modulo $\phi(n)$ (mittels des Erweiterten Euklidischen Algorithmus):
   $$d \equiv e^{-1} \pmod{\phi(n)} \iff e \cdot d \equiv 1 \pmod{\phi(n)}$$

##### Das Ergebnis
* **Öffentlicher Schlüssel (Public Key)**: $(e, n)$
* **Privater Schlüssel (Private Key)**: $(d, n)$ *(Zusätzlich müssen $p$, $q$ und $\phi(n)$ vernichtet oder streng geheim gehalten werden).*

---

#### 2. Verschlüsselung & Entschlüsselung
Der Klartext $m$ muss als Zahl repräsentiert werden, wobei gilt: $0 \le m < n$.

##### Verschlüsselung (mit dem Public Key)
$$c = m^e \pmod n$$

##### Entschlüsselung (mit dem Private Key)
$$m = c^d \pmod n$$

---

#### 3. Der mathematische Korrektheitsbeweis
Warum ergibt $c^d \pmod n$ wieder den Klartext $m$?
Aus der Definition von $d$ folgt, dass $e \cdot d = k \cdot \phi(n) + 1$ für ein ganzzahliges $k$.
$$c^d \equiv (m^e)^d \equiv m^{e \cdot d} \equiv m^{k \cdot \phi(n) + 1} \equiv (m^{\phi(n)})^k \cdot m \pmod n$$
Nach dem **Satz von Euler** gilt für teilerfremde Zahlen $m$ und $n$: $m^{\phi(n)} \equiv 1 \pmod n$.
$$c^d \equiv (1)^k \cdot m \equiv m \pmod n$$

**Verknüpfte Zettel:**
- [[Endliche Körper und Ringe]] (Grundlagen zum multiplikativen Inversen und dem EEA)

---
#### Flashcards

Wie lauten die Formeln zur Ver- und Entschlüsselung bei RSA?::Verschlüsselung: $c = m^e \pmod n$. Entschlüsselung: $m = c^d \pmod n$.

Aus welchen Schritten besteht die RSA-Schlüsselerzeugung?::Wähle große Primzahlen $p, q$. Berechne Modul $n = p \cdot q$ und $\phi(n) = (p-1)(q-1)$. Wähle $e$ teilerfremd zu $\phi(n)$. Berechne den privaten Exponenten $d = e^{-1} \pmod{\phi(n)}$.

Warum wird in der Praxis für den öffentlichen Exponenten häufig $e = 65537$ gewählt?::Weil $65537$ ($2^{16}+1$) eine Primzahl mit einer sehr kurzen Binärdarstellung (nur zwei Einsen) ist, was die modulare Exponentiation bei der Verschlüsselung beschleunigt.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[RSA-Verfahren]]
SORT file.mtime DESC
```
