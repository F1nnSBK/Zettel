#Note

2025-12-03

Tags: [[]], [[]], [[]]

---
Bei **dynamischen Investitionsrechenverfahren** werden nicht [[Gewinn|Gewinne]] oder [[Erlöse]] betrachtet, sondern Ein- und Auszahlungen, die aus den [[Investitionsobjekt|Investitionsobjekten]] resultieren.
Es wird der Zahlungszeitpunkt berücksichtigt und damit mögliche Zinskosten oder Zinserträge. Grundprinzip ist hier, dass Zahlungsströme weniger Wert sind, desto ferner in der Zukunft sie liegen ([[Zeitwert des Geldes]]).

- **Wissen:**
    
    - **Unterschied Gewinn vs. Cash Flow:** CF ist zahlungsorientiert34. Gewinn ist periodenorientiert. **Nicht zahlungswirksam** sind z.B. kalkulatorische Kosten (AfA, kalk. Zinsen) und Bildung/Auflösung von Rückstellungen oder Forderungen/Verbindlichkeiten 35.
        
    - **Zeitwert des Geldes (Time Value of Money):** Ein Euro heute ist mehr wert als ein Euro in der Zukunft (wegen Zinsertrag)36363636.
        
    - **Aufzinsen (Compounding):** Wert einer heutigen Zahlung in der Zukunft bestimmen (Endwert)37.
        
    - **Abzinsen (Diskontierung):** Wert einer zukünftigen Zahlung heute bestimmen (Barwert)38.
        
- **Können (Formeln auswendig):**
    
    - Endwert (Future Value):
        
        $$EW_n = CF_0 \cdot (1+i)^n$$
        
        ( $CF_0$ = Heutiger Cash Flow, $i$ = Zinssatz, $n$ = Laufzeit) 39
        
    - Barwert (Present Value):
        
        $$BW_0 = \frac{CF_n}{(1+i)^n}$$
        
        ( $CF_n$ = Zukünftiger Cash Flow zum Zeitpunkt n) 40
        

#### 2. Kapitalwertmethode (Net Present Value, NPV)

- **Wissen:**
    
    - **Ziel:** Der Kapitalwert ist die **Summe aller auf heute abgezinsten (diskontierten) Ein- und Auszahlungen** einer Investition41.
        
    - **Interpretation:** $KW_0$ ist der Betrag, um den das Vermögen des Investors (über die Mindestverzinsung $i$ hinaus) heute steigt42.
        
    - **Entscheidungsregel:**
        
        - **$KW_0 > 0$:** Investition ist vorteilhaft (Vermögenszuwachs, Rendite > $i$)43. **Investieren!**
            
        - **$KW_0 = 0$:** Investition neutral (Rendite = $i$)44.
            
        - **$KW_0 < 0$:** Investition ist nachteilig (Vermögensminderung, Rendite < $i$)45. **Nicht investieren!**
            
    - **Vorteile:** Berücksichtigt Zeitwert des Geldes 46, basiert auf (schwerer manipulierbaren) Cash Flows47.
        
    - **Nachteil:** Ist eine absolute Kennzahl, keine relative (%)48.
        
- **Können (Formeln auswendig):**
    
    - Kapitalwert (KW / NPV):
        
        $$KW_0 = \sum_{t=0}^{n} \frac{CF_t}{(1+i)^t}$$
        
        49
        
    - Praktische Formel:
        
        $$KW_0 = -I_0 + \sum_{t=1}^{n} \frac{CF_t}{(1+i)^t} + \frac{R_n}{(1+i)^n}$$
        
        ( $I_0$ = Investition heute, $CF_t$ = Laufender Cash Flow in Periode t, $R_n$ = Restwert/Liquidationserlös in Periode n) 50
        

#### 3. Interne Zinsfußmethode (Internal Rate of Return, IRR)

- **Wissen:**
    
    - **Definition:** Der Interne Zinsfuß (IZF) ist derjenige Zinssatz ( $i$ ), bei dem der **Kapitalwert ($KW_0$) genau Null ist**5151.
        
    - **Interpretation:** Der IZF ist die **effektive, durchschnittliche Jahresrendite** des investierten Kapitals52.
        
    - **Entscheidungsregel:**
        
        - **$IZF > i$ (Kalkulationszinssatz/Kapitalkosten):** Investition vorteilhaft53.
            
        - **$IZF < i$:** Investition nachteilig.
            
    - **Kritik:** Kann bei unregelmäßigen Cash Flows (z.B. - + - +) mehrere oder keinen IZF geben. Bei widersprüchlichen Ergebnissen zwischen KW und IZF: **Immer der Kapitalwertmethode folgen!** (Maximiert den absoluten Vermögenszuwachs)54.
        
- **Können (Formel auswendig):**
    
    - Interne Zinsfuß (IZF / IRR):
        
        $$0 = -I_0 + \sum_{t=1}^{n} \frac{CF_t}{(1+i_{\text{IZF}})^t} + \frac{R_n}{(1+i_{\text{IZF}})^n}$$
        
        (Diese Gleichung muss nach $i_{\text{IZF}}$ aufgelöst werden, in der Klausur meist durch Probieren oder Interpolation, wenn nur 2-3 Perioden gegeben sind) 5555.
        

#### 4. Amortisationsrechnung (Payback Period)

- **Wissen:**
    
    - **Ziel:** Risikobeurteilung56. Fragt: **Wie lange dauert es, bis das investierte Kapital zurückgeflossen ist?**57.
        
    - **Entscheidungsregel:** Wähle die Alternative mit der **kürzesten Amortisationszeit (AZ)**58.
        
    - **Kritik:** Ignoriert alle Cash Flows _nach_ der Amortisationszeit 59, ignoriert Zeitwert des Geldes (in der statischen Variante), kein Rentabilitätsmaß6060. Dient nur als **Ergänzung/Risikoindikator**61616161.
        
- **Können (Formeln auswendig):**
    
    - Durchschnittsrechnung (vereinfacht, bei konstanten CFs):
        
        $$AZ = \frac{I_0}{\text{Durchschnittlicher Rückfluss (CF) pro Jahr}}$$
        
        62
        
    - Kumulationsrechnung (korrekt, bei variablen CFs):
        
        $$AZ = n + \frac{\text{Noch zu deckender Betrag (kum. CF bis n)}}{\text{Cash Flow des Folgejahres (t)}}$$
        
        ( $n$ = Letztes Jahr vor Amortisation (letztes Jahr mit negativem kum. CF)) 63

---
### Verwendung
```dataview
list from [[Dynamische Investitionsrechenverfahren]]
```