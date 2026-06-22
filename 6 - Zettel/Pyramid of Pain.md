#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Incident-Response]]
#it_security

---

### Pyramid of Pain

Die **Pyramid of Pain** (entwickelt von David Bianco) ist ein Konzept der Cyber-Security, das beschreibt, wie viel Aufwand (Schmerz) ein Angreifer betreiben muss, um seine Taktik zu ändern, wenn ein Verteidiger bestimmte Angriffsindikatoren (**Indicators of Compromise - IoCs**) erkennt und blockiert.

```
          /\  TTPs (Taktiken, Techniken, Abläufe) -> Extrem schmerzhaft
         /  \ 
        /----\ Tools (Werkzeuge) -> Sehr schmerzhaft
       /      \ 
      /--------\ Netzwerk-/Host-Artefakte -> Lästig
     /          \ 
    /------------\ Domainnamen -> Einfach
   /              \ 
  /----------------\ IP-Adressen -> Sehr einfach
 /                  \ 
/--------------------\ Hashwerte -> Trivial (Kein Schmerz)
```

---

#### Die Ebenen der Pyramide

##### 1. Hashwerte (Hash Values) – Trivial
* **Beispiel**: MD5/SHA-256 einer Malware-Datei.
* **Schmerz für den Angreifer**: Keiner. Schon das Ändern eines einzigen Bits in der Malware erzeugt einen völlig neuen Hashwert.

##### 2. IP-Adressen (IP Addresses) – Sehr einfach
* **Beispiel**: IP-Adresse des Command-and-Control (C2) Servers.
* **Schmerz für den Angreifer**: Minimal. Der Angreifer kann schnell über Proxys, VPNs oder kurzlebige Server eine neue IP-Adresse beziehen.

##### 3. Domainnamen (Domain Names) – Einfach
* **Beispiel**: Gefälschte Domains für Phishing oder C2-Kommunikation (z. B. `update-microsoft.com`).
* **Schmerz für den Angreifer**: Gering. Domains müssen registriert und bezahlt werden, was etwas Aufwand erfordert. Angreifer nutzen oft dynamisches DNS (DDNS) oder Domain Generation Algorithms (DGAs).

##### 4. Netzwerk- und Host-Artefakte (Network & Host Artifacts) – Lästig (Annoying)
* **Beispiel**: Spezifische User-Agent-Strings im HTTP-Header der Malware, feste Registry-Einträge auf dem infizierten Rechner.
* **Schmerz für den Angreifer**: Spürbar. Der Angreifer muss seine Malware modifizieren oder konfigurieren, um diese Erkennungsmerkmale zu entfernen.

##### 5. Tools (Werkzeuge) – Sehr schmerzhaft (Challenging)
* **Beispiel**: Einsatz bekannter Hackertools wie *Mimikatz* oder *Cobalt Strike*.
* **Schmerz für den Angreifer**: Hoch. Wenn das Tool blockiert wird, muss der Angreifer ein neues Werkzeug schreiben, kaufen oder lernen, es zu bedienen.

##### 6. TTPs (Tactics, Techniques, and Procedures) – Extrem schmerzhaft
* **Beispiel**: Die grundlegende Vorgehensweise des Angreifers (z. B. wie er sich im Netz lateral bewegt, Passwörter abgreift).
* **Schmerz für den Angreifer**: Maximal. TTPs spiegeln das Verhalten und das Training des Angreifers wider. Diese zu ändern erfordert ein komplettes Umdenken und Umschulen der Angreifer-Teams.

---

#### ⚖️ Relevanz für die Verteidigung
* **Traditionelle Abwehr** (Firewall, AV) arbeitet meist an der Basis (Hashes, IPs). Das ist ineffektiv gegen zielgerichtete Angreifer.
* **Moderne Abwehr** (Threat Intelligence, EDR, SIEM) versucht, TTPs an der Spitze der Pyramide zu erkennen (z. B. "Verdächtiges Verhalten von PowerShell"). Erkennt man TTPs, blockiert man den Angreifer nachhaltig.

**Verknüpfte Zettel:**
- [[Hashfunktionen]] (Grundlagen zu Hashwerten)

---
#### Flashcards

Was beschreibt die Pyramid of Pain?::Sie visualisiert, wie viel Aufwand (Schmerz) ein Angreifer betreiben muss, wenn ein Verteidiger bestimmte Angriffsindikatoren (IoCs) blockiert.

Welcher Indikator ist für den Angreifer am einfachsten zu ändern?::Der Hashwert der Datei (Änderung eines Bits reicht aus).

Warum ist die Erkennung von TTPs für die Verteidigung am wertvollsten?::Weil sie das tatsächliche Verhalten des Angreifers beschreiben. Werden TTPs blockiert, muss der Angreifer seine gesamte Arbeitsweise neu erlernen und anpassen (maximaler Schmerz).

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Pyramid of Pain]]
SORT file.mtime DESC
```
