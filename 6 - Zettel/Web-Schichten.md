#Note

2026-06-22

Tags: [[Cyber-Security]], [[IT-Sicherheit]], [[Netzwerke]], [[Grundlagen]]
#it_security

---

### Die drei Web-Schichten (Clear Web, Deep Web, Dark Net)

Das Internet wird metaphorisch oft als Eisberg dargestellt. Es lässt sich in drei verschiedene Schichten unterteilen, die sich in ihrer Zugänglichkeit, Indexierung und Anonymität unterscheiden.

```
          ▲      Clear Web (Surface Web)  ~4-10%
         / \     [Indexiert, über Google findbar]
        /   \ 
_______/_____\_________________________________ Wasserlinie
      /       \  Deep Web              ~90-95%
     /         \ [Datenbanken, Logins, Online-Banking]
    /           \ 
   /  Dark Net   \ Dark Net             <1%
  /  [TOR-Netz]   \ [Verschlüsselt, anonymisiert]
 /_________________\ 
```

#### 1. Clear Web (Surface Web)
* **Definition**: Der sichtbare, frei zugängliche Teil des Internets. Alle Seiten sind von Standard-Suchmaschinen (Google, Bing) indexiert und können mit normalen Webbrowsern aufgerufen werden.
* **Beispiel**: Wikipedia, Nachrichtenseiten, öffentliche Blogs.

#### 2. Deep Web
* **Definition**: Seiten und Inhalte, die **nicht von Suchmaschinen indexiert** sind. Sie machen den größten Teil des Internets (ca. 90-95%) aus. Der Zugriff ist oft durch Passwörter, Bezahlschranken oder Datenbankabfragen geschützt.
* **Beispiel**: E-Mail-Postfächer, Online-Banking-Portale, firmeninterne Wikis, Krankenakten, SQL-Datenbankinhalte.

#### 3. Dark Net (Darknet)
* **Definition**: Ein kleiner, geschlossener Teil des Deep Webs, der auf dezentralen Netzwerken (z. B. TOR, I2P) basiert. Seiten enden oft auf spezielle TLDs (z. B. `.onion`) und können nur mit spezieller Software (z. B. dem TOR-Browser) aufgerufen werden. Datenverkehr und Serverstandorte sind stark verschlüsselt und anonymisiert.
* **Beispiel**: Foren für Whistleblower, Marktplätze, anonyme Kommunikationsplattformen.

---

#### ⚖️ Herausforderungen für Strafverfolgungsbehörden im Dark Net
Das Dark Net erschwert die Verfolgung illegaler Aktivitäten massiv durch folgende Faktoren:

1. **Onion-Routing & IP-Verschleierung**: Durch die mehrschichtige Verschlüsselung des [[TOR-Netzwerk|TOR-Netzwerks]] sieht der Zielserver nur die IP-Adresse des Exit-Nodes, nicht aber die des eigentlichen Nutzers.
2. **Dezentralisierung & Hosten im Ausland**: Server werden oft in Ländern betrieben, die nicht mit westlichen Behörden kooperieren ("Bulletproof Hosting").
3. **Anonyme Zahlungsmittel**: Transaktionen werden überwiegend mit Kryptowährungen abgewickelt. Insbesondere *Privacy Coins* wie Monero (XMR) machen die Nachverfolgung von Geldflüssen nahezu unmöglich (im Gegensatz zu Bitcoin, dessen Blockchain öffentlich ist).
4. **Kein zentraler Administrator**: Es gibt keine zentrale Instanz, die Webseiten sperren oder Nutzerdaten herausgeben kann.

**Verknüpfte Zettel:**
- [[Datenbanken]] (Basis des Deep Webs)
- [[REST]] (Schnittstellen im Clear/Deep Web)
- [[Cloud Computing]] (Hosting-Infrastruktur)

---
#### Flashcards

Wie unterscheiden sich Deep Web und Dark Net bezüglich des Zugriffs?::Das Deep Web erfordert meist Zugangsdaten (z. B. Logins), läuft aber über Standardbrowser. Das Dark Net erfordert spezielle Software (z. B. TOR-Browser) und Verschlüsselungsprotokolle.

Welche drei Faktoren machen Ermittlungen im Dark Net so schwierig?
?
1. **IP-Anonymisierung**: Die Herkunft des Datenverkehrs wird verschleiert.
2. **Kryptowährungen (Privacy Coins)**: Finanzströme (z. B. Monero) sind nicht rückverfolgbar.
3. **Internationale Zuständigkeiten**: Server stehen oft in unkooperativen Ländern (Bulletproof Hosting).

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Web-Schichten]]
SORT file.mtime DESC
```