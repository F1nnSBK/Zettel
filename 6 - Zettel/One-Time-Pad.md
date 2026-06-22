#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Kryptographie]], [[Klassische-Chiffren]]
#it_security

---

### One-Time-Pad (OTP)

Das **One-Time-Pad** (Vernam-Chiffre) ist das einzige kryptographische Verfahren, das nachweislich **perfekte Sicherheit** (mathematische Unknackbarkeit) bietet.

---

#### Funktionsweise (Binärvariante)
Klartext $m$ und Schlüssel $k$ liegen als Bitströme vor. Die Verschlüsselung erfolgt durch eine bitweise Exklusiv-Oder-Verknüpfung (XOR, $\oplus$).
* **Verschlüsselungsformel**:
  $$c = m \oplus k$$
* **Entschlüsselungsformel**:
  $$m = c \oplus k \quad (\text{da } c \oplus k = m \oplus k \oplus k = m \oplus 0 = m)$$

---

#### ⚖️ Bedingungen für perfekte Sicherheit (nach Claude Shannon)
Das One-Time-Pad ist nur dann perfekt sicher, wenn alle vier folgenden Bedingungen **strikt** erfüllt sind:

1. **Echter Zufall (True Randomness)**: Der Schlüssel muss mithilfe eines physikalischen Zufallsgenerators (TRNG) erzeugt werden. Pseudozufall (PRNG) zerstört die Unknackbarkeit.
2. **Schlüssellänge**: Der Schlüssel muss mindestens genauso lang sein wie der Klartext.
3. **Einmalige Verwendung**: Jeder Schlüssel darf exakt nur ein einziges Mal benutzt werden. (Bei Wiederverwendung brechen Angriffe wie das Two-Time-Pad das Verfahren sofort).
4. **Absolute Geheimhaltung**: Der Schlüssel muss über einen sicheren Kanal ausgetauscht werden.

##### Was bedeutet "Perfekte Sicherheit" (Shannon-Sicherheit)?
Selbst ein Angreifer mit unendlicher Rechenleistung kann das OTP nicht brechen:
* Der Geheimtext liefert keinerlei statistische Informationen über den Klartext.
* Zu jedem Geheimtext existieren bei entsprechendem Schlüssel alle denkbaren Klartexte derselben Länge.
* *Beispiel*: Ein 5-Buchstaben-Geheimtext kann bei unterschiedlichen Schlüsseln das Wort "LEBEN" oder das Wort "TODES" ergeben. Beide sind für den Angreifer exakt gleich wahrscheinlich.

---

#### 🛠️ Praktische Einschränkungen
Trotz perfekter Sicherheit wird das OTP in der Praxis selten verwendet:
* **Schlüsselaustausch-Problem**: Da der Schlüssel so lang sein muss wie die Nachricht, ist der sichere Austausch des Schlüssels genauso aufwendig wie der sichere Austausch der Nachricht selbst.

---
#### Flashcards

Welche vier Bedingungen müssen für die perfekte Sicherheit des One-Time-Pad erfüllt sein?::Der Schlüssel muss echt zufällig sein, mindestens so lang wie die Nachricht, darf nur einmal verwendet werden und muss absolut geheim bleiben.

Was bedeutet perfekte Sicherheit aus informationstheoretischer Sicht?::Dass der Geheimtext dem Angreifer keinerlei Rückschlüsse auf den Klartext erlaubt, da bei unbegrenzter Rechenleistung jeder Klartext derselben Länge gleich wahrscheinlich ist.

Warum wird das One-Time-Pad trotz perfekter Sicherheit im Internet kaum eingesetzt?::Wegen des Schlüsselaustauschproblems. Es ist unpraktisch, vor jeder verschlüsselten Verbindung einen Schlüssel auszutauschen, der so groß wie die zu übertragenden Daten ist.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[One-Time-Pad]]
SORT file.mtime DESC
```
