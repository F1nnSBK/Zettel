#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Kryptographie]], [[Klassische-Chiffren]]
#it_security

---

### Monoalphabetische Chiffren

Bei einer **monoalphabetischen Substitutionschiffre** wird jeder Buchstabe des Klartexts durch einen festen anderen Buchstaben des Geheimtextalphabets ersetzt. 

---

#### Die drei klassischen Typen (modulo 26)

##### 1. Verschiebechiffre (Cäsar-Chiffre)
Der Klartext wird um einen festen Schlüsselwert $k$ im Alphabet verschoben.
* **Verschlüsselung**: $c = (m + k) \pmod{26}$
* **Entschlüsselung**: $m = (c - k) \pmod{26}$
* **Sicherheitsanalyse**: Extrem schwach. Der Schlüsselraum beträgt nur 26 Möglichkeiten und kann sofort per Brute-Force durchprobiert werden.

##### 2. Multiplikative Chiffre
Der Klartextwert wird mit einem Schlüssel $k$ multipliziert.
* **Verschlüsselung**: $c = (m \cdot k) \pmod{26}$
* **Schlüsselbedingung**: Das Inverse von $k$ muss existieren, daher muss $\text{ggT}(k, 26) = 1$ sein. Gültige Schlüssel sind nur $\{1, 3, 5, 7, 9, 11, 15, 17, 19, 21, 23, 25\}$.
* **Schlüsselraum**: Beträgt nur $\phi(26) = 12$ Möglichkeiten.

##### 3. Affine Chiffre
Kombiniert die multiplikative und die Verschiebechiffre mit einem Schlüsselpaar $(a, b)$.
* **Verschlüsselung**: $c = E(m) = (a \cdot m + b) \pmod{26}$
* **Entschlüsselung**: $m = D(c) = a^{-1} \cdot (c - b) \pmod{26}$
* **Schlüsselbedingung**: $\text{ggT}(a, 26) = 1$.
* **Beispiel zur Entschlüsselung**:
  * Gegeben: $c = 15$, $a = 3$, $b = 5$.
  * Berechnung von $a^{-1}$: In $\mathbb{Z}_{26}$ gilt $3 \cdot 9 = 27 \equiv 1 \pmod{26} \implies a^{-1} = 9$.
  * Entschlüsselung: $m = 9 \cdot (15 - 5) \pmod{26} = 9 \cdot 10 \pmod{26} = 90 \pmod{26} = 12 \implies \text{'M'}$.

---

#### ⚖️ Warum monoalphabetische Chiffren unsicher sind
* **Häufigkeitsanalyse**: Da jeder Buchstabe immer durch den exakt gleichen Geheimtextbuchstaben ersetzt wird, bleibt die statistische Verteilung der Buchstaben einer Sprache erhalten. 
* In der deutschen Sprache ist der häufigste Buchstabe das **'E'**. Der häufigste Buchstabe im Geheimtext entspricht daher mit hoher Wahrscheinlichkeit dem verschlüsselten 'E', worüber das gesamte Alphabet schnell rekonstruiert werden kann.

---
#### Flashcards

Wie lauten die Formeln zur Verschlüsselung und Entschlüsselung bei der Affinen Chiffre?::Verschlüsselung: $c = (a \cdot m + b) \pmod{26}$. Entschlüsselung: $m = a^{-1} \cdot (c - b) \pmod{26}$.

Welche mathematische Voraussetzung muss für den Parameter $a$ bei der Affinen Chiffre gelten?::Er muss teilerfremd zum Modul sein, also: $\text{ggT}(a, 26) = 1$. Nur dann existiert das multiplikative Inverse $a^{-1}$ zur Entschlüsselung.

Warum brechen monoalphabetische Chiffren unter einer Häufigkeitsanalyse?::Weil sie die statistische Verteilung der Buchstaben der Klartextsprache eins zu eins auf den Geheimtext übertragen (z. B. bleibt das verschlüsselte 'E' das häufigste Zeichen im Geheimtext).

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Monoalphabetische Chiffren]]
SORT file.mtime DESC
```
