#Note

2025-12-15

Tags: [[Projektmanagement]], [[Controlling]], [[Kosten]], [[EVM]]
#pm

---
**Earned Value Management (EVM)** (Fertigstellungswertanalyse) ist eine Methode zur integrierten Überwachung von **Leistung (Scope)**, **Kosten** und **Terminen**. Sie erlaubt (im Gegensatz zum reinen Soll-Ist-Vergleich) eine verlässliche Prognose des Projektendes.

#### 1. Die drei Basiswerte
1. **Planned Value (PV):** _Planwert._ Was _sollte_ das Projekt zum Stichtag laut Plan kosten? (Geplanter Wert der Arbeit).
2. **Actual Cost (AC):** _Ist-Kosten._ Was _hat_ die bisher geleistete Arbeit tatsächlich gekostet?
3. Earned Value (EV): Fertigstellungswert. Welchen Wert hat die tatsächlich geleistete Arbeit laut Plan?
$$EV = \text{Gesamtbudget (BAC)} \cdot \text{Fortschrittsgrad (\%completed)}$$


_Beispiel:_ Wir wollten 10 Wände bauen (je 1.000 €).
- Geplant heute: 5 Wände (PV = 5.000 €).
- Fertig heute: 4 Wände (EV = 4.000 €).
- Kosten dafür: 4.500 € (AC = 4.500 €).

#### 2. Abweichungen (Variances)
Geben die absolute Abweichung in Geldeinheiten an.
- Cost Variance (CV): Kostenabweichung.

$$CV = EV - AC$$

    - $CV < 0$: Über Budget (Schlecht).
    
    - $CV > 0$: Unter Budget (Gut).
    
- Schedule Variance (SV): Zeitplanabweichung (in Euro!).
$$SV = EV - PV$$

    - $SV < 0$: Hinter Zeitplan (Schlecht).
    
    - $SV > 0$: Vor Zeitplan (Gut).
    

#### 3. Indizes (Performance Indices)
Geben die Effizienz an. Idealwert ist 1,0.
- Cost Performance Index (CPI): Kosteneffizienz.

$$CPI = \frac{EV}{AC}$$

    - $CPI < 1$: Wir bekommen weniger als 1 € Wert für jeden ausgegebenen Euro (Kostenproblem).
    
    - $CPI = 0,8$: Das Projekt ist 20% teurer als geplant.
        
- Schedule Performance Index (SPI): Zeiteffizienz.

$$SPI = \frac{EV}{PV}$$

    - $SPI < 1$: Wir arbeiten langsamer als geplant (Zeitproblem).


#### 4. Prognosen (Forecasting)
- **BAC (Budget at Completion):** Das ursprüngliche Gesamtbudget.
- **EAC (Estimate at Completion):** Erwartete Gesamtkosten am Ende (basierend auf aktueller Performance).
    - Formel (wenn aktuelle Abweichung typisch bleibt):
    $$EAC = \frac{BAC}{CPI}$$
        
- ETC (Estimate to Complete): Erwartete Restkosten bis zum Ende.
$$ETC = EAC - AC$$


---
#### Flashcards

Wie berechnet sich der Earned Value (EV) eines Projekts?
?
$$EV = \text{Gesamtbudget (BAC)} \cdot \text{Fortschrittsgrad (\%completed)}$$
<!--SR:!2025-12-17,1,210-->

Wie berechnet sich die Kostenabweichung (CV)? :: $CV = EV - AC$ (Earned Value minus Actual Cost).
<!--SR:!2025-12-17,1,210-->

Was sagt ein negativer SV-Wert aus ($SV < 0$)? :: Das Projekt hinkt dem Zeitplan hinterher (Behind Schedule).
<!--SR:!2025-12-17,1,210-->

Wie lautet die Formel für den CPI (Cost Performance Index)? :: $CPI = EV / AC$.
<!--SR:!2025-12-17,1,210-->

Was bedeutet $CPI > 1$? :: Das Projekt liegt unter dem Budget (kostengünstiger als geplant).
<!--SR:!2025-12-17,1,210-->

Wie prognostiziert man die Gesamtkosten (EAC), wenn der aktuelle Trend anhält? :: $EAC = BAC / CPI$.
<!--SR:!2025-12-17,1,230-->

Wofür steht die Abkürzung PV? :: Planned Value (Geplanter Wert zum Stichtag).
<!--SR:!2025-12-17,1,210-->


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Earned Value Management]]
SORT file.mtime DESC
```