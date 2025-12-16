#Note

2025-12-08

Tags: [[Grundlagen Finanzierung & Investition]]
#finance

---
Die **Amortisationszeit** (Payback Period) ist der Zeitraum, innerhalb dessen das investierte Kapital wieder zurückgeflossen ist. Sie dient primär der **Risikobeurteilung** (Risikozeitspanne).

### Berechnung

1. Vereinfacht (bei konstanten Rückflüssen / Annuität):

$$AZ = \frac{I_0}{C}$$

- $I_0$: Investitionsausgabe
- $C$: Durchschnittlicher Rückfluss pro Jahr

2. Exakt (bei schwankenden Rückflüssen / Kumulationsmethode):

$$AZ = n + \frac{CF_{ua}}{CF_t}$$

- $n$: Anzahl der vollen Jahre vor der Amortisation
- $CF_{ua}$: Noch unamortisierter Restbetrag am Ende von Jahr $n$
- $CF_t$: Cash Flow im Jahr der Amortisation
    

### Entscheidungskriterium

- **Einzelinvestition:** Investieren, wenn $AZ \le$ vorgegebene Maximaldauer (Soll-Amortisationszeit).
    
- **Auswahlproblem:** Wähle die Alternative mit der **kürzesten Amortisationszeit**.

---
#### Flashcards

Wann wird die vereinfachte Amortisationsformel ($I_0 / C$) angewendet? :: Nur bei konstanten jährlichen Rückflüssen (Annuitäten).

Welches Entscheidungskriterium gilt bei der Amortisationsrechnung im Vergleich zweier Projekte? :: Wähle das Projekt mit der kürzeren Amortisationszeit.

Was ist der gravierendste Nachteil der Amortisationsrechnung? :: Sie ignoriert alle Zahlungsströme, die nach dem Amortisationszeitpunkt anfallen (und trifft keine Aussage über die Gesamtrentabilität).
<!--SR:!2025-12-17,1,230-->

Welche Funktion erfüllt die Amortisationsdauer in der Investitionsrechnung primär? :: Risikobeurteilung (Risikozeitspanne) und Liquiditätsprüfung.
<!--SR:!2025-12-17,1,230-->

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Amortisationszeit]]
SORT file.mtime DESC
```