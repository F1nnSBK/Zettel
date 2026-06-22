#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Kryptographie]], [[Asymmetrische-Kryptographie]]
#it_security

---

### Sicherheit und Angriffe auf RSA

Die Sicherheit des [[RSA-Verfahren|RSA-Verfahrens]] hängt maßgeblich von der mathematischen Komplexität der Primfaktorzerlegung ab. In dieser Notiz werden die Angriffsvektoren auf RSA analysiert.

---

#### 1. Die mathematische Sicherheitsbasis
* **Das Faktorisierungsproblem**: Ein Angreifer kennt den öffentlichen Modul $n$. Um den privaten Schlüssel $d$ zu berechnen, muss er $n$ in seine Primfaktoren $p$ und $q$ zerlegen:
  $$n = p \cdot q$$
  Es gibt bisher keinen effizienten (polynomiellen) klassischen Algorithmus zur Faktorisierung großer Zahlen. Der beste bekannte klassische Algorithmus ist das **Zahlkörpersieb (GNFS)**.
* **Quantencomputer**: Mit dem *Shor-Algorithmus* auf einem ausreichend großen Quantencomputer könnte RSA in polynomieller Zeit gebrochen werden (Motivation für Post-Quantum-Kryptographie).
* **Aktuelle Empfehlung**: Mindestens **2048 Bit** Schlüssellänge für mittelfristige Sicherheit, besser **4096 Bit**.

---

#### 2. Kryptoanalytische & Mathematische Angriffe

##### A. Angriff bei zu kleinem privaten Exponenten $d$ (Wiener’s Attack)
* Wenn der private Schlüssel $d$ zu klein gewählt wird ($d < \frac{1}{3} n^{1/4}$), kann er mithilfe von Kettenbrüchen (Continued Fractions) effizient aus dem öffentlichen Schlüssel $(e, n)$ berechnet werden.

##### B. Malleability (Verformbarkeit) von Textbook-RSA
* Reines RSA (ohne Padding) ist mathematisch homomorph bezüglich der Multiplikation:
  $$E_k(m_1) \cdot E_k(m_2) \equiv m_1^e \cdot m_2^e \equiv (m_1 \cdot m_2)^e \equiv E_k(m_1 \cdot m_2) \pmod n$$
* **Gefahr**: Ein Angreifer kann einen abgefangenen Geheimtext $c$ manipulieren, indem er ihn mit $s^e \pmod n$ multipliziert. Das Ergebnis $c' = c \cdot s^e \pmod n$ entschlüsselt sich beim Empfänger zu:
  $$m' = m \cdot s \pmod n$$
  Der Klartext wurde gezielt verändert, ohne dass der Angreifer den Schlüssel oder den Originalinhalt kannte.

---

#### 3. Implementierungs- & Padding-Angriffe

##### A. Padding-Oracle-Angriffe (Bleichenbacher-Angriff)
* Um Malleability zu verhindern, wird der Klartext vor der Verschlüsselung mit einem strukturierten Padding (z. B. **OAEP** - Optimal Asymmetric Encryption Padding) versehen.
* **Der Angriff**: Schickt ein Angreifer einen modifizierten Geheimtext an den Server und dieser antwortet mit unterschiedlichen Fehlermeldungen (z. B. "Decryption Error" vs. "Bad Padding"), verhält sich der Server als **Padding Oracle**.
* Durch systematisches Senden modifizierter Nachrichten und Auswerten der Serverantworten kann der Angreifer den Klartext einer abgefangenen Nachricht in ca. 1 Million Anfragen vollständig rekonstruieren (Bleichenbacher's "Million-Message-Attack").
* **Gegenmaßnahme**: Konstante Fehlermeldungen und Zeitabläufe bei Entschlüsselungsfehlern.

##### B. Seitenkanalangriffe (Timing-Angriffe)
* Die modulare Exponentiation $c^d \pmod n$ dauert je nach Anzahl der gesetzten Bits im privaten Schlüssel $d$ unterschiedlich lange (z. B. beim Square-and-Multiply-Verfahren).
* **Gegenmaßnahme (Blinding)**: Der Server multipliziert den Geheimtext vor der Entschlüsselung mit einem zufälligen Wert und rechnet diesen danach wieder heraus. Dadurch ist die Rechenzeit unabhängig vom Schlüssel.

**Verknüpfte Zettel:**
- [[RSA-Verfahren]] (Mathematische Grundlagen)

---
#### Flashcards

Auf welchem mathematischen Problem basiert die Sicherheit von RSA?::Auf der Schwierigkeit der Primfaktorzerlegung (Faktorisierungsproblem) des Moduls $n = p \cdot q$.

Was versteht man unter der Malleability (Verformbarkeit) von reinem RSA?::Dass man den Geheimtext mathematisch so verändern kann, dass sich der resultierende Klartext beim Empfänger vorhersagbar verändert ($c' = c \cdot s^e \implies m' = m \cdot s$).

Wie schützt man RSA vor Malleability- und Padding-Oracle-Angriffen?::Durch die Verwendung moderner, standardisierter Padding-Verfahren wie OAEP (Optimal Asymmetric Encryption Padding) und das Vermeiden detaillierter Fehlermeldungen bei Entschlüsselungsfehlern.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Sicherheit und Angriffe auf RSA]]
SORT file.mtime DESC
```
