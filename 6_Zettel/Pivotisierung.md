#Note

2025-05-17

Tags: [[Pivotisierung]], [[LU-Zerlegung]], [[Gauß-Algorithmus]], [[Matrizen]], [[Lineare Algebra]], [[Pivotelement]], [[Permutationsmatrix]]

---

**Pivotisierung** ist ein Schritt, der in bestimmten Matrixalgorithmen, wie dem [[Gauß-Algorithmus]] oder der [[LU-Zerlegung]], angewendet wird und das **Vertauschen von Zeilen** (und manchmal Spalten) beinhaltet. Der Hauptzweck ist, sicherzustellen, dass ein geeignetes [[Pivotelement]] (ungleich Null) für die Eliminationsschritte zur Verfügung steht und/oder die numerische Stabilität des Algorithmus zu verbessern.

**Warum ist Pivotisierung notwendig?**

Bei der [[LU-Zerlegung]] in der einfachen Form $A=LU$ kann es zu Problemen kommen, wenn während des [[Gauß-Algorithmus]] ein notwendiges [[Pivotelement]] Null ist. Eine Division durch Null wäre dann nicht möglich, und die Zerlegung schlägt fehl. Pivotisierung löst dieses Problem, indem eine Zeile mit einem Nicht-[[Pivotelement|Null]]-Eintrag an die aktuelle [[Pivotelement|Pivot]]position verschoben wird.

**Arten der Pivotisierung:**

Die am häufigsten verwendeten Arten sind:

1.  **Partielle Pivotisierung:** Hierbei wird in der aktuellen [[Pivotelement|Pivot]]spalte die aktuelle Zeile mit der Zeile **unterhalb** vertauscht, die den Eintrag mit dem **größten Absolutwert** in dieser Spalte aufweist. Dies verbessert auch die numerische Stabilität, da Divisionen durch kleine Zahlen vermieden werden. Wenn partielle Pivotisierung angewendet wird, ergibt sich die Zerlegung $PA = LU$, wobei $P$ eine [[Permutationsmatrix|Permutationsmatrix]] ist, die die Zeilenvertauschungen aufzeichnet. $PA=LU$ existiert für jede [[Invertierbarkeit|invertierbare Matrix]] $A$.
2.  **Volle Pivotisierung:** Hierbei wird in der verbleibenden Untermatrix nach dem Eintrag mit dem **größten Absolutwert** gesucht. Dessen Zeile wird an die aktuelle [[Pivotelement|Pivot]]zeile und dessen Spalte an die aktuelle [[Pivotelement|Pivot]]spalte vertauscht. Dies erfordert sowohl Zeilen- als auch Spaltenvertauschungen und führt zur Form $PAQ = LU$, wobei $P$ die Zeilen- und $Q$ die Spaltenvertauschungen aufzeichnet. Volle Pivotisierung bietet die höchste numerische Stabilität, ist aber rechnerisch aufwendiger.

**Rolle bei der [[Berechnung]]:**

Wenn Pivotisierung angewendet wird, muss die [[Permutationsmatrix|Permutationsmatrix]] (oder die Abfolge der Vertauschungen) aufgezeichnet werden. Bei der Lösung von Systemen $A\vec{x}=\vec{b}$ mit $PA=LU$ löst man $LU\vec{x}=P\vec{b}$, also $L\vec{y}=P\vec{b}$ (Vorwärtseinsetzen mit vertauschtem $\vec{b}$) und dann $U\vec{x}=\vec{y}$ (Rückwärtseinsetzen).

---

## Verwendung:

```dataview
list from [[Pivotisierung]]
```