#Note

2026-06-22

Tags: [[Cyber-Security]], [[IT-Sicherheit]], [[Grundlagen]]
#it_security

---

### Sicherheitsnebenziele (Erweiterte Schutzziele)

Ergänzend zu den drei Hauptzielen der [[CIA-Triade]] gibt es mehrere wichtige Nebenziele, die für die Rechtsverbindlichkeit, Nachvollziehbarkeit und den Datenschutz in IT-Systemen unerlässlich sind.

#### 1. Authentizität (Authenticity)
* **Definition**: Nachweis der Identität eines Kommunikationspartners (Subjekts) oder der Herkunft einer Datei (Objekts). Ein Objekt ist authentisch, wenn es wirklich von der angegebenen Quelle stammt.
* **Beispiel**: Verifikation eines SSL-Zertifikats beim Aufrufen einer Website; digitale Signatur einer E-Mail.

#### 2. Autorisierung (Authorization)
* **Definition**: Feststellung, ob ein bereits authentifizierter Benutzer das Recht besitzt, eine bestimmte Aktion (z. B. Lesen, Schreiben, Löschen) auf einer Ressource durchzuführen.
* **Beispiel**: Zuweisung von Administratorrechten vs. Gastrechten in einer Active Directory.

#### 3. Nichtabstreitbarkeit (Non-repudiation)
* **Definition**: Die Unfähigkeit, die Urheberschaft oder Durchführung einer Aktion (z. B. Absenden einer Nachricht, Eingehen eines Vertrags) im Nachhinein glaubhaft zu leugnen.
* **Wichtigkeit bei digitalen Verträgen**: Ohne Nichtabstreitbarkeit könnten Vertragspartner nach Transaktionen behaupten, sie hätten diese nie autorisiert (z. B. bei Online-Banking oder digitalen Kaufverträgen). Sie wird typischerweise durch **digitale Signaturen** (Private Key des Absenders) in Kombination mit vertrauenswürdigen Zeitstempeln (Time Stamps) realisiert.

#### 4. Anonymisierung vs. Pseudonymisierung
Beim Schutz personenbezogener Daten (z. B. nach DSGVO) gibt es zwei Kernkonzepte:
* **Anonymisierung**: Die Identifikationsmerkmale werden so verändert, dass die Daten dauerhaft keiner Person mehr zugeordnet werden können. Dies ist **irreversibel**.
  * *Beispiel*: Das Entfernen von Namen, Adressen und IP-Adressen aus einem Datensatz.
* **Pseudonymisierung**: Identifikationsmerkmale werden durch ein Pseudonym (z. B. eine zufällige ID) ersetzt. Die Zuordnung zur echten Person ist nur mit zusätzlichem, separat geschütztem Wissen möglich. Dies ist **reversibel**.
  * *Beispiel*: Ersetzen von Patientennamen durch IDs und Speichern der Zuordnungstabelle in einer separaten, gesicherten Datenbank.

**Verknüpfte Zettel:**
- [[Rechteverwaltung]] (Zuständig für Autorisierung)
- [[Datenintegrität]] (Wichtig für Authentizität und Nichtabstreitbarkeit durch Signaturen)

---
#### Flashcards

Was versteht man unter Nichtabstreitbarkeit (Non-repudiation)?::Die Unmöglichkeit für einen Sender oder Akteur, die Durchführung einer Aktion (z. B. eine Transaktion) nachträglich zu leugnen.

Warum ist Nichtabstreitbarkeit bei digitalen Verträgen entscheidend?
?
Um Rechtssicherheit zu garantieren. Sie stellt sicher, dass Verträge nicht einfach widerrufen werden können, indem behauptet wird, die Willenserklärung stamme von jemand anderem (erfordert i. d. R. digitale Signaturen).

Welches datenschutzrechtliche Verfahren ist reversibel: Anonymisierung oder Pseudonymisierung?::Die Pseudonymisierung ist reversibel (mittels Zusatzwissen), während die Anonymisierung unwiderruflich (irreversibel) ist.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Sicherheitsnebenziele]]
SORT file.mtime DESC
```