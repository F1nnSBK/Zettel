#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Netzwerke]], [[Anonymisierung]]
#it_security

---

### Onion Routing und TOR-Netzwerk

Das **TOR-Netzwerk** (The Onion Router) ist ein freies, dezentrales Netzwerk zur Anonymisierung von Verbindungsdaten im Internet. Es bildet das Rückgrat des Dark Nets.

---

#### 1. Das Funktionsprinzip (Onion Routing)
Die Kernidee ist die **mehrschichtige Verschlüsselung** (wie die Schichten einer Zwiebel / *Onion*). Die Daten werden über eine Kette von drei zufällig ausgewählten Relays (Nodes) geleitet.

```
Client ──► [ Guard Node ] ──► [ Middle Node ] ──► [ Exit Node ] ──► Zielserver
```

##### Ablauf der Verschlüsselung
Der Client vereinbart vorab über [[Diffie-Hellman Key Exchange|DHKE]] eigene symmetrische Sitzungsschlüssel mit jedem der drei Knoten. Er verschlüsselt die Nachricht dreifach:
$$\text{Paket} = E_{\text{Guard}}(E_{\text{Middle}}(E_{\text{Exit}}(\text{Daten} \parallel \text{Ziel})))$$

##### Ablauf der Weiterleitung
1. **Guard Node (Entry Node)**:
   * Entschlüsselt die äußere Schicht. Er sieht die IP-Adresse des Clients und weiß, dass das Paket zum Middle Node weitergeleitet werden muss.
   * *Wissen*: Kennt den Client, aber weder den Inhalt noch das Ziel.
2. **Middle Node (Relay)**:
   * Entschlüsselt die mittlere Schicht. Er sieht, dass das Paket vom Guard Node kam und zum Exit Node gesendet werden muss.
   * *Wissen*: Kennt nur den vorherigen und nachfolgenden Knoten. Hat keine Verbindung zum Client oder zum Ziel.
3. **Exit Node (Ausgangsknoten)**:
   * Entschlüsselt die letzte Schicht. Er erhält die tatsächlichen Rohdaten und das eigentliche Ziel (z. B. eine IP-Adresse im Clear Web). Er leitet die Daten dorthin weiter.
   * *Wissen*: Kennt das Ziel und die übertragenen Daten, aber nicht die IP-Adresse des Clients.

---

#### 2. Die Rollen der Knoten
* **Guard Node**: Um den Client vor Identifikation durch bösartige Einstiegsknoten zu schützen, bleibt ein Client über einen längeren Zeitraum (meist Wochen/Monate) mit demselben vertrauenswürdigen Guard-Knoten verbunden (*Entry Guards*).
* **Exit Node**: Die kritischste Rolle, da hier die unverschlüsselte Datenübertragung ins normale Internet erfolgt. Betreiber von Exit-Nodes tragen rechtliche Risiken (da dort illegale Datenströme austreten) und Angriffsrisiken.

**Verknüpfte Zettel:**
- [[Web-Schichten]] (Verbindung zum Dark Net)
- [[Diffie-Hellman Key Exchange]] (Kryptographische Basis für den Session-Key-Austausch)

---
#### Flashcards

Wie funktioniert die Verschlüsselung beim Onion Routing?::Der Client verschlüsselt das Datenpaket nacheinander mit den Schlüsseln des Exit-, Middle- und Guard-Nodes, sodass jeder Knoten auf dem Weg nur eine Schicht entschlüsseln muss.

Welche IP-Adressen kennt ein Middle Node im TOR-Netzwerk?::Nur die IP-Adresse des Guard-Nodes (Eingang) und die des Exit-Nodes (Ausgang). Die IP-Adresse des Clients ist ihm unbekannt.

Welche Funktion hat ein Entry Guard (Guard Node)?::Er ist der erste Knoten im TOR-Pfad. Da er die echte IP des Nutzers sieht, bleibt der Client lange mit demselben Guard verbunden, um Angreifer am systematischen Ausspähen des Clients zu hindern.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Onion Routing und TOR-Netzwerk]]
SORT file.mtime DESC
```
