#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Kryptographie]], [[Symmetrische-Kryptographie]]
#it_security

---

### AES-Operationen

Diese Notiz beschreibt die mathematischen Details der vier Kernoperationen von [[AES]] (SubBytes, ShiftRows, MixColumns).

---

#### 1. SubBytes (Byte-Substitution)
SubBytes ist die einzige nichtlineare Operation in AES. Jedes Byte $a_{i,j}$ des States wird durch ein Byte $b_{i,j}$ ersetzt.

##### Mathematische Konstruktion der S-Box
Die Substitution erfolgt in zwei aufeinanderfolgenden Schritten im Galois-Körper $GF(2^8)$:
1. **Multiplikative Inversion**: Berechne das Inverse $x = a_{i,j}^{-1}$ in $GF(2^8)$ bezüglich des irreduziblen Polynoms:
   $$P(x) = x^8 + x^4 + x^3 + x + 1$$
   *(Das Element $00_{16}$ wird auf sich selbst abgebildet).*
2. **Affine Transformation**: Multiplikation mit einer festen Matrix über $GF(2)$ und anschließendes XOR-Verknüpfen mit dem Byte $63_{16}$ ($01100011_2$).
* **Zweck**: Die Inversion liefert maximale Nichtlinearität (Schutz gegen differenzielle Kryptoanalyse). Die affine Transformation zerstört die rein algebraische Struktur, um algebraische Angriffe zu verhindern.

---

#### 2. ShiftRows (Zeilenverschiebung)
ShiftRows verschiebt die Zeilen des States zyklisch nach links. Sie sorgt für die Diffusion der Daten über die Spaltengrenzen hinweg.
* Zeile 0: verschoben um **0 Bytes** (keine Änderung)
* Zeile 1: verschoben um **1 Byte** nach links
* Zeile 2: verschoben um **2 Bytes** nach links
* Zeile 3: verschoben um **3 Bytes** nach links

$$\begin{pmatrix} s_{0,0} & s_{0,1} & s_{0,2} & s_{0,3} \\ s_{1,0} & s_{1,1} & s_{1,2} & s_{1,3} \\ s_{2,0} & s_{2,1} & s_{2,2} & s_{2,3} \\ s_{3,0} & s_{3,1} & s_{3,2} & s_{3,3} \end{pmatrix} \rightarrow \begin{pmatrix} s_{0,0} & s_{0,1} & s_{0,2} & s_{0,3} \\ s_{1,1} & s_{1,2} & s_{1,3} & s_{1,0} \\ s_{2,2} & s_{2,3} & s_{2,0} & s_{2,1} \\ s_{3,3} & s_{3,0} & s_{3,1} & s_{3,2} \end{pmatrix}$$

---

#### 3. MixColumns (Spaltenmischung)
MixColumns vermischt die Bytes innerhalb jeder Spalte. Zusammen mit ShiftRows wird dadurch nach wenigen Runden eine vollständige Diffusion (Lawineneffekt) erreicht.
* **Mathematik**: Jede Spalte wird als Polynom vom Grad $< 4$ über $GF(2^8)$ interpretiert und mit einem festen Polynom $c(x) = 03 \cdot x^3 + 01 \cdot x^2 + 01 \cdot x + 02 \pmod{x^4 + 1}$ multipliziert.
* **Matrixform**: Dies entspricht einer Matrix-Vektor-Multiplikation im Körper $GF(2^8)$:
  $$\begin{pmatrix} s'_{0,j} \\ s'_{1,j} \\ s'_{2,j} \\ s'_{3,j} \end{pmatrix} = \begin{pmatrix} 02 & 03 & 01 & 01 \\ 01 & 02 & 03 & 01 \\ 01 & 01 & 02 & 03 \\ 03 & 01 & 01 & 02 \end{pmatrix} \begin{pmatrix} s_{0,j} \\ s_{1,j} \\ s_{2,j} \\ s_{3,j} \end{pmatrix}$$
  *Alle Multiplikationen und Additionen erfolgen nach den Regeln von $GF(2^8)$.*

**Verknüpfte Zettel:**
- [[Matrizen]] (Verwendung von Matrixmultiplikation zur Diffusion)
- [[Endliche Körper und Ringe]] (Die mathematische Struktur von $GF(2^8)$)

---
#### Flashcards

Aus welchen zwei Schritten setzt sich die AES S-Box mathematisch zusammen?::Zuerst die multiplikative Inversion im Galois-Körper $GF(2^8)$, danach eine affine Transformation über $GF(2)$.

Warum wird bei der S-Box-Konstruktion nach der Inversion noch eine affine Transformation durchgeführt?::Um die rein algebraische Struktur der Inversion zu brechen, wodurch das Lösen einfacher algebraischer Gleichungssysteme zur Entschlüsselung unmöglich wird.

Wie sorgt ShiftRows für die Durchmischung der Daten?::Durch das zeilenweise zyklische Verschieben nach links (0, 1, 2, 3 Positionen) werden Bytes einer Spalte auf vier verschiedene Spalten aufgeteilt.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[AES-Operationen]]
SORT file.mtime DESC
```
