#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Kryptographie]], [[Mathematik]]
#it_security

---

### Mathematische Grundlagen der Kryptographie

Die moderne Kryptographie basiert fast vollständig auf der **Zahlentheorie** und der **abstrakten Algebra**. Hier werden die wichtigsten mathematischen Werkzeuge vorgestellt.

---

#### 1. Der Modulo-Operator ($\pmod m$)
Der Modulo-Operator berechnet den Rest einer Ganzzahldivision.
* **Formel**: $a \pmod m = r$ bedeutet, dass es eine ganze Zahl $q$ gibt, sodass:
  $$a = q \cdot m + r \quad \text{mit} \quad 0 \le r < m$$
* **Beispiele**:
  * $15 \pmod 4 = 3 \quad (\text{denn } 15 = 3 \cdot 4 + 3)$
  * $-3 \pmod 5 = 2 \quad (\text{denn } -3 = -1 \cdot 5 + 2)$

---

#### 2. Restklassenringe ($\mathbb{Z}_m$)
Die Menge aller Reste bei Division durch eine Zahl $m$ bildet den **Restklassenring** $\mathbb{Z}_m = \{0, 1, 2, \dots, m-1\}$.
* In $\mathbb{Z}_m$ kann normal addiert, subtrahiert und multipliziert werden, wobei nach jeder Operation Modulo $m$ gerechnet wird.
* **Beispiel in $\mathbb{Z}_9$**:
  * $5 + 6 = 11 \equiv 2 \pmod 9$
  * $4 \cdot 3 = 12 \equiv 3 \pmod 9$

---

#### 3. Primkörper ($\mathbb{Z}_p$)
Ist der Modul eine Primzahl $p$, so wird der Restklassenring zu einem **Körper** (engl. *Field*), geschrieben als $\mathbb{Z}_p$.
* **Eigenschaft**: In einem Primkörper $\mathbb{Z}_p$ besitzt jedes Element $a \neq 0$ ein eindeutiges **multiplikatives Inverses** $a^{-1}$ modulo $p$, sodass gilt:
  $$a \cdot a^{-1} \equiv 1 \pmod p$$
* Dies ist für die Entschlüsselung (Umkehrung der Verschlüsselung) essenziell.

---

#### 4. Elliptische Kurven (Elliptic Curves)
Elliptische Kurven sind mathematische Kurven, die durch Gleichungen der Form:
$$y^2 \equiv x^3 + a \cdot x + b \pmod p$$
definiert werden.
* **Gruppe**: Die Punkte auf einer solchen Kurve bilden zusammen mit einem speziellen "Punkt im Unendlichen" eine mathematische Gruppe.
* **Nutzen**: Das Problem, aus einem Punkt $P$ und einem Punkt $Q = k \cdot P$ den Faktor $k$ zu berechnen, ist extrem schwer (**Diskretes Logarithmusproblem auf elliptischen Kurven - ECDLP**). Dies erlaubt kürzere Schlüssel bei gleicher Sicherheit im Vergleich zu RSA.

**Verknüpfte Zettel:**
- [[Natürliche Zahlen]] (Grundlegende Zahlenmengen)

---
#### Flashcards

Wie ist die Modulo-Operation mathematisch definiert?::Als der Rest $r$ einer Ganzzahldivision: $a \pmod m = r$, wobei $a = q \cdot m + r$ mit $0 \le r < m$.

Was unterscheidet einen Primkörper $\mathbb{Z}_p$ von einem Restklassenring $\mathbb{Z}_m$?::Im Primkörper $\mathbb{Z}_p$ (Modul ist eine Primzahl) besitzt jedes Element ungleich Null ein multiplikatives Inverses. Im Restklassenring $\mathbb{Z}_m$ ist dies nicht für alle Elemente der Fall.

Warum sind Elliptische Kurven in der modernen Kryptographie so beliebt?::Weil das mathematische Problem (ECDLP) so schwer ist, dass viel kürzere Schlüssellängen (z. B. 256 Bit) die gleiche Sicherheit bieten wie RSA mit 3072 Bit.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Mathematische Grundlagen der Kryptographie]]
SORT file.mtime DESC
```
