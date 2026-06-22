#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Incident-Response]], [[Grundlagen]]
#it_security

---

### Incident Response (IR)

**Incident Response (IR)** beschreibt den strukturierten Prozess, mit dem eine Organisation auf Sicherheitsvorfälle (Incidents) reagiert, um Schäden zu begrenzen und den Normalbetrieb schnellstmöglich wiederherzustellen.

---

#### 🔄 Der Paradigmenwechsel: Von Prävention zu Reaktion
Traditionell lag der Fokus der IT-Sicherheit fast ausschließlich auf der **Prävention** (Firewalls, Virenschutz, Abschottung). 

In der modernen Cyber-Security hat ein Paradigmenwechsel stattgefunden:
* **Prävention ist notwendig, aber nicht ausreichend**: Angesichts hochgradig professioneller Angreifer und Zero-Day-Exploits gilt der Grundsatz **"Assume Breach"** (Gehe davon aus, dass du bereits kompromittiert bist oder kompromittiert wirst).
* **Fokus Reaktion**: Die Fähigkeit, einen laufenden Angriff schnellstmöglich zu **erkennen**, **einzudämmen** (Containment) und zu **bereinigen** (Eradication), ist entscheidend, um existenzbedrohende Schäden zu verhindern.

---

#### ⚖️ Abgrenzung: Incident Response vs. IT-Forensik
Obwohl eng miteinander verzahnt, haben IR und IT-Forensik unterschiedliche Zielsetzungen:

| Merkmal | **Incident Response (IR)** | **IT-Forensik** |
| :--- | :--- | :--- |
| **Hauptziel** | Schadensbegrenzung, Ausfallzeit minimieren, Wiederherstellung | Aufklärung der Ursache, Beweissicherung (gerichtsverwertbar) |
| **Priorität** | **Schnelligkeit**: Das System muss so schnell wie möglich wieder laufen. | **Sorgfalt & Meticulousness**: Keine Veränderung von Datenspuren. |
| **Fokus** | Operativ / Business Continuity | Analytisch / Rekonstruktion |

* **Konflikt**: Eine schnelle Eindämmung (z. B. Server hart ausschalten oder RAM löschen) zerstört oft wertvolle forensische Spuren im Arbeitsspeicher. Ein geschultes IR-Team muss daher abwägen, wann Beweissicherung und wann Systemwiederherstellung Vorrang hat.

**Verknüpfte Zettel:**
- [[Schwachstellenkategorien]] (Auslöser für Incidents)

---
#### Flashcards

Was besagt das Prinzip "Assume Breach" in der Incident Response?::Dass ein System niemals als absolut sicher angesehen werden darf. Man plant die Sicherheitsarchitektur unter der Annahme, dass Angreifer bereits im Netz sind.

Wann steht Incident Response im Konflikt mit IT-Forensik?
?
Bei der Systembereinigung: Um den Betrieb schnell wiederherzustellen (IR), müssen infizierte Systeme neu aufgesetzt werden. Dies überschreibt jedoch Logdateien und Arbeitsspeicher-Spuren, die für die forensische Analyse wichtig sind.

Wie lautet der Hauptfokus von Incident Response im Vergleich zur IT-Forensik?::Incident Response fokussiert sich auf Schadenseindämmung und Wiederherstellung (Schnelligkeit); IT-Forensik fokussiert sich auf die präzise Analyse des Hergangs und Beweissicherung (Sorgfalt).

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Incident Response]]
SORT file.mtime DESC
```
