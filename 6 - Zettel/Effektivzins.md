#Note

2025-12-11

Tags: [[Grundlagen Finanzierung & Investition]], [[Finanzierung]]
#finance

---
Der **Effektivzins** ($i_{eff}$) beziffert die tatsächlichen, jährlichen Gesamtkosten eines Kredits in Prozent des Nettodarlehensbetrags. Er dient der **Vergleichbarkeit** verschiedener Kreditangebote (gemäß Preisangabenverordnung - PAngV).

#### 1. Unterschied zum Nominalzins

- **Nominalzins:** Nur die reine Vergütung für die Geldüberlassung.
- **Effektivzins:** Nominalzins + alle preisbestimmenden Faktoren:
    - [[Disagio]] (Auszahlungsverlust).
    - Bearbeitungsgebühren.
    - Tilgungsverrechnungstermine.
    - Zinsbindungsdauer.

#### 2. Berechnungsmethoden

A) Exakte Methode (Interner Zinsfuß)
Mathematisch exakt ist der Effektivzins derjenige Zinssatz, bei dem der Kapitalwert aller Ein- und Auszahlungen gleich Null ist ($KW_0 = 0$).
(Hinweis: Dies entspricht der [[Interne Zinsfußmethode|IRR-Methode]]). Nur iterativ lösbar.

B) Näherungsmethode (Uniform-Methode)
Für die Klausur (und ohne Finanzrechner) wird oft die Faustformel verwendet. Sie verteilt die einmaligen Kosten (Disagio) linear über die Laufzeit.

$$
i_{\text{eff}} \approx
\frac{\text{Nominalzins p.a.} \;(\text{€}) \;+\; \dfrac{\text{Disagio} \;(\text{€})}{\text{Laufzeit }(n)}}{\text{Auszahlungsbetrag} \;(\text{€})}
\cdot 100
$$

**Legende / Verweise**
- Nominalzins (p.a.): [[Nominalzins]]  
- Disagio: [[Disagio]]  
- Laufzeit \(n\): [[Laufzeit]]  
- Auszahlungsbetrag: [[Auszahlungsbetrag]]

bzw. in deiner Notation:

$$i_{eff} \approx \frac{Z + \frac{D}{n}}{A} \cdot 100$$

- $Z$: Jährliche Nominalzinszahlung in €
- $D$: Disagio / Kosten in € (Nennwert - Auszahlungsbetrag)
- $n$: Laufzeit in Jahren
- $A$: Auszahlungsbetrag (Nettokreditbetrag)
    

---
#### Flashcards

Was drückt der Effektivzins aus? :: Die tatsächlichen jährlichen Gesamtkosten eines Kredits (Vergleichsgröße für Kreditangebote).

Warum ist der Effektivzins bei einem Disagio höher als der Nominalzins? :: Weil das Disagio (Auszahlungsabschlag) wie eine zusätzliche Zinszahlung wirkt, die auf die Laufzeit umgelegt wird.
<!--SR:!2025-12-17,1,230-->

Wie lautet die Faustformel (Uniform-Methode) für den Effektivzins?
?
$$i_{eff} \approx \frac{\text{Nominalzins (€)} + \frac{\text{Disagio (€)}}{\text{Laufzeit}}}{\text{Auszahlungsbetrag}} \cdot 100$$
<!--SR:!2025-12-17,1,230-->

Welcher finanzmathematischen Methode entspricht die _exakte_ Berechnung des Effektivzinses? :: Der **Internen Zinsfußmethode** (IRR): Der Zins, bei dem der Kapitalwert der Zahlungsreihe Null ist.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Effektivzins]]
SORT file.mtime DESC
```