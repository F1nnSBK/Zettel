#Note

2026-05-19

Tags: [[Statistik]] , [[Stochastik]] , [[Wahrscheinlichkeitsrechnung]] , [[Unabhängigkeit]]
#stochastik 

---
Zwei Ereignisse $A$ und $B$ heißen **stochastisch unabhängig**, wenn das Eintreffen des einen Ereignisses die Wahrscheinlichkeit für das Eintreffen des anderen Ereignisses nicht beeinflusst.

### Die Multiplikationsregel (Formale Definition)

Mathematisch wird die Unabhängigkeit über die Schnittmenge definiert. Zwei Ereignisse $A$ und $B$ sind stochastisch unabhängig genau dann, wenn gilt:

$$P(A \cap B) = P(A) \cdot P(B)$$

### Äquivalenz zur bedingten Wahrscheinlichkeit

Aus der Definition der [[Bedingte Wahrscheinlichkeit|bedingten Wahrscheinlichkeit]] ergibt sich bei Unabhängigkeit sofort, dass die Bedingung "verpufft":

$$P(A \mid B) = \frac{P(A \cap B)}{P(B)} = \frac{P(A) \cdot P(B)}{P(B)} = P(A)$$

Analog gilt: $P(B \mid A) = P(B)$. Die Information, dass $B$ eingetreten ist, ändert die Erwartung für $A$ nicht.

### Extrem wichtige Abgrenzung: Unabhängig vs. Disjunkt

|**Konzept**|**Mathematische Bedingung**|**Intuitive Bedeutung**|
|---|---|---|
|**Disjunkt (Unvereinbar)**|$A \cap B = \emptyset$|Beide Ereignisse können **niemals gleichzeitig** passieren (schließen sich aus).|
|**Stochastisch Unabhängig**|$P(A \cap B) = P(A) \cdot P(B)$|Das Auftreten von $A$ hat **keinen Einfluss** auf die Chance von $B$.|

_Klausurfalle:_ Wenn zwei Ereignisse $A$ und $B$ disjunkt sind und positive Wahrscheinlichkeiten besitzen ($P(A), P(B) > 0$), dann sind sie **immer stochastisch abhängig**, da $P(A \cap B) = 0 \neq P(A) \cdot P(B)$.



---
#### Flashcards

Wie lautet die mathematische Definitionsformel für die stochastische Unabhängigkeit zweier Ereignisse?
?
$$P(A \cap B) = P(A) \cdot P(B)$$

Was gilt für die bedingte Wahrscheinlichkeit $P(B \mid A)$, wenn die Ereignisse $A$ und $B$ stochastisch unabhängig sind?
?
$$P(B \mid A) = P(B)$$(Die Bedingung $A$ liefert keine neue Information über $B$).

Warum sind zwei disjunkte Ereignisse mit $P(A) > 0$ und $P(B) > 0$ niemals stochastisch unabhängig?
?
Weil bei disjunkten Ereignissen gilt: $P(A \cap B) = 0$. Da aber $P(A) \cdot P(B) > 0$ ist, kann die Produktformel für Unabhängigkeit niemals erfüllt sein. Sie sind maximal abhängig, da das Eintreffen von $A$ das Eintreffen von $B$ komplett ausschließt.

Wie prüft man in einer Kontingenztabelle empirisch auf stochastische Unabhängigkeit?
?
Man prüft für jede einzelne Zelle, ob die relative Zellhäufigkeit $r_{ij}$ dem Produkt der dazugehörigen relativen Randhäufigkeiten ($r_{i.} \cdot r_{.j}$) entspricht.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Stochastische Unabhängigkeit]]
SORT file.mtime DESC
```