#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Kryptographie]], [[Stromchiffren]]
#it_security

---

### Beispiele für Stromchiffren: RC4, A5/1 & Trivium

Es existieren verschiedene Architekturen zur Erzeugung von Schlüsselströmen. Die drei bekanntesten Beispiele zeigen die Evolution von Hardware- und Software-basierten Ansätzen.

---

#### 1. A5/1 (GSM-Verschlüsselung)
* **Design**: Hardware-orientiert. Basiert auf drei **Linear Feedback Shift Registers (LFSR)** mit unterschiedlichen Längen (19, 22 und 23 Bit).
* **Steuerung**: Über ein Taktungsverfahren (Majority Voting System).
* **Status**: Heute unsicher. Durch die geringe Gesamt-Schlüssellänge von 64 Bit sind Time-Memory Trade-off Angriffe (mittels vorberechneter Rainbow Tables) in Sekunden möglich.

---

#### 2. Trivium (Moderner Hardware-Standard)
* **Design**: Extrem einfaches, leichtgewichtiges Design für Hardware-Implementierungen. Basiert auf drei Schieberegistern mit einer Gesamtlänge von 288 Bit und nichtlinearen Logik-Gattern.
* **Status**: Gilt nach wie vor als sicher und hocheffizient.

---

#### 3. RC4 (Rivest Cipher 4)
* **Design**: Software-orientiert. Extrem einfach und schnell. RC4 arbeitet byte-orientiert und basiert auf einem internen Zustand in Form eines Arrays mit 256 Bytes (S-Box), das durch zwei Zeiger vertauscht wird (Key-Scheduling Algorithm KSA und Pseudo-Random Generation Algorithm PRGA).
* **Schwächen von RC4**:
  * **Statistical Biases**: Die Verteilung der ersten Bytes des Schlüsselstroms ist statistisch nicht gleichverteilt. Beispielsweise ist das zweite Byte mit einer Wahrscheinlichkeit von $\approx 1/128$ gleich Null (doppelt so hoch wie bei perfektem Zufall).
  * **Folge**: Angreifer konnten durch das Abfangen vieler verschlüsselter Verbindungen (z. B. Cookie-Header) Klartextdaten rekonstruieren.
  * **Historischer Impact**: RC4 führte zum Zusammenbruch der WLAN-Sicherheitsstandards WEP und WPA-TKIP.
  * **Gegenmaßnahme**: Zunächst half das Verwerfen der ersten 256 oder 512 Bytes des Keystreams (*RC4-drop*). Heute ist RC4 in TLS und allen modernen Protokollen komplett verboten (RFC 7465).

---
#### Flashcards

In welchem Bereich wurde die Stromchiffre A5/1 eingesetzt und warum ist sie unsicher?::In Mobilfunknetzen (2G/GSM). Sie ist unsicher wegen einer zu geringen effektiven Schlüssellänge von 64 Bit, was Angriffe mit Rainbow Tables erlaubt.

Was ist die mathematische Schwachstelle von RC4?::Der Schlüsselstrom weist statistische Abweichungen (Biases) auf, insbesondere in den ersten Bytes, wodurch Muster des Klartexts rekonstruiert werden können.

Welche WLAN-Standards wurden durch die Schwächen von RC4 unsicher?::WEP und WPA-TKIP.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[RC4 und Stromchiffren-Beispiele]]
SORT file.mtime DESC
```
