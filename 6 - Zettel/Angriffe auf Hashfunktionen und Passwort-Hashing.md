#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Kryptographie]], [[Hashing]]
#it_security

---

### Angriffe auf Hashfunktionen und Passwort-Hashing

Diese Notiz behandelt Angriffe auf die Vertraulichkeit von gehashten Daten (z. B. Passwörtern) sowie strukturelle Schwachstellen in Hash-Algorithmen.

---

#### 1. Angriffe auf Passwort-Hashes

##### Rainbow Tables (Regenbogen-Tabellen)
* **Problem**: Datenbanken speichern Passwörter aus Sicherheitsgründen nur als Hashwerte. Erbeutet ein Angreifer die Datenbank, versucht er die Passwörter per Brute-Force oder Wörterbuchangriff zu erraten.
* **Das Tool**: Eine **Rainbow Table** ist eine gigantische, vorab berechnete Tabelle, die Milliarden Klartextwörter über mathematische Reduktionsfunktionen mit ihren zugehörigen Hashes verknüpft. Sie erlaubt es, einen erbeuteten Hashwert in Sekunden in das Klartextpasswort zurückzuübersetzen.
* **Gegenmaßnahme: Salting (Salzen)**:
  * Vor dem Hashing wird an jedes Passwort eine eindeutige, zufällige Zeichenfolge (das **Salt**) angehängt:
    $$h = H(\text{Passwort} \parallel \text{Salt})$$
  * Das Salt wird im Klartext in der Datenbank neben dem Hash gespeichert.
  * **Wirkung**: Rainbow Tables werden komplett nutzlos. Da jedes Passwort ein anderes Salt nutzt, müsste der Angreifer für jedes einzelne Benutzerkonto eine eigene, gigantische Tabelle neu berechnen.

##### Langsame Hash-Funktionen gegen Brute-Force
* Da moderne Grafikkarten (GPUs) Milliarden Hashes pro Sekunde berechnen können, sind Standard-Hashfunktionen (wie SHA-256) für Passwörter unsicher.
* **Lösung**: Verwendung spezieller, künstlich verlangsamter Hash-Funktionen, die viel Rechenzeit und RAM benötigen (z. B. **Argon2id**, **bcrypt**, **PBKDF2**), um Brute-Force-Angriffe unbezahlbar zu machen.

---

#### 2. Length-Extension-Angriffe (Längen-Erweiterung)
Dieser Angriff betrifft die interne Struktur vieler klassischer Hash-Funktionen (wie MD5, SHA-1, SHA-256), die auf der **Merkle-Damgård-Konstruktion** basieren.

##### Das Phänomen
* Wenn ein Angreifer den Hashwert $H(m)$ einer geheimen Nachricht $m$ und die Länge von $m$ kennt, kann er den gültigen Hashwert für eine erweiterte Nachricht:
  $$H(m \parallel \text{Padding} \parallel \text{Zusatzdaten})$$
  berechnen, **ohne** die ursprüngliche Nachricht $m$ jemals zu kennen.

##### Relevanz für Message Authentication Codes (MACs)
* Ein naiver MAC-Entwurf lautet: $\text{MAC}(m) = H(\text{Key} \parallel m)$.
* Durch den Length-Extension-Angriff kann ein Angreifer an das Ende einer Nachricht eigene Steuerbefehle anhängen und den passenden, gültigen MAC dafür berechnen, obwohl er den geheimen Schlüssel (`Key`) nicht kennt.
* **Gegenmaßnahmen**:
  * Verwendung des standardisierten **HMAC-Verfahrens** ($\text{HMAC}(m) = H((\text{Key} \oplus opad) \parallel H((\text{Key} \oplus ipad) \parallel m))$).
  * Verwendung von **SHA-3**, welches auf der *Sponge-Konstruktion* basiert und mathematisch immun gegen diesen Angriff ist.

**Verknüpfte Zettel:**
- [[Hashfunktionen]] (Sicherheitsanforderungen und Beispiele)

---
#### Flashcards

Was versteht man unter "Salting" beim Passwort-Hashing und wogegen schützt es?::Das Anhängen einer zufälligen Zeichenfolge vor dem Hashing des Passworts. Es schützt vor dem Einsatz vorkalkulierter Regenbogen-Tabellen (Rainbow Tables).

Warum sind Standard-Hashfunktionen wie SHA-256 für die Passwortspeicherung ungeeignet?::Weil sie zu schnell berechnet werden können. Angreifer können mit starker Hardware (GPUs) Milliarden Passwörter pro Sekunde per Brute-Force testen. Es müssen langsame Verfahren wie Argon2id verwendet werden.

Welches Problem entsteht bei der naiven MAC-Konstruktion $H(Key \parallel Message)$?::Sie ist anfällig für Length-Extension-Angriffe, bei denen Angreifer unbemerkt Daten an die Nachricht anhängen und den passenden MAC ohne Schlüsselberechnung fälschen können.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Angriffe auf Hashfunktionen und Passwort-Hashing]]
SORT file.mtime DESC
```
