#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Kryptographie]], [[Betriebsmodi]]
#it_security

---

### Vergleich der Betriebsmodi

Blockchiffren können je nach Anwendungsfall in unterschiedlichen Betriebsmodi eingesetzt werden. Diese Notiz vergleicht die Eigenschaften und Einsatzzwecke der wichtigsten Modi.

---

#### 1. Vergleichstabelle

| Modus | IV benötigt? | Padding nötig? | Parallelisierbar? | Fehlerfortpflanzung (Bitfehler) | Integritätsschutz? |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **ECB** | Nein | Ja | Ja (Verschl. & Entschl.) | Nur im betroffenen Block | Nein |
| **CBC** | Ja | Ja | Nur Entschlüsselung | Betroffener Block zerstört, nächster Block hat Bitfehler | Nein |
| **CFB** | Ja | Nein | Nur Entschlüsselung | Betroffener Block hat Bitfehler, nächster Block zerstört | Nein |
| **OFB** | Ja | Nein | Nein | Nur das korrespondierende Bit | Nein |
| **CTR** | Ja | Nein | Ja (Verschl. & Entschl.) | Nur das korrespondierende Bit | Nein |
| **GCM** | Ja | Nein | Ja (Verschl. & Entschl.) | Nein (Entschlüsselung bricht bei Fehler komplett ab) | **Ja** (AEAD) |

---

#### 2. Fehlerfortpflanzung (Error Propagation)
Tritt bei der Übertragung des Geheimtexts ein Bitfehler auf, hat dies je nach Modus unterschiedliche Folgen bei der Entschlüsselung:
* **CBC-Modus**: 
  * Ein gekipptes Bit in Block $c_i$ führt dazu, dass der Klartextblock $m_i$ bei der Entschlüsselung vollständig zerstört wird (Datenmüll).
  * Im darauffolgenden Block $m_{i+1}$ kippt exakt das Bit an derselben Position, an der der Fehler in $c_i$ auftrat. Danach stabilisiert sich das System wieder.
* **CTR- und OFB-Modus**:
  * Da sie wie Stromchiffren arbeiten, pflanzt sich ein Fehler nicht fort. Ein gekipptes Bit in $c_i$ führt lediglich dazu, dass exakt das entsprechende Bit im Klartextblock $m_i$ kippt.

---

#### 3. Anwendungsempfehlungen
* **Für Netzwerkverbindungen (TLS, IPSec)**: **GCM** ist der Standard, da er Vertraulichkeit und Schutz vor aktiven Manipulationen (Integrität) garantiert.
* **Für Festplattenverschlüsselung (z. B. BitLocker)**: XTS-AES (eine Variante des CTR-Modus), da hier wahlfreier Zugriff (Random Access) auf Sektoren zwingend notwendig ist.
* **Für Datenbanken**: **CTR-Modus**, wenn Performance und wahlfreier Zugriff im Vordergrund stehen (Padding-Oracles werden dadurch vermieden).

**Verknüpfte Zettel:**
- [[Datenbanken]] (Relevanz von Random Access und Verschlüsselung)
- [[CIA-Triade]] (Schutzziele und deren Erfüllung durch die Modi)

---
#### Flashcards

Wie wirkt sich ein einzelner Bitfehler im Geheimtext bei der Entschlüsselung im CBC-Modus aus?::Der betroffene Block wird komplett zerstört und im nächsten Block kippt das Bit an derselben Stelle. Danach läuft die Entschlüsselung fehlerfrei weiter.

Warum sollte man für Netzwerkverbindungen GCM statt CBC oder CTR wählen?::Weil GCM ein AEAD-Modus ist und somit die Integrität der Pakete garantiert, während CBC und CTR anfällig für Bit-Flipping-Angriffe sind.

In welchen Betriebsmodi ist die Verschlüsselung parallelisierbar?::In ECB, CTR und GCM (da die Blöcke unabhängig voneinander verschlüsselt werden können).

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Vergleich der Betriebsmodi]]
SORT file.mtime DESC
```
