#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Kryptographie]], [[Asymmetrische-Kryptographie]]
#it_security

---

### Sicherheit und Angriffe auf DHKE

Obwohl [[Diffie-Hellman Key Exchange|DHKE]] mathematisch stark ist, ist das Basisprotokoll in realen Netzwerken ohne zusätzliche Schutzmaßnahmen verwundbar.

---

#### 1. Der Man-in-the-Middle-Angriff (MitM)
Das größte Problem des klassischen DHKE ist das **Fehlen von Authentizität**. Die Kommunikationspartner können nicht prüfen, wer am anderen Ende der Leitung sitzt.

##### Ablauf des Angriffs
Ein aktiver Angreifer (Mallory) schaltet sich in den Datenfluss zwischen Alice und Bob:
```
  Alice (a)                  Mallory (x, y)                   Bob (b)
  ─────────                  ──────────────                   ───────
  A = α^a ──►                Fängt A ab
                             Generiert: A_M = α^x
                             Schickt A_M an Bob ────────────► Fängt A_M ab
                             
  Fängt B_M ab ◄──────────── Generiert: B_M = α^y
                             Fängt B ab ◄──────────────────── B = α^b
                             
  Berechnet:                 Berechnet:                       Berechnet:
  s_1 = (B_M)^a              s_1 = A^y (Key mit Alice)        s_2 = (A_M)^b
                             s_2 = B^x (Key mit Bob)          s_2 = (A_M)^b (Key mit Bob)
```

##### Konsequenz
* Alice glaubt, einen Schlüssel mit Bob vereinbart zu haben (nutzt tatsächlich $s_1$).
* Bob glaubt, einen Schlüssel mit Alice vereinbart zu haben (nutzt tatsächlich $s_2$).
* Mallory besitzt beide Schlüssel. Sie entschlüsselt Alice' Nachrichten mit $s_1$, liest/modifiziert sie, verschlüsselt sie mit $s_2$ und leitet sie an Bob weiter.
* **Gegenmaßnahme**: Authentifizierung der DHKE-Schlüssel mittels **digitaler Signaturen** (z. B. durch Zertifikate in TLS/HTTPS).

---

#### 2. Forward Secrecy (Perfect Forward Secrecy - PFS)
**Forward Secrecy** ist ein wichtiges Sicherheitsmerkmal in modernen Protokollen (wie TLS 1.3). Es stellt sicher, dass das Aufzeichnen von verschlüsseltem Datenverkehr über Jahre hinweg nutzlos bleibt, selbst wenn der Angreifer in der Zukunft den privaten Schlüssel des Servers stiehlt.

##### Ephemeral Diffie-Hellman (DHE / ECDHE)
* **Klassischer Schlüsselaustausch (RSA)**: Wenn der Server-Key gestohlen wird, können alle in der Vergangenheit aufgezeichneten Sessions entschlüsselt werden, da die Session-Keys mit dem Server-Key verschlüsselt waren.
* **Mit Ephemeral DH**: Für *jede einzelne Session* generieren die Parteien temporäre (ephemere) DH-Schlüssel $a$ und $b$. Diese werden unmittelbar nach dem Verbindungsaufbau aus dem Arbeitsspeicher gelöscht.
* **Ergebnis**: Ein Diebstahl des langfristigen Server-Zertifikats erlaubt nur die zukünftige Authentifizierung (Identitätsdiebstahl), nicht aber das Entschlüsseln aufgezeichneter historischer Daten, da die zugehörigen ephemeren Schlüssel längst gelöscht wurden.

**Verknüpfte Zettel:**
- [[Diffie-Hellman Key Exchange]] (Mathematische Funktionsweise)

---
#### Flashcards

Warum schützt ein reines DHKE-Protokoll nicht vor einem Man-in-the-Middle-Angriff?::Weil das Protokoll keine Authentifizierung bietet. Ein Angreifer kann sich unbemerkt als Partner ausgeben und mit beiden Seiten eigene DHKE-Schlüssel vereinbaren.

Wie kann man einen Man-in-the-Middle-Angriff auf DHKE verhindern?::Indem die öffentlichen DH-Parameter (A und B) vor der Übertragung digital signiert und zertifiziert werden (z. B. über TLS/HTTPS-Zertifikate).

Welche Eigenschaft garantiert Perfect Forward Secrecy (PFS)?::Dass die Kompromittierung des langfristigen privaten Schlüssels in der Zukunft nicht dazu führt, dass zuvor aufgezeichneter Datenverkehr entschlüsselt werden kann.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Sicherheit und Angriffe auf DHKE]]
SORT file.mtime DESC
```
