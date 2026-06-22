#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Kryptographie]], [[Betriebsmodi]]
#it_security

---

### Stromchiffren-Modi und CTR

Einige Betriebsmodi ermöglichen es, eine Blockchiffre so zu betreiben, dass sie sich wie eine [[Stromchiffren|Stromchiffre]] verhält. 
* **Vorteil**: Da der Klartext bitweise mit dem Schlüsselstrom per XOR verknüpft wird, ist **kein Padding** notwendig. Jede beliebige Dateilänge kann exakt verschlüsselt werden.

---

#### 1. CFB-Modus (Cipher Feedback)
Der Geheimtext des vorherigen Blocks wird als Input für die Verschlüsselung genutzt, um den nächsten Teil des Schlüsselstroms zu generieren.
* **Verschlüsselung**: $c_i = m_i \oplus E_k(c_{i-1}) \quad (\text{mit } c_{-1} = IV)$
* **Entschlüsselung**: $m_i = c_i \oplus E_k(c_{i-1})$

---

#### 2. OFB-Modus (Output Feedback)
Der Schlüsselstrom wird generiert, indem das Ergebnis der vorherigen Verschlüsselung erneut verschlüsselt wird (Feedback-Schleife). Er ist unabhängig vom Klar- und Geheimtext.
* **Keystream**: $s_0 = E_k(IV)$ und $s_i = E_k(s_{i-1})$
* **Verschlüsselung**: $c_i = m_i \oplus s_i$
* **Entschlüsselung**: $m_i = c_i \oplus s_i$

---

#### 3. CTR-Modus (Counter Mode)
Der CTR-Modus verschlüsselt einen fortlaufenden Zählerwert (Counter), um den Schlüsselstrom zu erzeugen. Er ist heute der am häufigsten genutzte Stromchiffren-Modus.

##### Funktionsweise
* **Zählerwert**: Setzt sich meist aus einer einmaligen Zufallszahl (**Nonce**, z. B. 64 Bit) und einem fortlaufenden Blockzähler (z. B. 64 Bit) zusammen:
  $$\text{Counter}_i = \text{Nonce} \parallel i$$
* **Verschlüsselung**: $c_i = m_i \oplus E_k(\text{Counter}_i)$
* **Entschlüsselung**: $m_i = c_i \oplus E_k(\text{Counter}_i)$

```
Counter 1 ──► [ Enc ] ──► (⊕) ──► Geheimtext C1
                ▲          ▲
                │          │
           Schlüssel K   Klartext M1

Counter 2 ──► [ Enc ] ──► (⊕) ──► Geheimtext C2
                ▲          ▲
                │          │
           Schlüssel K   Klartext M2
```

##### Die Vorteile des CTR-Modus
* **Vollständige Parallelisierbarkeit**: Sowohl Verschlüsselung als auch Entschlüsselung können komplett parallel verarbeitet werden, da alle Zählerwerte ($\text{Counter}_i$) unabhängig im Voraus berechnet werden können.
* **Random Access**: Man kann Block $i$ entschlüsseln, ohne die Blöcke $0 \dots i-1$ berechnen zu müssen (wichtig für den Dateizugriff auf Festplatten).

##### ⚠️ Die gravierende Schwachstelle (Counter-Reuse)
* Wenn ein Zählerwert für denselben Schlüssel jemals wiederverwendet wird, entsteht exakt das Problem der Keystream-Wiederverwendung (siehe [[Angriffe auf Stromchiffren]]). Die Chiffre bricht sofort zusammen.

**Verknüpfte Zettel:**
- [[Stromchiffren]] (Verhalten des resultierenden Schlüsselstroms)
- [[Angriffe auf Stromchiffren]] (Gefahr des Keystream-Reuse bei Zählerduplikaten)

---
#### Flashcards

Wie wird im Counter (CTR)-Modus der Schlüsselstrom erzeugt?::Indem ein eindeutiger Zählerwert (bestehend aus Nonce und Blockzähler) mit dem geheimen Schlüssel verschlüsselt wird: $s_i = E_k(\text{Counter}_i)$.

Welche zwei Performance-Vorteile hat der CTR-Modus gegenüber dem CBC-Modus?::Er ist voll parallelisierbar (sowohl beim Verschlüsseln als auch beim Entschlüsseln) und erlaubt wahlfreien Zugriff (Random Access) auf beliebige Datenblöcke.

Welcher schwerwiegende Fehler muss bei der Implementierung des CTR-Modus vermieden werden?::Die Wiederverwendung eines Zählerwerts (Nonce + Zähler) mit demselben Schlüssel, da dies zum vollständigen Verlust der Vertraulichkeit führt.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Stromchiffren-Modi und CTR]]
SORT file.mtime DESC
```
