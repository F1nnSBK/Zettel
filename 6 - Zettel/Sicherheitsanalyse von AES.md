#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Kryptographie]], [[Symmetrische-Kryptographie]]
#it_security

---

### Sicherheitsanalyse von AES

AES gilt heute weltweit als der sicherste symmetrische Verschlüsselungsstandard. In dieser Notiz werden seine Resistenzen sowie die Schwachstellen in echten Systemumgebungen analysiert.

---

#### 1. Mathematische Sicherheit
Bislang gibt es keine bekannten mathematischen oder kryptoanalytischen Angriffe, mit denen AES (in voller Rundenanzahl) signifikant schneller als durch reine Brute-Force-Suche gebrochen werden kann.

* **Brute-Force-Resistenz**:
  * Selbst für AES-128 beträgt der Schlüsselraum $2^{128} \approx 3,4 \cdot 10^{38}$ Schlüssel.
  * Ein Supercomputer, der $10^{18}$ Schlüssel pro Sekunde prüfen könnte, bräuchte etwa $10^{13}$ Jahre (das Tausendfache des Alters des Universums), um den Schlüsselraum zu durchsuchen.
* **Resistenz gegen Kryptoanalyse**: Das mathematische Design der S-Box (multiplikative Inversion) bietet optimalen Schutz gegen differenzielle und lineare Kryptoanalyse.

---

#### 2. Seitenkanalangriffe (Side-Channel Attacks)
Obwohl AES mathematisch sicher ist, können unsichere Implementierungen in Software oder Hardware Angreifern Angriffsflächen bieten. Seitenkanalangriffe nutzen physische Nebenwirkungen des Verschlüsselungsprozesses:

##### A. Zeitmessungs-Angriffe (Timing Attacks)
* **Problem**: Viele Software-Implementierungen nutzen vorberechnete Tabellen (Lookup Tables) im RAM für die S-Box-Zugriffe, um die Berechnung zu beschleunigen.
* **Schwachstelle**: Da der Zugriff auf den CPU-Cache schneller ist als auf den Hauptspeicher (RAM), variiert die Zugriffszeit in Abhängigkeit von den verarbeiteten Schlüssel- und Datenteilen (Cache Misses). Ein Angreifer kann diese winzigen Zeitunterschiede messen und den Schlüssel extrahieren.

##### B. Leistungsanalyse (SPA/DPA - Simple/Differential Power Analysis)
* **Problem**: Mikrochips (z. B. in Smartcards) verbrauchen je nach verarbeitetem Bit (0 oder 1) unterschiedlich viel elektrischen Strom.
* **Schwachstelle**: Durch Messung des Stromverbrauchs während der Verschlüsselung können Angreifer direkt auf die Schlüsselbits schließen.

---

#### 3. Gegenmaßnahmen
* **Hardware-Beschleunigung**: Moderne CPUs besitzen integrierte Befehlssätze (z. B. **Intel AES-NI**), die die S-Box-Operationen direkt in Hardware in konstanter Zeit ausführen. Dies eliminiert Timing-Angriffe vollständig.
* **Maskierung (Masking)**: Zufällige Werte werden vor den Berechnungen mit den Daten verknüpft (XOR) und am Ende wieder herausgerechnet. Dadurch ist der Stromverbrauch unabhängig vom tatsächlichen Schlüssel.

---
#### Flashcards

Warum ist ein mathematischer Brute-Force-Angriff auf AES-128 unmöglich?::Weil der Schlüsselraum von $2^{128}$ so gigantisch ist, dass selbst modernste Supercomputer Milliarden Jahre bräuchten, um alle Schlüssel auszuprobieren.

Wie funktioniert ein Timing-Seitenkanalangriff auf AES?::Der Angreifer misst geringfügige Unterschiede in der Rechenzeit (verursacht durch Cache-Zugriffe bei S-Box-Tabellenlookups), um Rückschlüsse auf den Schlüssel zu ziehen.

Wie schützt Hardware-Unterstützung (z. B. Intel AES-NI) vor Seitenkanalangriffen?::Sie führt die AES-Operationen direkt in den CPU-Registern in konstanter Zeit aus, wodurch keine Cache-abhängigen Zeitunterschiede entstehen.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Sicherheitsanalyse von AES]]
SORT file.mtime DESC
```
