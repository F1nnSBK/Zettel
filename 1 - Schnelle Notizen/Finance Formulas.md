

---

# 🚀 Finance & Accounting - Ultimate Exam Guide

## 1. Investitionsrechnung (Algorithmik)

| **Methode**              | **Formel / Logik**                                                                                            | **Entscheidung**             |
| ------------------------ | ------------------------------------------------------------------------------------------------------------- | ---------------------------- |
| **Gewinn (Statisch)**    | $G = \text{Erlöse} - (\text{var. Kosten} + \text{fixe Kosten} + \text{Abschreib.} + \text{kalk. Zins})$       | Maximiere $G$                |
| **Kalk. Zinsen**         | $\frac{AK + RW}{2} \cdot i$ (Zinsen auf das **$\varnothing$ gebundene Kapital**)                              | Teil der Fixkosten           |
| **ROI (auf EBIT-Basis)** | $\frac{EBIT}{\varnothing \text{ gebundenes Kapital}} \cdot 100$                                               | Maximiere $\%$ (Effizienz)   |
| **Amortisation**         | $\frac{\text{Investitionssumme}}{\text{Cashflow pro Jahr}}$                                                   | Minimiere $t$                |
| **Kapitalwert ($C_0$)**  | $-I_0 + \sum_{t=1}^{n} \frac{CF_t}{(1+i)^t} + \frac{L}{(1+i)^n}$                                              | Wähle wenn $C_0 > 0$         |
| **Interner Zins (IZF)**  | Suche $i$, sodass $C_0(i) = 0$.<br><br>  <br><br>Bei Einmalzahlung: $i_{eff}=\sqrt[n]{\frac{CF_n}{CF_0}} - 1$ | Wähle wenn $i > \text{Zins}$ |
| **Annuität**             | $Annuität = C_0 \cdot \frac{(1+i)^n \cdot i}{(1+i)^n - 1}$                                                    | Maximiere Annuität           |
| **$i_{eff}$ (Näherung)** | $$<br>\frac{\text{Zins} + \frac{\text{Disagio}}{n}}{\text{Auszahlung}} \cdot 100<br>$$                        | Vergleiche Effektivkosten    |

---

## 2. Bilanz-Kennzahlen (Feature Engineering)

|**Feature**|**Formel**|**Bedeutung**|
|---|---|---|
|**EBIT**|Jahresüberschuss + Steuern + Zinsen|Operative Performance|
|**EBITDA**|EBIT + Abschreibungen|Cash-Proxy (ohne Accounting-Bias)|
|**EK-Rentabilität**|$\frac{\text{Gewinn}}{\text{EK}} \cdot 100$|Return for Shareholders ($> 10\%$)|
|**Umsatzrendite**|$\frac{\text{Gewinn}}{\text{Umsatz}} \cdot 100$|Marge ($> 5\%$)|
|**EK-Quote**|$\frac{\text{EK}}{\text{Gesamtkapital}} \cdot 100$|Stabilität / Bonität ($> 30\%$)|
|**Zinsdeckung**|$\frac{\text{EBIT}}{\text{Zinsaufwand}}$|Pleiterisiko ($> 2$)|
|**Dyn. Verschuldung**|$\frac{\text{Finanzschulden}}{OCF}$|Unter 7 Jahre (Rückzahlungsdauer)|
|**Kapitaldienstf.**|$\frac{OCF}{Zins + Tilgung}$|Überlebenswichtig ($> 1$)|

---
## 3. Kostenrechnung (KLR) & Deckungsbeitrag

|**Begriff**|**Formel**|**Bedeutung**|
|---|---|---|
|**Umsatz ($E$)**|$\text{Menge} (x) \cdot \text{Preis} (p)$|Erlöse aus dem Verkauf.|
|**Deckungsbeitrag ($DB$)**|$E - K_{var}$ oder $(p - k_{var}) \cdot x$|Betrag zur Deckung der Fixkosten.|
|**Stück-DB ($db$)**|$p - k_{var}$|Deckungsbeitrag pro verkaufter Einheit.|
|**Deckungsbeitragsquote ($DBQ$)**|$\frac{DB}{\text{Umsatz}} \cdot 100$|Anteil des Umsatzes zur Fixkostendeckung.|
|**Break-Even-Punkt ($x_{BE}$)**|$\frac{K_{fix}}{db}$|Menge, ab der Gewinn erzielt wird ($G=0$).|
|**Gesamtkosten ($K_{ges}$)**|$K_{fix} + K_{var}$|$K_{var} = \text{variable Stückkosten} \cdot x$.|

---

## 4. Bilanz-Basics (Data Structure)

- **Anschaffungskosten (AK):** Netto-Preis + Nebenkosten (Montage/Transport) - Rabatte/Skonti.
    
- **Niederstwertprinzip:** * **Umlaufvermögen:** Streng (Marktpreis < Buchwert? $\to$ Pflicht zur Abschreibung).
    
    - **Anlagevermögen:** Gemildert (Abschreibung nur bei dauerhafter Minderung).
        
- **Rückstellungen (§ 249 HGB):** Pflicht bei ungewissen Verbindlichkeiten (Wahrscheinlichkeit $> 50\%$ & Imparitätsprinzip).
    
- **Drohverluste:** Rückstellungspflicht bei verlustreichen schwebenden Geschäften.
    
- **Disagio:** Wahlrecht zur Aktivierung als ARAP; dient der sofortigen Senkung der Steuerlast.

---

## 5. Die "HGB-Checkliste" für Begründungen

1. **Vorsichtsprinzip:** Lieber zu arm als zu reich rechnen (Gläuberschutz).
    
2. **Imparitätsprinzip:** Verluste (z.B. Drohverluste, Rückstellungen) sofort buchen.
    
3. **Realisationsprinzip:** Gewinne erst buchen, wenn die Leistung beim Kunden ist.
    
4. **Niederstwertprinzip:** Im Umlaufvermögen (Waren/Rohstoffe) **immer** den niedrigsten Wert ansetzen (Marktpreis vs. Anschaffungskosten).