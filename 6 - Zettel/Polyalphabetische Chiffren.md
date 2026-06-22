#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Kryptographie]], [[Klassische-Chiffren]]
#it_security

---

### Polyalphabetische Chiffren

Bei einer **polyalphabetischen Substitutionschiffre** wechselt das Substitutionsalphabet von Zeichen zu Zeichen. Dadurch wird die einfache Häufigkeitsanalyse unbrauchbar, da derselbe Klartextbuchstabe an verschiedenen Positionen durch unterschiedliche Geheimtextbuchstaben dargestellt werden kann.

---

#### Die Vigenère-Chiffre
Die bekannteste polyalphabetische Chiffre nutzt ein Schlüsselwort $K$ der Länge $l$.
* **Prinzip**: Der Schlüssel wird periodisch über den Klartext geschrieben. Die Buchstaben werden als Zahlen ($A=0, B=1, \dots$) interpretiert und addiert.
* **Verschlüsselungsformel**:
  $$c_i = (m_i + k_{i \pmod l}) \pmod{26}$$
* **Entschlüsselungsformel**:
  $$m_i = (c_i - k_{i \pmod l}) \pmod{26}$$

---

#### 🔍 Kryptoanalyse: Der Kasiski-Test (Kasiski-Untersuchung)
Obwohl die Vigenère-Chiffre lange als unknackbar galt (*Le Chiffre indéchiffrable*), wurde sie im 19. Jahrhundert durch Friedrich Kasiski systematisch gebrochen.

##### Phase 1: Bestimmung der Schlüssellänge
1. **Mustersuche**: Suche nach sich wiederholenden Buchstabenfolgen (Trigramme oder mehr, z. B. "X Y Z") im Geheimtext.
2. **Abstandsberechnung**: Berechne die Abstände (Anzahl der Zeichen) zwischen den Wiederholungen.
3. **Gemeinsame Teiler**: Da sich Wortteile häufig dann identisch verschlüsseln, wenn sie auf dieselbe Stelle des sich wiederholenden Schlüssels treffen, sind die Abstände meist Vielfache der Schlüssellänge. Der **größte gemeinsame Teiler (ggT)** der Abstände liefert die wahrscheinliche Schlüssellänge $l$.

##### Phase 2: Häufigkeitsanalyse
* Sobald die Schlüssellänge $l$ bekannt ist, zerlegt man den Geheimtext in $l$ getrennte Teiltexte (Teiltext 1 enthält Zeichen $1, 1+l, 1+2l, \dots$; Teiltext 2 enthält Zeichen $2, 2+l, \dots$).
* Jeder dieser Teiltexte wurde mit einer konstanten Verschiebung (monoalphabetisch) verschlüsselt und kann nun einzeln mittels Standard-Häufigkeitsanalyse gebrochen werden.

---
#### Flashcards

Was unterscheidet eine polyalphabetische von einer monoalphabetischen Chiffre?::Polyalphabetische Chiffren wechseln das Substitutionsalphabet basierend auf der Position des Zeichens, sodass ein Klartextbuchstabe zu unterschiedlichen Geheimtextbuchstaben werden kann.

Wie bestimmt der Kasiski-Test die Schlüssellänge einer Vigenère-Verschlüsselung?::Durch Ermittlung des größten gemeinsamen Teilers (ggT) der Abstände zwischen sich wiederholenden Mustern im Geheimtext.

Was macht man, sobald man die Schlüssellänge einer Vigenère-Chiffre kennt?::Man zerlegt den Text in $l$ Teiltexte, die jeweils monoalphabetisch verschlüsselt sind, und bricht diese einzeln mit Häufigkeitsanalyse.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Polyalphabetische Chiffren]]
SORT file.mtime DESC
```
