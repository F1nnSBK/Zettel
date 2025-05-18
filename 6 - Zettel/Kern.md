#Note

2025-05-17

Tags: [[Kern]], [[Nullraum]], [[Matrizen]], [[Lineare Algebra]], [[Vektorräume]], [[Unterraum]], [[Homogenes Lineares Gleichungssystem]], [[Lösbarkeit]], [[Rang]], [[Basis]], [[Rang-Defekt-Theorem]], [[Gauß-Algorithmus]]

---

Der **Kern** einer [[Matrizen|Matrix]] $A$, auch **Nullraum** genannt (notiert als $\operatorname{Kern}(A)$ oder $\operatorname{Null}(A)$), ist die Menge aller [[Vektoren]] $\vec{x}$, die durch die Multiplikation mit der Matrix $A$ auf den [[Nullvektor]] $\vec{0}$ abgebildet werden.

**Definition:**

$$ \operatorname{Kern}(A) = \{ \vec{x} \mid A\vec{x} = \vec{0} \} $$

Die Bedingung $A\vec{x} = \vec{0}$ beschreibt ein **[[Homogenes Lineares Gleichungssystem]]**. Der Kern ist also die Lösungsmenge dieses homogenen Systems.

**Eigenschaften und Bedeutung:**

* Der Kern einer [[Matrizen|Matrix]] $A$ ist immer ein **[[Vektorräume|Unterraum]]** des [[Vektorräume|Vektorraums]], aus dem die Vektoren $\vec{x}$ stammen (wenn $A$ eine $m \times n$ Matrix ist, ist der Kern ein Unterraum von $\mathbb{R}^n$).
* Der Kern enthält immer mindestens den [[Nullvektor]] $\vec{x} = \vec{0}$ (die **triviale Lösung** des homogenen Systems).
* Die **Dimension** des Kerns wird als **Defekt** der Matrix bezeichnet: $\dim(\operatorname{Kern}(A))$.
* **[[Rang-Defekt-Theorem]]:** Für eine $m \times n$ Matrix $A$ besagt das [[Rang-Defekt-Theorem]], dass die Dimension des Kerns plus der [[Rang]] der Matrix gleich der Anzahl der Spalten ist:

    $$ \dim(\operatorname{Kern}(A)) + rg(A) = n $$

    Die Dimension des Kerns entspricht der Anzahl der **Nicht-[[Pivotelement|Pivot]]spalten** in der [[Reduzierte Zeilenstufenform (RZF)]] von $A$.

* Der Kern repräsentiert die Vektoren, die durch die lineare [[Transformation]], welche die Matrix $A$ darstellt, "ausgelöscht" oder auf Null reduziert werden. Im PDF wird dies als das, was die Matrix "nicht sieht" oder "neutralisiert", beschrieben.

**[[Berechnung]] einer [[Basis]] für den Kern:**

Um eine [[Basis]] für den Kern zu finden, löst man das [[Homogenes Lineares Gleichungssystem]] $A\vec{x} = \vec{0}$ mithilfe des [[Gauß-Algorithmus]]. Man bringt die erweiterte Matrix $(A|\vec{0})$ in [[Reduzierte Zeilenstufenform (RZF)]]. Die Variablen, die keiner [[Pivotelement|Pivot]]spalte entsprechen (die **freien Variablen**), können beliebig gewählt werden. Die [[Basis|Basisvektoren]] für den Kern werden erhalten, indem man für jede freie Variable einmal 1 und für die anderen freien Variablen 0 setzt und die entsprechenden Lösungen für die [[Pivotelement|Pivot]]variablen berechnet.

---

## Verwendung:

```dataview
list from [[Kern (Nullraum)]]
```