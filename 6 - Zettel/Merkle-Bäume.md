#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Kryptographie]], [[Hashing]]
#it_security

---

### Merkle-Bäume (Merkle Trees)

Ein **Merkle-Baum** (oder Hash-Baum) ist eine Baumstruktur, in der jeder Blattknoten den Hashwert eines Datenblocks enthält und jeder Elternknoten den kombinierten Hashwert seiner jeweiligen Kindknoten darstellt.

```
                  [ Merkle Root: H_1234 ]
                            /\
                           /  \
                [ H_12 ]          [ H_34 ]
                   /\                /\
                  /  \              /  \
             [ H_1 ]  [ H_2 ]  [ H_3 ]  [ H_4 ]
                │        │        │        │
             [ L_1 ]  [ L_2 ]  [ L_3 ]  [ L_4 ]  <-- Datenblöcke (Transaktionen)
```

---

#### 1. Aufbau und Funktionsweise
In einem binären Merkle-Baum läuft die Konstruktion wie folgt ab:
1. **Blatt-Hashes**: Jeder Datenblock (z. B. eine Transaktion $L_i$) wird einzeln gehasht:
   $$H_1 = H(L_1), \quad H_2 = H(L_2), \quad \dots$$
2. **Kombination**: Die Hashes werden paarweise aneinandergehängt und erneut gehasht:
   $$H_{12} = H(H_1 \parallel H_2)$$
3. **Wurzel (Merkle Root)**: Dieser Prozess wird fortgesetzt, bis nur noch ein einziger Hashwert an der Spitze übrig bleibt:
   $$H_{1234} = H(H_{12} \parallel H_{34})$$

---

#### 2. Vorteile und Effizienz

##### Vertrauensanker (Root Hash)
* Man muss nur dem einzigen Root-Hash (Merkle Root) vertrauen (z. B. durch digitale Signatur gesichert), um die Integrität von Millionen darunterliegenden Datenblöcken zu garantieren.
* Jede nachträgliche Änderung an einem beliebigen Datenblock (z. B. $L_3$) ändert dessen Hash ($H_3$), was die Kette hochwandert und zu einer völlig anderen Merkle Root führt.

##### Effiziente Verifikation (Merkle Proof)
* Um nachzuweisen, dass ein bestimmter Block (z. B. $L_1$) Teil des Baumes ist, muss man nicht den gesamten Baum oder alle Datenblöcke übertragen.
* Es reicht aus, den Pfad zur Wurzel zu rekonstruieren. Dafür benötigt man nur die **Geschwister-Hashes** auf dem Weg nach oben (im Beispiel: $H_2$ und $H_{34}$). Dieser Nachweis wird als *Merkle Proof* oder *Audit Path* bezeichnet.
* **Komplexität**: Die Anzahl der zu sendenden Hashes sinkt von $O(N)$ (bei linearer Prüfung) auf **$O(\log N)$**. Bei einer Million Blöcken müssen zur Verifikation nur 20 Hashes übertragen werden.

---

#### 3. Praxisanwendungen
* **Blockchains (Bitcoin / Ethereum)**: Transaktionen in einem Block werden als Merkle-Baum organisiert. Dies erlaubt es mobilen Clients (SPV - Simple Payment Verification), die Existenz einer Transaktion ressourcenschonend nachzuweisen.
* **Git (Versionsverwaltung)**: Verwaltet Projektdateien als Verzeichnisbaum aus Hashes (Merkle DAG).
* **BitTorrent**: Effiziente Überprüfung, ob einzelne heruntergeladene Dateifragmente beschädigt sind.

**Verknüpfte Zettel:**
- [[Big Data]] (Strukturierung und effiziente Verarbeitung großer Datenmengen)

---
#### Flashcards

Wie ist ein Merkle-Baum aufgebaut?::Die Blätter enthalten Hashes der tatsächlichen Datenblöcke. Die Elternknoten enthalten die kombinierten Hashes ihrer Kindknoten, bis hin zur Wurzel (Merkle Root) an der Spitze.

Warum sind Merkle-Bäume für Peer-to-Peer-Netzwerke (wie BitTorrent) vorteilhaft?::Weil man heruntergeladene Dateifragmente sofort einzeln gegen den bekannten Root-Hash verifizieren kann, ohne die gesamte Datei heruntergeladen haben zu müssen.

Welche mathematische Komplexität hat ein Merkle-Proof zur Verifikation eines Blocks bei $N$ Blättern?::Logarithmische Komplexität: $O(\log N)$.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Merkle-Bäume]]
SORT file.mtime DESC
```
