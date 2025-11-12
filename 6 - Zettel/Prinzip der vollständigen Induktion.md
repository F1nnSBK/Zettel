#Note

2025-11-12

Tags: [[Natürliche Zahlen]], [[Analysis 1]], [[Königsberger]]

---
Das **Prinzip der vollständigen Induktion** ist eine grundlegende [[Beweistechnik]] für Aussagen $A(n)$, die für alle [[Natürliche Zahlen|natürlichen Zahlen]] $n$ gelten sollen.

Die Aussagen $A(n)$ sind korrekt, wenn $(I)$ und $(II)$ bewiesen werden können:
+ $(I)$ Induktionsanfang: $A(1)$ ist richtig.
+ $(II)$ Induktionsschluss: Für jedes $n$, für das $A(n)$ richtig ist, muss auch $A(n+1)$ gelten.

Das **Induktionsprinzip** kann nicht nur als Beweistechnik, sondern auch als Werkzug zur Definition [[mathematische Struktur|mathematischer Objekte]] dienen. Das nennt man **Konstruktion durch vollständige Induktion** oder auch **reukursive Definition**. Der Aufbau folgt dem Muster der Beweistechnik.

+ $(I)$ Basisfall: Der erste Wert wird festgelegt $f(1)$
+ $(II)$ Vorschrift $F$ (Rekursionsschritt), welche die Berechnung des Elements $f(n+1)$ für alle $n \in \mathbb{N}$ ermöglicht.

Beispiel der Potenzen:
+ $(I)$ Basisfall $f(1)$: $x^1\coloneqq x$
+ $(II)$ Rekursionssatz $f(n+1)$: $x^{n+1}\coloneqq x^{n} \cdot x$

Takeaways:
- **Beweisprinzip:** "Von $A(n)$ auf $A(n+1)$ _schließen_.
- **Konstruktionsprinzip:** "Von $f(n)$ auf $f(n+1)$ _aufbauen_.

---
### Verwendung
```dataview
list from [[Prinzip der vollständigen Induktion]]
```