#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Netzwerke]], [[Anonymisierung]]
#it_security

---

### Sicherheit und Schwächen von TOR

Obwohl das TOR-Netzwerk starke Anonymität bietet, existieren verschiedene Angriffsvektoren, die die Anonymität der Benutzer gefährden oder zur Kompromittierung von Daten führen können.

---

#### 1. Angriffe an den Knotenpunkten

##### A. Bösartige Exit-Nodes (Exit Node Attacks)
* **Das Risiko**: Da der Exit-Node die letzte Verschlüsselungsschicht abstreift, fließen die Daten von dort unverschlüsselt zum Zielserver, sofern keine zusätzliche Transportschichtverschlüsselung vorliegt.
* **Der Angriff**: Ein Angreifer betreibt absichtlich Exit-Nodes, um den ausgehenden Verkehr zu sniffen. Er kann unverschlüsselte Passwörter mitlesen, DNS-Anfragen manipulieren oder Schadcode in HTTP-Downloads injizieren.
* **Gegenmaßnahme**: **Ende-zu-Ende-Verschlüsselung**. Über TOR sollten ausschließlich verschlüsselte Protokolle (z. B. HTTPS, SSH) verwendet werden. HTTPS verschlüsselt die Daten zwischen Client und Zielserver, sodass der Exit-Node-Betreiber nur noch verschlüsselten Datenmüll sieht.

##### B. Traffic-Korrelation (End-to-End Correlation)
* **Das Risiko**: Ein Angreifer (z. B. ein Geheimdienst) kontrolliert oder überwacht gleichzeitig den Guard Node und den Exit Node einer Verbindung.
* **Der Angriff**: Da TOR den Datenverkehr fast in Echtzeit weiterleitet (Low-Latency-Netzwerk), kann der Angreifer die Pakete korrelieren. Stimmen die Paketgrößen und die exakten Sendezeiten am Eingang (Guard) und Ausgang (Exit) überein, kann der Angreifer die echte IP-Adresse des Benutzers dem aufgerufenen Ziel zuordnen.

---

#### 2. Schwachstellen auf Anwendungsebene

##### A. Browser Fingerprinting
* **Problem**: Webserver können detaillierte Systeminformationen (Bildschirmauflösung, installierte Schriften, Zeitzone, Betriebssystemversion) abfragen. Die Kombination dieser Daten ergibt einen eindeutigen "Fingerabdruck" (Fingerprint) des Nutzers.
* **Schutz im TOR-Browser**:
  * Deaktivierung aller Plugins (wie Flash oder Java), da diese die echte IP-Adresse am Browser vorbei direkt an Server senden können.
  * Standardisierung der Fenstergröße (Benutzer sollten das Browserfenster nicht maximieren).
  * Blockieren von Canvas-Bildabfragen zur Verhinderung von Hardware-Fingerprinting.

##### B. DNS Leaks
* **Problem**: Wenn der Browser zwar den Web-Verkehr über TOR leitet, die Namensauflösung (DNS) jedoch über den lokalen Internetprovider (ISP) abwickelt.
* **Schutz**: Der TOR-Browser zwingt alle DNS-Anfragen, ebenfalls verschlüsselt durch das TOR-Netzwerk zu laufen.

**Verknüpfte Zettel:**
- [[Onion Routing und TOR-Netzwerk]] (Struktur des Netzwerks)

---
#### Flashcards

Welche Gefahr droht durch manipulierte Exit-Nodes im TOR-Netzwerk?::Der Exit-Node kann unverschlüsselten Datenverkehr (HTTP) mitlesen, manipulieren oder Schadcode injizieren. Schutz bietet nur Ende-zu-Ende-Verschlüsselung (HTTPS).

Wie funktioniert ein Traffic-Korrelations-Angriff auf das TOR-Netzwerk?::Ein Angreifer, der den Eintritts- und den Austrittsknoten einer Verbindung überwacht, gleicht Sendezeiten und Paketgrößen ab, um die IP des Nutzers dem Ziel zuzuordnen.

Warum sollte das Fenster des TOR-Browsers nicht maximiert werden?::Um "Browser Fingerprinting" zu erschweren. Eine einheitliche Standard-Fenstergröße sorgt dafür, dass sich die Benutzer im Web nicht durch individuelle Auflösungen voneinander unterscheiden lassen.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Sicherheit und Schwächen von TOR]]
SORT file.mtime DESC
```
