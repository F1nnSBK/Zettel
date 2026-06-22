#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Incident-Response]]
#it_security

---

### MITRE Frameworks

Die **MITRE-Frameworks** (insbesondere **ATT&CK** und **D3FEND**) sind standardisierte Wissensdatenbanken der Sicherheitsforschung, die zur Modellierung von Angriffspfaden und zur Planung defensiver Sicherheitsarchitekturen genutzt werden.

---

#### 1. MITRE ATT&CK (Adversary Tactics, Techniques, and Common Knowledge)
* **Definition**: Eine freie, globally zugängliche Matrix, die das Verhalten von Angreifern basierend auf realen Beobachtungen kategorisiert.
* **Struktur**:
  * **Tactics (Taktiken)**: Das "Warum" des Angreifers (die Ziele, z. B. *Initial Access* für den Einbruch, *Credential Access* für den Diebstahl von Passwörtern, *Exfiltration* für den Datenabfluss).
  * **Techniques (Techniken)**: Das "Wie" (die Methode, z. B. *Spearphishing Attachment* unter Initial Access).
  * **Procedures (Abläufe)**: Die konkrete Implementierung durch eine bestimmte Hacker-Gruppe (z. B. APT28 nutzt Tool X auf Weise Y).

---

#### 2. MITRE D3FEND (Detection, Denial, and Disruption Framework)
* **Definition**: Das komplementäre Gegenstück zu ATT&CK, das sich ausschließlich auf **defensive Sicherheitsmaßnahmen** (Countermeasures) konzentriert.
* **Struktur**: Es kategorisiert Abwehrmethoden in Gruppen wie:
  * *Model* (z. B. Asset-Katalogisierung)
  * *Detect* (z. B. Dateianalyse, Netzwerküberwachung)
  * *Isolate* (z. B. Sandboxing, Netzwerksegmentierung)
  * *Deceive* (z. B. Honeypots)
  * *Evict* (z. B. Session-Beendigung)

---

#### 🤝 Das Zusammenspiel in der Verteidigung
* **ATT&CK** dient zur Bedrohungsanalyse: *"Welche Techniken nutzen Angreifer in unserer Branche, um Passwörter zu stehlen?"*
* **D3FEND** liefert die passenden Abwehrmaßnahmen: *"Welche technischen Kontrollen müssen wir implementieren, um diese Techniken zu blockieren oder zu erkennen?"*
* Durch die Verknüpfung beider Frameworks können Unternehmen Sicherheitslücken (Gaps) in ihrer Verteidigung systematisch aufdecken und gezielt schließen.

**Verknüpfte Zettel:**
- [[Angriffskategorien]] (Grundlagen der Angriffsarten)

---
#### Flashcards

Was versteht man unter dem MITRE ATT&CK-Framework?::Eine weltweit standardisierte Wissensdatenbank, die reale Angriffstaktiken, -techniken und -prozeduren von Cyberkriminellen systematisch erfasst.

Wie grenzen sich MITRE ATT&CK und D3FEND voneinander ab?::MITRE ATT&CK beschreibt die Angriffstechniken (Offensiv-Sicht); MITRE D3FEND strukturiert die defensiven Abwehrmaßnahmen (Defensiv-Sicht).

Was beschreibt eine Taktik (Tactic) im MITRE ATT&CK-Framework?::Das taktische Ziel des Angreifers in einer bestimmten Phase des Angriffs (z. B. Erlangen von Erstzugang oder Ausspähen von Passwörtern).

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[MITRE Frameworks]]
SORT file.mtime DESC
```
