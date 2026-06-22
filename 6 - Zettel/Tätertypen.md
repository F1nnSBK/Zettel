#Note

2026-06-22

Tags: [[Cyber-Security]], [[IT-Sicherheit]], [[Grundlagen]]
#it_security

---

### Tätertypen und Motivationen in der Cyber-Security

Bedrohungen für IT-Systeme können sowohl von Personen innerhalb der Organisation (Innentäter) als auch von außen (Außentäter) ausgehen. Zudem werden Hacker in der Szene metaphorisch nach "Hutfarben" klassifiziert.

---

#### 1. Innentäter vs. Außentäter

##### Innentäter (Insider Threats)
* **Definition**: Personen, die legitimen Zugriff auf interne Systeme und Netzwerke des Unternehmens haben oder hatten (z. B. Angestellte, Administratoren, externe Dienstleister, Ex-Mitarbeiter).
* **Kategorien**:
  * **Böswillige Innentäter**: Sabotieren absichtlich oder stehlen Daten aus Rache, finanzieller Motivation oder Spionage.
  * **Fahrlässige Innentäter**: Richten durch Unachtsamkeit Schaden an (z. B. Klicken auf Phishing-Links, Weitergabe von Passwörtern).

##### Außentäter (External Threats)
* **Definition**: Externe Akteure ohne legitimen Systemzugriff (z. B. Cyberkriminelle, Hacktivisten, staatliche Akteure). Sie müssen Barrieren von außen überwinden.

---

#### 2. Die Hutfarben (Hacker-Typen)

* **White Hat (Ethische Hacker)**:
  * *Verhalten*: Hacken Systeme ausschließlich mit Erlaubnis des Besitzers, um Sicherheitslücken zu finden und zu melden, damit diese geschlossen werden können.
  * *Motivation*: Verbesserung der Sicherheit.
* **Black Hat (Kriminelle Hacker)**:
  * *Verhalten*: Hacken Systeme ohne Erlaubnis und brechen Gesetze, um Schaden anzurichten, Daten zu stehlen, Systeme zu sabotieren oder Geld zu erpressen.
  * *Motivation*: Persönliche Bereicherung, Spionage, Zerstörung.
* **Grey Hat**:
  * *Verhalten*: Hacken ohne Erlaubnis (Verstoß gegen Gesetze), tun dies aber meist ohne direkte Schadensabsicht. Sie melden die Lücke oft dem Betreiber oder veröffentlichen sie, um Druck zur Behebung aufzubauen.
  * *Motivation*: Häufig Geltungsbedürfnis oder der Wunsch, die Sicherheit zu verbessern (auf illegale Weise).

*Ergänzende Typen*:
* **Script Kiddies**: Unerfahrene Angreifer, die fertige Skripte und Tools nutzen, ohne deren Funktionsweise zu verstehen.
* **State-Sponsored / Staatliche Akteure**: Hochprofessionelle Teams mit enormem Budget, die im Auftrag von Regierungen spionieren oder sabotieren.

---

#### ⚖️ Warum sind Innentäter oft gefährlicher als Außentäter?
Innentäter stellen aus folgenden Gründen ein extrem hohes Sicherheitsrisiko dar:

1. **Vorhandene Berechtigungen**: Sie müssen keine Firewalls oder Multi-Faktor-Authentifizierungen (MFA) von außen überwinden; sie haben bereits gültige Passwörter und Zugriffsrechte.
2. **Detailwissen über das System**: Sie kennen die Netzwerkstruktur, die wertvollsten Datenbestände (Crown Jewels) und wissen, wo die Schwachstellen in den Prozessen liegen.
3. **Schwere Erkennbarkeit**: Da sie sich legitim im System bewegen, fallen ihre Aktionen (z. B. das Herunterladen großer Datenmengen) oft nicht unter Anomalien im Intrusion Detection System.

**Verknüpfte Zettel:**
- [[Organistionsformen]] (Strukturen und Rollen in Unternehmen)
- [[Rechteverwaltung]] (Einschränkung von Insider-Risiken durch das Least-Privilege-Prinzip)

---
#### Flashcards

Was ist der Unterschied zwischen White Hat, Black Hat und Grey Hat Hackern?::White Hats hacken legal zur Sicherheitsverbesserung; Black Hats hacken illegal mit krimineller Absicht; Grey Hats hacken illegal, aber meist ohne direkte Schadensabsicht.

Warum sind Innentäter (Insider) für Unternehmen schwerer zu stoppen als Außentäter?
?
Weil sie bereits legitime Zugangsdaten besitzen (umgehen Perimeter-Security wie Firewalls), internes Systemwissen haben und ihre schädlichen Aktionen schwer von ihrer normalen Arbeit zu unterscheiden sind.

Wie nennt man einen Hacker, der im Auftrag einer Regierung spioniert?::State-Sponsored Actor oder staatlicher Akteur (häufig als APT klassifiziert).

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Tätertypen]]
SORT file.mtime DESC
```