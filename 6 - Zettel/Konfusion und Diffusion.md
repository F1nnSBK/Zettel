#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Kryptographie]], [[Symmetrische-Kryptographie]]
#it_security

---

### Konfusion und Diffusion

Die Designstrategie moderner symmetrischer Verschlüsselungsverfahren (sowohl DES als auch [[AES]]) basiert auf den zwei von Claude Shannon (1949) definierten Konzepten: **Konfusion** und **Diffusion**.

---

#### 1. Konfusion (Confusion)
* **Ziel**: Die Beziehung zwischen dem geheimen Schlüssel und dem Geheimtext so komplex und undurchschaubar wie möglich zu machen.
* **Wirkung**: Ein Angreifer darf aus der Beobachtung des Geheimtextes keinerlei Rückschlüsse auf den Schlüssel ziehen können.
* **Umsetzung**: Durch **Substitutionen (S-Boxen)**. S-Boxen ersetzen Bitmuster nichtlinear. Das bedeutet, dass kleine Änderungen des Inputs zu chaotischen Änderungen des Outputs führen, die sich nicht durch lineare Gleichungen beschreiben lassen.

---

#### 2. Diffusion
* **Ziel**: Die statistischen Eigenschaften des Klartextes über den gesamten Geheimtext zu verteilen.
* **Wirkung**: Ein Angreifer darf keine Häufigkeiten oder Muster des Klartextes im Geheimtext wiederfinden. Jedes Bit des Geheimtextes sollte von möglichst vielen Bits des Klartextes und des Schlüssels abhängen.
* **Umsetzung**: Durch **Permutationen (P-Boxen / Vertauschungen)**. In DES wird dies durch die P-Box und die Expansion vollzogen; in [[AES]] durch die Operationen *ShiftRows* und *MixColumns*.

---

#### ❄️ Der Lawineneffekt (Avalanche Effect)
Der Lawineneffekt ist die mathematische Messgröße für eine gute Diffusion.
* **Definition**: Eine Chiffre zeigt einen starken Lawineneffekt, wenn die Änderung eines einzigen Bits im Klartext (oder im Schlüssel) dazu führt, dass sich in der nächsten Runde und letztlich im finalen Geheimtext im Durchschnitt **50% aller Bits** verändern.
* **Relevanz**: Ohne ausreichenden Lawineneffekt können Angreifer über differenzielle Kryptoanalyse (Vergleich von Textpaaren mit geringem Unterschied) den Schlüssel Stück für Stück rekonstruieren.

---
#### Flashcards

Was versteht man unter Konfusion nach Claude Shannon?::Die Verschleierung der Beziehung zwischen dem Schlüssel und dem Geheimtext, meist realisiert durch nichtlineare S-Boxen.

Was beschreibt Diffusion in einer Blockchiffre?::Das Verteilen des Einflusses einzelner Klartextbits über den gesamten Geheimtext, realisiert durch Permutationen (P-Boxen).

Wie viel Prozent der Geheimtextbits sollten sich ändern, wenn ein einziges Klartextbit kippt (Lawineneffekt)?::Im Durchschnitt 50 % aller Bits des Geheimtexts.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Konfusion und Diffusion]]
SORT file.mtime DESC
```
