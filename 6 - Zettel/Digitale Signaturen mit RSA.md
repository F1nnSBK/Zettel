#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Kryptographie]], [[Asymmetrische-Kryptographie]]
#it_security

---

### Digitale Signaturen mit RSA

Digitale Signaturen sichern die Schutzziele **Integrität**, **Authentizität** und **Nichtabstreitbarkeit** (Non-repudiation) von Dokumenten und Nachrichten. Das [[RSA-Verfahren]] kann direkt zur Signaturerzeugung eingesetzt werden.

---

#### 1. Der Ablauf der Signierung
Um eine Nachricht $m$ zu signieren, nutzt der Sender (Alice) seinen privaten Schlüssel $d$ und eine kryptographische Hash-Funktion $H$.

```
Alice:  Nachricht (m) ──► [ Hashing ] ──► Hash (h) ──► [ RSA-Private-Key (d) ] ──► Signatur (s)
                                                                                  
Bob:    Nachricht (m) ──► [ Hashing ] ──► Hash (h')
                                            │
                                      (Ist gleich?)
                                            │
        Signatur (s)  ──► [ RSA-Public-Key (e) ] ──► Entschlüsselter Hash (h_dec)
```

##### Schritt-für-Schritt (Alice)
1. **Hashing**: Alice berechnet den Hashwert der Nachricht $m$ (z. B. mit SHA-256):
   $$h = H(m)$$
2. **Signaturerzeugung**: Alice verschlüsselt den Hashwert $h$ mit ihrem **privaten Schlüssel** $d$:
   $$s = h^d \pmod n$$
3. **Senden**: Alice schickt die Nachricht $m$ zusammen mit der Signatur $s$ an Bob.

---

#### 2. Der Ablauf der Verifikation (Bob)
Bob empfängt die Nachricht $m$ und die Signatur $s$. Er nutzt Alices öffentlichen Schlüssel $e$.

##### Schritt-für-Schritt (Bob)
1. **Eigenes Hashing**: Bob berechnet den Hashwert der empfangenen Nachricht $m$ selbst:
   $$h' = H(m)$$
2. **Signatur entschlüsseln**: Bob entschlüsselt die Signatur $s$ mit Alices **öffentlichem Schlüssel** $e$:
   $$h_{\text{dec}} = s^e \pmod n$$
3. **Vergleich**: Bob prüft, ob gilt:
   $$h' \equiv h_{\text{dec}} \pmod n$$
   Stimmen die Werte überein, ist bewiesen:
   * Die Nachricht wurde nicht verändert (Integrität).
   * Die Nachricht stammt wirklich von Alice, da nur sie den privaten Schlüssel $d$ besitzt (Authentizität / Nichtabstreitbarkeit).

---

#### ⚖️ Warum wird der Hashwert signiert und nicht die Nachricht selbst?
Das direkte Signieren großer Dateien ohne Hashing hat gravierende Nachteile:

1. **Performance**: Asymmetrische Operationen modulo $n$ sind extrem langsam. Eine Datei von mehreren Gigabyte direkt zu verschlüsseln, würde Stunden dauern. Durch Hashing wird die Datei auf eine feste, kurze Länge (z. B. 256 Bit) reduziert.
2. **Sicherheit (Existential Forgery)**:
   * Wenn man ohne Hashfunktion signiert, könnte ein Angreifer eine zufällige Zahl $s$ wählen und berechnen: $m = s^e \pmod n$.
   * Die Kombination $(m, s)$ wäre eine mathematisch gültige Signatur, obwohl $m$ nur unleserlicher Datenmüll ist.
   * Durch die Einweg-Eigenschaft der Hash-Funktion $H$ ist es unmöglich, zu einem gewählten $s$ eine sinnvolle Nachricht zu finden, deren Hashwert $s^e \pmod n$ entspricht.

**Verknüpfte Zettel:**
- [[RSA-Verfahren]] (Die zugrundeliegende mathematische Basis)
- [[Sicherheitsnebenziele]] (Relevanz von Authentizität und Nichtabstreitbarkeit)

---
#### Flashcards

Wie wird eine digitale Signatur mit RSA erzeugt?::Der Hashwert der Nachricht $h = H(m)$ wird mit dem privaten Schlüssel $d$ des Senders signiert: $s = h^d \pmod n$.

Wie verifiziert ein Empfänger eine digitale RSA-Signatur?::Er berechnet den Hashwert der Nachricht $h' = H(m)$ und vergleicht ihn mit dem entschlüsselten Signaturwert $h_{dec} = s^e \pmod n$. Beide müssen übereinstimmen.

Welche zwei Gründe sprechen dafür, immer den Hashwert statt des Volltexts zu signieren?::1. Performance (Verschlüsselung eines kurzen, festen Hashs statt großer Dateien). 2. Sicherheit (Verhinderung von Fälschungsangriffen durch Existential Forgery).

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Digitale Signaturen mit RSA]]
SORT file.mtime DESC
```
