#Note

2026-06-22

Tags: [[Cyber-Security]], [[IT-Sicherheit]], [[Grundlagen]]
#it_security

---

### Der Faktor Mensch in der IT-Sicherheit

Der Mensch gilt in der Informationssicherheit oft als das schwächste Glied der Kette (in der Praxis scherzhaft als **DAU** – *Dümmster Anzunehmender User* – bezeichnet). Angreifer nutzen psychologische Tricks, um technische Schutzmaßnahmen komplett zu umgehen. Diesen Bereich nennt man **Social Engineering**.

---

#### 👤 Social Engineering-Techniken

##### 1. Phishing
* **Beschreibung**: Der Diebstahl von Zugangsdaten oder das Einschleusen von Schadsoftware über gefälschte E-Mails, SMS (Smishing) oder Anrufe (Vishing), die aussehen, als stammten sie von vertrauenswürdigen Quellen (z. B. Banken, Vorgesetzten).
* **Spear Phishing**: Maßgeschneidertes Phishing, das sich gezielt an eine bestimmte Person richtet (z. B. unter Verwendung persönlicher Daten aus Social Media).

##### 2. Pretexting
* **Beschreibung**: Das Erschaffen eines erfundenen Szenarios (ein "Vorwand"), um das Vertrauen des Opfers zu gewinnen und Informationen zu entlocken.
* **Beispiel**: Der Angreifer ruft an, gibt sich als IT-Support aus und behauptet, das Passwort des Nutzers zurücksetzen zu müssen, um ein Serverproblem zu lösen.

##### 3. Tailgating / Piggybacking
* **Beschreibung**: Das unbefugte physische Eindringen in gesicherte Bereiche, indem man einer autorisierten Person einfach durch eine geöffnete Tür folgt (z. B. mit vollgepackten Händen, um Höflichkeit auszunutzen).

---

#### 🛡️ Minimierung des "Faktors Mensch"
Ein Unternehmen kann das Risiko durch den Faktor Mensch nur durch eine Kombination aus organisatorischen und technischen Maßnahmen minimieren:

##### 1. Organisatorische Maßnahmen
* **Security Awareness Trainings**: Regelmäßige, praxisnahe Schulungen der Mitarbeiter zur Erkennung von Social-Engineering-Angriffen.
* **Phishing-Simulationen**: Durchführen simulierter Phishing-Kampagnen zur Überprüfung des Sicherheitsbewusstseins im Alltag.
* **Klare Verhaltensrichtlinien**: Festlegen von Prozessen (z. B. Passwörter werden *niemals* telefonisch weitergegeben; Freigabe hoher Geldbeträge erfordert das Vier-Augen-Prinzip).
* **Fehlerkultur**: Mitarbeiter sollten ermutigt werden, vermutete Fehler (z. B. das Klicken auf einen Phishing-Link) sofort ohne Angst vor Bestrafung zu melden, um Ausbreitungen zu stoppen.

##### 2. Technische Maßnahmen (Absicherung bei menschlichem Versagen)
* **Multi-Faktor-Authentifizierung (MFA)**: Selbst wenn Zugangsdaten per Phishing gestohlen werden, bleibt der Account ohne den zweiten Faktor (z. B. Hardware-Token) geschützt.
* **Least-Privilege-Prinzip**: Mitarbeiter erhalten nur die Berechtigungen, die sie zwingend für ihre Arbeit benötigen. Dies begrenzt den Schaden bei einer Kompromittierung.
* **E-Mail-Filter & Sandboxing**: Automatisches Ausfiltern von Spam- und Phishing-E-Mails sowie das Überprüfen von Anhängen vor der Zustellung.

**Verknüpfte Zettel:**
- [[Rechteverwaltung]] (Technische Schadensbegrenzung durch restriktive Rechte)
- [[Grundlagen Use Case & Scope]] (Bedeutung von Nutzerverhalten im Entwurf)
- [[Tätertypen]] (Gefahren durch Fahrlässigkeit von Innentätern)

---
#### Flashcards

Was versteht man unter Social Engineering?::Die psychologische Manipulation von Menschen mit dem Ziel, sie zur Preisgabe vertraulicher Informationen oder zur Ausführung bestimmter Aktionen (z. B. Malware-Installation) zu bewegen.

Wie unterscheidet sich Phishing von Pretexting?::Phishing nutzt meist standardisierte Massen-E-Mails oder SMS zur Täuschung. Pretexting baut auf einem erfundenen Vorwand auf, um gezielt per Dialog (z. B. Telefonat) Vertrauen aufzubauen.

Mit welchen technischen und organisatorischen Mittel fängt man den Faktor Mensch ab?
?
* **Technisch**: Multi-Faktor-Authentifizierung (MFA), Least-Privilege-Prinzip (Rechteverwaltung), E-Mail-Spamfilter.
* **Organisatorisch**: Security Awareness Trainings, simulierte Phishing-Tests, Etablierung einer offenen Meldekultur.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Faktor Mensch]]
SORT file.mtime DESC
```