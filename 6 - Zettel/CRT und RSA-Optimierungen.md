#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Kryptographie]], [[Asymmetrische-Kryptographie]]
#it_security

---

### CRT und RSA-Optimierungen

Die asymmetrische Entschlüsselung und Signaturerstellung mit RSA ist aufgrund der modularen Exponentiation großer Zahlen rechenintensiv. Das **Chinesische Restsatz-Verfahren (Chinese Remainder Theorem - CRT)** ist die wichtigste Methode, um diesen Prozess um den Faktor 3 bis 4 zu beschleunigen.

---

#### 1. Die mathematische Funktionsweise von RSA-CRT
Statt der Berechnung von $m = c^d \pmod n$ spaltet CRT den Prozess in zwei Berechnungen über die kleineren Moduln $p$ und $q$ auf.

##### Vorbereitung (Schlüsselerzeugung)
Zusätzlich zu $d$ werden bei der Schlüsselerzeugung folgende Werte vorberechnet und im privaten Schlüssel gespeichert:
* $d_p = d \pmod{p-1}$
* $d_q = d \pmod{q-1}$
* $q_{\text{inv}} = q^{-1} \pmod p$

##### Ablauf der Entschlüsselung
1. **Reduzierte Exponentiation**:
   $$m_p = c^{d_p} \pmod p$$
   $$m_q = c^{d_q} \pmod q$$
2. **Kombination (nach Garner's Formel)**:
   $$h = q_{\text{inv}} \cdot (m_p - m_q) \pmod p$$
   $$m = m_q + h \cdot q$$

##### Warum ist das schneller?
* Die Komplexität der modularen Exponentiation wächst kubisch ($O(k^3)$) mit der Bitlänge $k$.
* Wenn man eine 2048-Bit-Berechnung in zwei 1024-Bit-Berechnungen aufteilt, halbiert sich die Bitlänge. 
* Da $(1/2)^3 = 1/8$, benötigt jede Teilberechnung nur ca. 1/8 der Zeit einer Vollberechnung. Für beide Teilberechnungen zusammen benötigt man also $2 \cdot 1/8 = 1/4$ der Zeit. Dies entspricht einem theoretischen **Geschwindigkeitsvorteil von Faktor 4**.

---

#### 2. Der Bellcore-Angriff (Fault Attack / Fehlerangriff)
Die Verwendung von CRT birgt ein erhebliches physisches Sicherheitsrisiko bei Hardware-Implementierungen (z. B. in Smartcards).

* **Das Szenario**: Ein Angreifer provoziert während der Signaturerstellung (z. B. durch Induzieren von Spannungsschwankungen oder Laserstrahlung) gezielt einen Berechnungsfehler.
* **Die Schwachstelle**: Wenn bei der CRT-Berechnung nur eine der beiden Hälften ($m_p$ oder $m_q$) fehlerhaft berechnet wird, ist auch die kombinierte Signatur $s'$ fehlerhaft.
* **Der Bruch**: Aus der fehlerhaften Signatur $s'$ und der korrekten Signatur $s$ (oder der Originalnachricht $m$) kann der Angreifer den geheimen Primfaktor $p$ über eine einfache Berechnung des größten gemeinsamen Teilers (ggT) extrahieren:
  $$p = \text{ggT}(s'^e - m, n)$$
  Sobald $p$ bekannt ist, ist RSA vollständig gebrochen.
* **Gegenmaßnahme**: Die berechnete Signatur muss vor dem Senden verifiziert werden (durch erneutes Verschlüsseln mit dem öffentlichen Schlüssel $e$). Stimmt das Ergebnis nicht mit der Nachricht überein, wird die Ausgabe blockiert.

**Verknüpfte Zettel:**
- [[RSA-Verfahren]] (Grundlegendes mathematisches Konzept)

---
#### Flashcards

Wie beschleunigt das Chinesische Restsatz-Verfahren (CRT) die RSA-Berechnung?::Es spaltet die Exponentiation modulo $n$ in zwei Berechnungen modulo $p$ und $q$ auf, was die Bitlänge halbiert und Berechnungen um den Faktor 3 bis 4 beschleunigt.

Was ist ein Bellcore-Angriff auf RSA-CRT?::Ein physischer Fehlerangriff (Fault Attack). Ein induzierter Berechnungsfehler in einer CRT-Hälfte ermöglicht es dem Angreifer, über eine ggT-Berechnung den privaten Primfaktor $p$ zu extrahieren.

Wie kann man eine Smartcard gegen Bellcore-Angriffe absichern?::Indem die Smartcard die berechnete Signatur vor der Herausgabe selbst mit dem öffentlichen Schlüssel verifiziert und bei Fehlern die Ausgabe verweigert.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[CRT und RSA-Optimierungen]]
SORT file.mtime DESC
```
