#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Kryptographie]], [[Betriebsmodi]]
#it_security

---

### Betriebsmodi für Blockchiffren

Symmetrische Blockchiffren (wie DES oder [[AES]]) können standardmäßig nur Datenblöcke mit einer festen Länge (z. B. 128 Bit bei AES) verschlüsseln. Um beliebig lange Texte zu verarbeiten, benötigt man einen **Betriebsmodus** (Mode of Operation).

---

#### 1. Grundkonzepte

##### Deterministisch vs. Probabilistisch
* **Deterministische Verschlüsselung**: Gleicher Klartext und gleicher Schlüssel ergeben immer den gleichen Geheimtext. Dies ist unsicher, da Angreifer Wiederholungen und Muster erkennen können.
* **Probabilistische Verschlüsselung**: Durch Einbeziehen eines Zufallswerts ergibt das zweifache Verschlüsseln desselben Klartexts zwei völlig unterschiedliche Geheimtexte.

##### Der Initialisierungsvektor (IV)
Ein IV ist ein zufälliger Datenblock, der zu Beginn des Verschlüsselungsprozesses genutzt wird, um die Verschlüsselung probabilistisch zu machen. 
* **Regel**: Der IV muss nicht geheim gehalten werden, muss aber für jede Nachricht **einzigartig** (Nonce) und bei vielen Modi unvorhersehbar sein.

##### Padding (Füllbits)
Da Blockchiffren nur vollständige Blöcke verarbeiten, müssen unvollständige Daten am Ende aufgefüllt werden.
* **PKCS#7-Standard**: Fehlen zum Auffüllen des Blocks $n$ Bytes, so werden $n$ Bytes angehängt, die jeweils den Wert $n$ (als Byte) tragen.
  * *Beispiel*: Fehlen 3 Bytes, wird mit `03 03 03` aufgefüllt.
  * *Sonderfall*: Ist die Nachricht bereits ein Vielfaches der Blockgröße, muss ein **vollständiger Dummy-Block** (z. B. 16 Bytes mit dem Wert `10` bei AES) angehängt werden, damit der Empfänger beim Entschlüsseln immer eindeutig weiß, wie viele Bytes er abschneiden muss.

---

#### 2. Die klassischen Betriebsmodi

##### A. ECB-Modus (Electronic Codebook)
Jeder Block wird völlig unabhängig voneinander verschlüsselt.
* **Verschlüsselung**: $c_i = E_k(m_i)$
* **Entschlüsselung**: $m_i = D_k(c_i)$
* **Sicherheitsanalyse**: **Völlig unsicher**. Da kein IV verwendet wird, ist der Modus deterministisch. Muster (z. B. in Bilddateien) bleiben im Geheimtext sichtbar (der berühmte "ECB-Pinguin").

```
Klartext-Blöcke:    [ M1 ]      [ M2 ]
                      │           │
                      ▼           ▼
                   [ Enc ]     [ Enc ] <- Schlüssel K
                      │           │
                      ▼           ▼
Geheimtext-Blöcke:  [ C1 ]      [ C2 ]
```

##### B. CBC-Modus (Cipher Block Chaining)
Jeder Klartextblock wird vor der Verschlüsselung per XOR mit dem vorherigen Geheimtextblock verkettet.
* **Verschlüsselung**:
  * Block 0: $c_0 = E_k(m_0 \oplus IV)$
  * Block $i$: $c_i = E_k(m_i \oplus c_{i-1})$
* **Entschlüsselung**:
  * Block 0: $m_0 = D_k(c_0) \oplus IV$
  * Block $i$: $m_i = D_k(c_i) \oplus c_{i-1}$

```
Klartext-Blöcke:    [ M1 ] ──► (⊕)         [ M2 ] ──► (⊕)
                                ▲                      ▲
                                │                      │
  IV ───────────────────────────┘    ┌─────────────────┘
                                     │
                                     │
                                  [ Enc ] ──► Geheimtext C1
                                     │
                                     └─────────────────┐
                                                       ▼
                                                    [ Enc ] ──► Geheimtext C2
```

* **Eigenschaften**:
  * Durch die Verkettung ist das Verfahren probabilistisch.
  * **Parallelisierung**: Die Verschlüsselung kann **nicht** parallelisiert werden (da $c_{i-1}$ bekannt sein muss). Die Entschlüsselung ist jedoch voll parallelisierbar, da alle Geheimtextblöcke $c_i$ bereits vorliegen.

---
#### Flashcards

Warum ist der ECB-Modus für die Praxis ungeeignet?::Weil er deterministisch arbeitet: Identische Klartextblöcke erzeugen identische Geheimtextblöcke, wodurch die Struktur der zugrundeliegenden Daten sichtbar bleibt.

Wie lautet die mathematische Formel für die Verschlüsselung des ersten Blocks im CBC-Modus?::$c_0 = E_k(m_0 \oplus IV)$.

Warum kann die Verschlüsselung im CBC-Modus nicht parallelisiert werden, die Entschlüsselung aber schon?::Bei der Verschlüsselung wird der Geheimtext des vorherigen Blocks benötigt, welcher erst berechnet werden muss. Bei der Entschlüsselung liegen alle Geheimtextblöcke bereits vor.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Betriebsmodi für Blockchiffren]]
SORT file.mtime DESC
```
