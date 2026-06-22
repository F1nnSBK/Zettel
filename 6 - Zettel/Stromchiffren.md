#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Kryptographie]], [[Stromchiffren]]
#it_security

---

### Stromchiffren (Stream Ciphers)

Eine **Stromchiffre** verschlüsselt Daten zeichenweise (meist bit- oder byteweise). Sie simuliert die Funktionsweise des [[One-Time-Pad]], indem sie aus einem kurzen geheimen Schlüssel einen langen pseudozufälligen **Schlüsselstrom** (Keystream) erzeugt.

```mermaid
graph LR
    K["Schlüssel (Key)"] --> PRNG["CSPRNG / Keystream Generator"]
    PRNG -->|Keystream (s_i)| XOR{{"XOR (⊕)"}}
    P["Klartext (m_i)"] --> XOR
    XOR --> C["Geheimtext (c_i)"]
```

---

#### Die XOR-Operation ($\oplus$)
Das Herzstück fast aller Stromchiffren ist die XOR-Verknüpfung (Addition modulo 2).
* **Eigenschaft**: Die XOR-Operation ist symmetrisch. Zweimalige Anwendung mit demselben Wert hebt sich auf:
  $$c_i = m_i \oplus s_i \implies m_i = c_i \oplus s_i$$
* **Wahrheitstabelle**:
  * $0 \oplus 0 = 0$
  * $1 \oplus 1 = 0$
  * $1 \oplus 0 = 1$
  * $0 \oplus 1 = 1$

---

#### Zufallsgeneratoren (RNGs)
Die Sicherheit einer Stromchiffre hängt direkt von der Qualität des Schlüsselstrom-Generators ab:

##### 1. TRNG (True Random Number Generator)
* **Funktionsweise**: Nutzt unvorhersehbare physikalische Prozesse (z. B. thermisches Rauschen, radioaktiven Zerfall).
* **Einsatz**: Zur Erzeugung von Master-Schlüsseln (Keys) oder für das One-Time-Pad. TRNGs sind jedoch zu langsam für kontinuierliche Datenströme.

##### 2. PRNG (Pseudorandom Number Generator)
* **Funktionsweise**: Berechnet deterministisch eine Zahlenfolge aus einem Startwert (Seed).
* **Problem**: Bei Kenntnis der mathematischen Formel oder des internen Zustands kann die restliche Sequenz vorhergesagt werden (kryptographisch unsicher!).

##### 3. CSPRNG (Cryptographically Secure PRNG)
* **Funktionsweise**: Ein PRNG, der zwei zusätzliche Sicherheitskriterien erfüllt:
  * **Next-Bit-Test**: Selbst bei Kenntnis der ersten $k$ Bits der Sequenz ist es unmöglich, das $(k+1)$-te Bit mit einer Wahrscheinlichkeit $> 50\%$ vorherzusagen.
  * **Zustandssicherheit (State Compromise Extension)**: Selbst wenn ein Angreifer den internen Zustand des Generators zu einem Zeitpunkt erbeutet, kann er daraus keine vorherigen Zufallszahlen rekonstruieren.
* **Einsatz**: Generatoren in modernen Stromchiffren.

**Verknüpfte Zettel:**
- [[One-Time-Pad]] (Das theoretische Ideal der Stromchiffren)

---
#### Flashcards

Wie wird der Schlüsselstrom bei einer Stromchiffre mit dem Klartext verknüpft?::Bitweise mittels der XOR-Operation ($\oplus$).

Welche zwei Bedingungen machen einen Zufallsgenerator zu einem CSPRNG?::Er muss den Next-Bit-Test bestehen (Zukunft nicht vorhersagbar) und Zustandssicherheit garantieren (Vergangenheit bei Systemcompromiss nicht rekonstruierbar).

Warum ist ein Standard-PRNG (wie in Programmiersprachen üblich) für Kryptographie ungeeignet?::Weil er deterministisch arbeitet und ein Angreifer nach Beobachtung einiger Ausgaben den internen Zustand berechnen und alle zukünftigen Schlüsselstrom-Bits vorhersagen kann.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Stromchiffren]]
SORT file.mtime DESC
```
