#Note

2025-05-15

Tags: [[Lösbarkeit]], [[Lineare Gleichungssysteme]], [[LGS]], [[Rang]], [[Invertierbarkeit]], [[Determinante]], [[Matrizen]], [[Lineare Algebra]]

---

Die **[[Lösbarkeit]]** eines [[Lineare Gleichungssysteme|Linearen Gleichungssystems]] (LGS) $A\vec{x} = \vec{b}$ bezieht sich auf die Frage, ob überhaupt eine Lösung (ein Vektor $\vec{x}$) existiert, die alle Gleichungen im System erfüllt.

**Bedingung für [[Lösbarkeit]]:**

Ein [[Lineare Gleichungssysteme|LGS]] $A\vec{x} = \vec{b}$ ist genau dann lösbar, wenn der [[Rang]] der Koeffizientenmatrix $A$ gleich dem [[Rang]] der erweiterten Matrix $(A|\vec{b})$ ist:

$$rg(A) = rg(A|\vec{b})$$

Wenn $rg(A) \neq rg(A|\vec{b})$, ist das System unlösbar (inkonsistent).

**Anzahl der Lösungen:**

Wenn ein [[Lineare Gleichungssysteme|LGS]] lösbar ist ($rg(A) = rg(A|\vec{b})$), hängt die Anzahl der Lösungen von der Beziehung zwischen dem [[Rang]] und der Anzahl der Variablen ($n$) ab:

1.  **Genau eine Lösung:** Das System hat genau eine eindeutige Lösung, wenn der [[Rang]] gleich der Anzahl der Variablen ist:

    $$rg(A) = rg(A|\vec{b}) = n$$

    Dies tritt insbesondere bei [[Quadratische Matrix|quadratischen Systemen]] auf, bei denen die [[Matrizen|Matrix]] $A$ [[Invertierbarkeit|invertierbar]] ist ($\det(A) \neq 0$), da dann $rg(A) = n$.

2.  **Unendlich viele Lösungen:** Das System hat unendlich viele Lösungen, wenn der [[Rang]] kleiner ist als die Anzahl der Variablen:

    $$rg(A) = rg(A|\vec{b}) < n$$

    In diesem Fall gibt es "freie" Variablen, die beliebig gewählt werden können, wodurch unendlich viele Lösungsvektoren entstehen.

**Zusammenfassung:**

Die [[Lösbarkeit]] und die Anzahl der Lösungen eines [[Lineare Gleichungssysteme|LGS]] können vollständig durch den Vergleich der [[Rang]]e der Koeffizientenmatrix und der erweiterten Matrix sowie der Anzahl der Variablen bestimmt werden.

---

## Verwendung:

```dataview
list from [[Lösbarkeit]]
```