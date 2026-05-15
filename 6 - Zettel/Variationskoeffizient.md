#Note

2026-05-15

Tags: [[Statistik]], [[Deskriptive Statistik]], [[Streuungsmasse]], [[Variationskoeffizient]]
#deskriptive_statistik

---
Der **Variationskoeffizient** ($v$) ist ein relatives [[Streuungsmaß]]. Er setzt die Standardabweichung ins Verhältnis zum [[Mittelwert]] und wird meist in Prozent angegeben.

### Definition und Formel

Er ist definiert als der Quotient aus [[Standardabweichung]] $s$ und [[Arithmetisches Mittel|arithmetischem Mittel]] $\bar{x}$:

$$v = \frac{s}{\bar{x}} \quad (\text{bzw. } v = \frac{s}{\bar{x}} \cdot 100\%)$$

### Warum relative Streuung?

Absolute Streuungsmaße wie die Standardabweichung hängen von der Maßeinheit und der Größenordnung der Daten ab.

- **Problem:** Ein Elefant wiegt im Schnitt 5.000 kg mit einer Schwankung von 100 kg. Eine Maus wiegt 20 g mit einer Schwankung von 5 g. Absolut streut der Elefant mehr ($100 > 0,005$), aber relativ zur eigenen Größe ist die Maus deutlich variabler.
- **Lösung:** Der Variationskoeffizient macht diese unterschiedlichen Skalen vergleichbar, da er **einheitenlos** ist.

### Voraussetzungen

1. **Metrisches Skalenniveau:** Erfordert eine Verhältnisskala (Ratio Scale).
2. **Positiver Mittelwert:** $\bar{x} > 0$. Bei negativen Werten oder Werten nahe Null ist die Kennzahl nicht interpretierbar oder mathematisch instabil.

---

### Flashcards

Warum ist der Variationskoeffizient einheitenlos?::Da sowohl die Standardabweichung als auch der Mittelwert dieselbe Einheit besitzen (z. B. Kilogramm), kürzt sich diese bei der Division $v = \frac{s}{\bar{x}}$ heraus.

Unter welcher Bedingung ist der Vergleich von Standardabweichungen zweier Datensätze irreführend?::Wenn die Datensätze stark unterschiedliche Mittelwerte haben oder in unterschiedlichen Einheiten gemessen werden. Hier ist der Variationskoeffizient das präzisere Vergleichsmaß.

Warum darf der Variationskoeffizient nicht für Temperaturen in Grad Celsius verwendet werden?
?
Weil Celsius eine Intervallskala ist und keinen natürlichen Nullpunkt besitzt. Da der Mittelwert im Nenner steht, würde eine Verschiebung des Nullpunkts (z. B. Umrechnung in Kelvin) den Wert des Variationskoeffizienten willkürlich verändern.

Wie verändert sich der Variationskoeffizient, wenn alle Messwerte eines Datensatzes mit dem Faktor 5 multipliziert werden?
?
Er bleibt **gleich**. Da sich sowohl die Standardabweichung als auch der Mittelwert bei einer Multiplikation verfünffachen, bleibt ihr Verhältnis (der Quotient) konstant.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Variationskoeffizient]]
SORT file.mtime DESC
```