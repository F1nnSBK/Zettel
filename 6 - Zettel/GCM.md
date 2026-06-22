#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Kryptographie]], [[Betriebsmodi]]
#it_security

---

### Galois/Counter Mode (GCM)

Der **Galois/Counter Mode (GCM)** ist ein hochperformanter Betriebsmodus für symmetrische Blockchiffren. Er gehört zur Klasse der **AEAD-Modi** (Authenticated Encryption with Associated Data).

---

#### 1. Die Notwendigkeit von AEAD
Standardmodi wie CBC oder CTR schützen nur das Schutzziel der **Vertraulichkeit**. Sie schützen **nicht** vor Manipulationen der Daten während der Übertragung:
* **Angriffsfläche (Bit-Flipping)**: Im CTR-Modus führt das Flippen eines Geheimtextbits beim Empfänger dazu, dass exakt dasselbe Bit im Klartext kippt. Der Empfänger bemerkt die Manipulation nicht, sondern erhält verfälschte Daten.
* **Lösung**: AEAD-Verfahren kombinieren Verschlüsselung (Vertraulichkeit) und einen Integritätsnachweis (Authentizität) in einem einzigen Schritt.

---

#### 2. Funktionsweise von GCM
GCM kombiniert zwei Kernkomponenten:

```
Klartext ──► [ CTR-Modus (AES) ] ──► Geheimtext ──┐
                                                 ▼
Zusatzdaten (AD) ───────────────────────────► [ GMAC (GF(2^128)) ] ──► Auth-Tag (MAC)
```

1. **Verschlüsselung (CTR-Modus)**: Der Klartext wird über den schnellen, parallelisierbaren Counter-Modus verschlüsselt.
2. **Authentifizierung (GMAC)**: Der Geheimtext (und optionale unverschlüsselte Zusatzdaten) wird durch eine polynomiale Hash-Funktion im Galois-Körper $GF(2^{128})$ verarbeitet. Das Ergebnis ist ein eindeutiger kryptographischer Prüfwert, der **Authentication Tag (Auth-Tag)**.

##### Was sind Associated Data (AD)?
* Dies sind Begleitdaten, die im Klartext übertragen werden müssen (z. B. IP-Adressen in Netzwerk-Headern, damit Router das Paket weiterleiten können), aber dennoch gegen Manipulation geschützt sein sollen.
* GCM stellt sicher, dass der Empfänger merkt, wenn die IP-Adressen im Header verändert wurden, obwohl sie unverschlüsselt waren.

---

#### 3. Vorteile von GCM
* **Herausragende Performance**: Sowohl der CTR-Modus als auch die GMAC-Berechnung können vollständig parallelisiert werden.
* **Hardware-Unterstützung**: Moderne CPUs besitzen spezielle Instruktionen (z. B. CLMUL bei Intel), um die Multiplikation im Galois-Körper extrem schnell in Hardware auszuführen.
* **Standard**: GCM ist der Standard-Verschlüsselungsmodus in modernen Protokollen wie TLS 1.3 und IPSec.

**Verknüpfte Zettel:**
- [[CIA-Triade]] (Gleichzeitiger Schutz von Vertraulichkeit und Integrität)

---
#### Flashcards

Wofür steht das Akronym GCM?::Galois/Counter Mode.

Welche beiden Schutzziele der CIA-Triade löst GCM zeitgleich?::Vertraulichkeit (durch Verschlüsselung im CTR-Modus) und Integrität (durch Erzeugung des Galois-basierten Auth-Tags).

Warum ist die Integritätssicherung bei Netzwerkprotokollen so wichtig?::Weil Angreifer sonst gezielte Bit-Flipping-Angriffe auf den Geheimtext durchführen könnten, um z. B. Zieladressen oder Geldbeträge zu manipulieren, ohne dass der Empfänger es bemerkt.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[GCM]]
SORT file.mtime DESC
```
