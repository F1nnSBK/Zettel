#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Kryptographie]], [[Stromchiffren]]
#it_security

---

### Angriffe auf Stromchiffren

Stromchiffren sind bei korrekter Verwendung sehr sicher. Sie reagieren jedoch extrem empfindlich auf Implementierungsfehler. Die zwei verheerendsten Angriffszenarien werden hier beschrieben.

---

#### 1. Wiederverwendung des Schlüsselstroms (Keystream Reuse / Two-Time Pad)
Der schwerste Implementierungsfehler bei Stromchiffren ist die Wiederverwendung desselben Schlüsselstroms (erzeugt aus demselben Key und IV) für zwei verschiedene Nachrichten.

##### Der mathematische Bruch
Ein Angreifer fängt zwei Geheimtexte $c_1$ und $c_2$ ab, die mit demselben Schlüsselstrom $s$ verschlüsselt wurden:
$$c_1 = m_1 \oplus s$$
$$c_2 = m_2 \oplus s$$

Der Angreifer verknüpft nun die beiden Geheimtexte mittels XOR:
$$c_1 \oplus c_2 = (m_1 \oplus s) \oplus (m_2 \oplus s)$$
$$c_1 \oplus c_2 = m_1 \oplus m_2 \oplus s \oplus s \quad (\text{da } s \oplus s = 0)$$
$$c_1 \oplus c_2 = m_1 \oplus m_2$$

##### Konsequenz
* Der Schlüsselstrom wurde vollständig eliminiert.
* Der Angreifer erhält das XOR-Produkt der beiden Klartexte $m_1 \oplus m_2$.
* Da natürliche Sprachen eine hohe Redundanz aufweisen, lassen sich die beiden Klartexte über statistische Analysen (z. B. *Crib Dragging* – Durchschieben wahrscheinlicher Wörter) extrem leicht voneinander trennen.

---

#### 2. Known-Plaintext-Angriff (KPA)
Bei Stromchiffren führt die Kenntnis eines Klartextabschnitts sofort zur Offenlegung des genutzten Schlüsselstroms an dieser Position.
* **Ablauf**: 
  * Der Angreifer kennt einen Teil der Nachricht $m$ (z. B. Standard-Header wie `GET / HTTP/1.1`) und den zugehörigen Geheimtext $c$.
  * Er berechnet:
    $$s = c \oplus m$$
  * Kennt er den Schlüsselstrom $s$, kann er jede andere Nachricht entschlüsseln, die mit demselben Schlüsselstrom verschlüsselt wurde.
* **Schutz**: Jede Nachricht muss einen eindeutigen **Initialisierungsvektor (IV)** verwenden, damit auch bei gleichem Key immer ein neuer Keystream generiert wird.

**Verknüpfte Zettel:**
- [[One-Time-Pad]] (Gleiche Angreifbarkeit bei Schlüsselwiederverwendung)

---
#### Flashcards

Was passiert mathematisch, wenn zwei Geheimtexte mit demselben Schlüsselstrom XOR-verknüpft werden?::Der Schlüsselstrom kürzt sich heraus und der Angreifer erhält das XOR-Produkt der Klartexte: $c_1 \oplus c_2 = m_1 \oplus m_2$.

Wie kann ein Angreifer bei einer Stromchiffre den Schlüsselstrom ermitteln, wenn er einen Teil des Klartexts kennt?::Indem er den bekannten Klartextteil mit dem entsprechenden Geheimtextteil XOR-verknüpft: $s = c \oplus m$ (Known-Plaintext-Angriff).

Welcher Parameter verhindert die Wiederverwendung desselben Schlüsselstroms bei gleichem Schlüssel?::Ein eindeutiger, für jede Nachricht wechselnder **Initialisierungsvektor (IV)**.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Angriffe auf Stromchiffren]]
SORT file.mtime DESC
```
