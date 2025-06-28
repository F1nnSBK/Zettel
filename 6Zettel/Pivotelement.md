#Note

2025-05-15

Tags: [[Pivotelement]], [[Zeilenstufenform]], [[Reduzierte Zeilenstufenform]], [[Gauß-Algorithmus]], [[Rang]], [[Matrizen]], [[Lineare Algebra]]

---

Ein **[[Pivotelement]]** ist das **erste Element ungleich Null** in jeder **Nicht-Null-Zeile** einer [[Matrizen|Matrix]], die in [[Zeilenstufenform (ZSF)]] oder [[Reduzierte Zeilenstufenform (RZF)]] gebracht wurde.

**Eigenschaften und Bedeutung:**

* In der [[Zeilenstufenform]] liegt jedes [[Pivotelement]] in einer Spalte, die weiter rechts liegt als die Spalte des [[Pivotelement]]s in der darüber liegenden Zeile.
* In der [[Reduzierte Zeilenstufenform (RZF)]] ist jedes [[Pivotelement]] speziell gleich **1**, und alle anderen Elemente in der Spalte des [[Pivotelement]]s sind Null.
* Die Spalten, die [[Pivotelement]]e enthalten, werden als **[[Pivot]]spalten** bezeichnet.
* Die [[Pivotelement]]e sind entscheidend im [[Gauß-Algorithmus]], da sie verwendet werden, um Elemente unterhalb (und in der RZF auch oberhalb) in ihrer Spalte zu eliminieren.
* Die **Anzahl der [[Pivotelement]]e** in der [[Zeilenstufenform]] oder [[Reduzierte Zeilenstufenform]] einer Matrix ist gleich ihrem [[Rang]].

Das [[Pivotelement]] ist somit ein Indikator für die lineare Unabhängigkeit der Zeilen und die Struktur der Matrix nach der Anwendung des [[Gauß-Algorithmus]].

---

## Verwendung:

```dataview
list from [[Pivotelement]]
```