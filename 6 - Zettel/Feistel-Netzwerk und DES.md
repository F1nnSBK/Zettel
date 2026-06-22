#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Kryptographie]], [[Symmetrische-Kryptographie]]
#it_security

---

### Feistel-Netzwerk und DES

Der **Data Encryption Standard (DES)** ist eine historische Blockchiffre (1977 veröffentlicht), die auf der Architektur eines **Feistel-Netzwerks** basiert.

---

#### 1. Das Feistel-Netzwerk
Ein Feistel-Netzwerk zerlegt einen Klartextblock der Länge $2n$ in zwei Hälften: Links ($L$) und Rechts ($R$). In jeder Runde wird nur eine Hälfte modifiziert, und die Hälften werden vertauscht.

##### Die Runden-Formeln (Verschlüsselung)
Für jede Runde $i = 1, \dots, r$:
$$L_i = R_{i-1}$$
$$R_i = L_{i-1} \oplus f(R_{i-1}, K_i)$$
*Wobei $f$ eine beliebige Rundenfunktion und $K_i$ der Rundenschlüssel ist.*

##### Vorteil der Feistel-Struktur
* **Symmetrie**: Verschlüsselung und Entschlüsselung nutzen denselben Algorithmus. Zur Entschlüsselung müssen lediglich die Rundenschlüssel in umgekehrter Reihenfolge ($K_r, \dots, K_1$) eingegeben werden.
* **Keine Invertierbarkeit von $f$ nötig**: Die Rundenfunktion $f$ selbst muss **nicht** umkehrbar (invertierbar) sein, da sich die Modifikation bei der Entschlüsselung durch das XOR aufhebt.

---

#### 2. Aufbau von DES
* **Blockgröße**: 64 Bit
* **Schlüssellänge**: 56 Bit (Effektiv). Der ursprüngliche Schlüssel hat 64 Bit, aber jedes 8. Bit dient als Paritätsbit und wird verworfen.
* **Struktur**: 16 Feistel-Runden, umrahmt von einer initialen Permutation (IP) und einer finalen inversen Permutation ($IP^{-1}$).

##### Die f-Funktion von DES
Die f-Funktion verarbeitet die rechte Hälfte $R_{i-1}$ (32 Bit) und den Rundenschlüssel $K_i$ (48 Bit):
1. **Expansion (E-Box)**: Dehnt die 32 Bit durch Duplizieren bestimmter Bits auf 48 Bit aus (linear).
2. **Schlüssel-XOR**: Verknüpft das Ergebnis per XOR mit dem Rundenschlüssel $K_i$ (48 Bit).
3. **Substitution (S-Boxen)**: Teilt die 48 Bit in 8 Blöcke zu je 6 Bit auf. Jeder Block wird durch eine eigene **S-Box** (S1 bis S8) in 4 Bit übersetzt (Gesamt: 32 Bit). Dies ist der einzige **nichtlineare** Teil von DES und das Herzstück der Sicherheit.
4. **Permutation (P-Box)**: Vertauscht die Bits des 32-Bit-Ausgangs (linear).

---
#### Flashcards

Wie lauten die mathematischen Formeln für eine Verschlüsselungsrunde im Feistel-Netzwerk?::$L_i = R_{i-1}$ und $R_i = L_{i-1} \oplus f(R_{i-1}, K_i)$.

Warum müssen die S-Boxen in DES nichtlinear sein?::Weil lineare Chiffren extrem leicht durch das Aufstellen und Lösen linearer Gleichungssysteme gebrochen werden können. Nichtlinearität erzwingt mathematische Komplexität.

Welche effektive Schlüssellänge hat DES und wofür dienen die restlichen Bits?::56 Bit effektiv. Die restlichen 8 Bits (bei 64 Bit Gesamtlänge) dienen als Paritätsbits zur Fehlererkennung und werden verworfen.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Feistel-Netzwerk und DES]]
SORT file.mtime DESC
```
