#Note

2026-06-22

Tags: [[Cyber-Security]], [[IT-Sicherheit]], [[Grundlagen]]
#it_security

---

### Safety vs. Security

Im Englischen wird klar zwischen *Safety* und *Security* unterschieden, während im Deutschen beide Begriffe oft mit "Sicherheit" übersetzt werden. Das Verständnis dieses Unterschieds ist besonders in der industriellen IT (OT - Operational Technology) und im IoT-Bereich essenziell.

| Merkmal | **Safety (Betriebssicherheit)** | **Security (Angriffssicherheit)** |
| :--- | :--- | :--- |
| **Bedeutung** | Unfallverhütung / Schutz vor Fehlfunktionen | Schutz vor böswilligen Angriffen |
| **Richtung** | **Inside-Out**: Schutz der Umwelt vor dem System | **Outside-In**: Schutz des Systems vor der Umwelt |
| **Gefahrenquelle** | Zufällige Fehler, Verschleiß, Naturkatastrophen | Menschliche Angreifer mit böswilliger Absicht |
| **Ziel** | Vermeidung von Personen- & Sachschäden | Erhalt der Vertraulichkeit, Integrität & Verfügbarkeit |

---

#### 🏭 Praxis-Beispiel: Maßnahmen in einem Kraftwerk
In einem Kern- oder Kohlekraftwerk überschneiden sich beide Konzepte, erfordern jedoch völlig unterschiedliche Maßnahmen:

##### 1. Safety-Maßnahmen (Schutz vor technischen Fehlern/Unfällen)
* **Überdruckventile**: Öffnen sich rein mechanisch bei zu hohem Druck, um eine Explosion zu verhindern (unabhängig von Software).
* **Redundante Notkühlsysteme**: Sichern die Kühlung des Reaktors bei Ausfall der Hauptkühlung.
* **Brandschutztüren & Notaus-Schalter**: Physische Vorrichtungen zur Schadensbegrenzung.

##### 2. Security-Maßnahmen (Schutz vor Manipulationen/Sabotage)
* **Firewalls & Netzsegmentierung**: Trennung des administrativen IT-Netzwerks vom operativen SCADA/Steuerungsnetzwerk.
* **Kryptographisch gesicherte Kommunikation**: Verschlüsselung von Befehlen an Steuergeräte (PLC), um Man-in-the-Middle-Angriffe zu verhindern.
* **Zutrittskontrollen**: Biometrische Scanner und Wachpersonal an Eingängen zu Serverräumen und Leitständen.

#### Das Zusammenwirken (Die Brücke)
Wenn ein Security-Schutz versagt (z. B. ein Angreifer dringt in das Steuerungssystem ein und manipuliert die Sensordaten), kann dies direkt zu einem Safety-Vorfall führen (z. B. Überhitzung des Reaktors). Cybersicherheit (Security) ist somit eine zwingende Voraussetzung für physische Betriebssicherheit (Safety).

**Verknüpfte Zettel:**
- [[Grundlagen Software Engineering]] (Qualitätsmerkmale von Software)
- [[Jeep Cherokee Hack]] (Physische Safety-Folgen durch einen Security-Mangel)

---
#### Flashcards

Was ist der Unterschied zwischen Safety und Security bezüglich der Schutzrichtung?::Safety schützt die Umwelt/Menschen vor Fehlfunktionen des Systems (Inside-Out); Security schützt das System vor böswilligen Zugriffen von außen (Outside-In).

Welche Security-Maßnahme schützt die Steuergeräte (PLCs) eines Kraftwerks vor Sabotage?::Eine strikte Netzsegmentierung (Trennung von Office-IT und OT) sowie die Verschlüsselung und Authentifizierung des Datenverkehrs.

Warum kann ein Security-Versagen zu einem Safety-Problem führen?
?
Wenn ein Angreifer Sicherheitsbarrieren (Security) überwindet, kann er physische Aktoren manipulieren (z. B. Ventile schließen, Bremsen deaktivieren), was Unfälle verursacht und Menschen gefährdet (Safety-Verstoß).

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Safety vs. Security]]
SORT file.mtime DESC
```