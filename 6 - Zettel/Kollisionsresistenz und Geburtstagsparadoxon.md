#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Kryptographie]], [[Hashing]], [[Wahrscheinlichkeitsrechnung]]
#it_security

---

### Kollisionsresistenz und Geburtstagsparadoxon

Das **Geburtstagsparadoxon** ist ein fundamentales Phänomen der Wahrscheinlichkeitstheorie. In der Kryptographie bestimmt es die notwendige Ausgabelänge von Hash-Funktionen, um vor Kollisionsangriffen geschützt zu sein.

---

#### 1. Das Geburtstagsparadoxon
* **Die Fragestellung**: Wie viele Personen müssen sich in einem Raum befinden, damit die Wahrscheinlichkeit, dass mindestens zwei am selben Tag Geburtstag haben, größer als 50% ist?
* **Die Intuition**: Viele schätzen die Zahl auf $365/2 \approx 180$ Personen.
* **Die Realität**: Es reichen bereits **23 Personen** aus. Bei 57 Personen liegt die Wahrscheinlichkeit schon bei über 99%.

##### Mathematische Begründung
Die Wahrscheinlichkeit steigt deshalb so schnell, weil wir nicht fragen, ob jemand an *einem bestimmten* Tag Geburtstag hat, sondern ob *irgendein Paar* am selben Tag Geburtstag hat.
* Die Anzahl der möglichen Zweierpaare bei $n$ Personen wächst quadratisch:
  $$\text{Anzahl Paare} = \frac{n \cdot (n - 1)}{2} = \begin{pmatrix} n \\ 2 \end{pmatrix}$$
* Bei $n = 23$ Personen gibt es bereits $\frac{23 \cdot 22}{2} = 253$ mögliche Paare, die alle eine Kollisionschance haben.

##### Die Näherungsformel
Für eine Menge von $d$ möglichen Ergebnissen (z. B. 365 Tage) und $n$ zufälligen Proben (Personen) ist die Wahrscheinlichkeit für mindestens eine Kollision:
$$p(n; d) \approx 1 - e^{-\frac{n^2}{2d}}$$

---

#### 2. Relevanz für Hash-Funktionen (Kollisionsangriffe)
Das Geburtstagsparadoxon besagt, dass es dramatisch viel einfacher ist, eine **beliebige Kollision** ($m_1 \neq m_2$ mit $H(m_1) = H(m_2)$) zu finden, als zu einer *festen* Nachricht $m_1$ ein passendes Gegenstück $m_2$ zu berechnen (Second Preimage).

* **Halbierung der Bit-Sicherheit**:
  * Eine Hash-Funktion besitze eine Ausgabelänge von $k$ Bits. Der Wertebereich umfasst somit $d = 2^k$ mögliche Hashes.
  * Nach dem Geburtstagsparadoxon reicht es aus, ca. $n \approx \sqrt{2^k} = 2^{k/2}$ Nachrichten zu hashen, um mit einer Wahrscheinlichkeit von $\approx 50\%$ eine Kollision zu finden.
  * **Folge**: Um 128 Bit Sicherheit gegen Kollisionsangriffe zu garantieren, muss die Hashfunktion mindestens **256 Bit** lang sein (z. B. SHA-256). Ein 128-Bit-Hash (wie MD5) bietet nur 64 Bit Kollisionssicherheit und ist per Brute-Force leicht angreifbar.

**Verknüpfte Zettel:**
- [[Bedingte Wahrscheinlichkeit]] (Mathematische Grundlage der Wahrscheinlichkeitsrechnung)

---
#### Flashcards

Was besagt das Geburtstagsparadoxon bezüglich der Wahrscheinlichkeit von Übereinstimmungen?::Dass die Wahrscheinlichkeit für Übereinstimmungen (Kollisionen) viel schneller steigt als gedacht, da die Anzahl der untersuchten Paare quadratisch mit der Probenzahl wächst (z. B. $>50\%$ bei 23 Personen).

Wie wirkt sich das Geburtstagsparadoxon auf die Kollisionssicherheit von Hashfunktionen aus?::Es halbiert die effektive Bit-Sicherheit. Eine Hashfunktion mit $k$ Bits Ausgabelänge bietet nur $k/2$ Bits effektive Sicherheit gegen Kollisionsangriffe.

Wie viele Hashes müssen bei SHA-256 (256-Bit-Ausgabe) generiert werden, um mit 50 % Wahrscheinlichkeit eine Kollision zu finden?::Ungefähr $2^{128}$ Hashes (statt der intuitiv vermuteten $2^{256}$).

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Kollisionsresistenz und Geburtstagsparadoxon]]
SORT file.mtime DESC
```
