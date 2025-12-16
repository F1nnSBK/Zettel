#Note

2025-12-14

Tags: [[Kosten- und Leistungsrechnung]], [[Kostenstellenrechnung]], [[BAB]]
#finance

---
Die **Kostenstellenrechnung** beantwortet die Frage: **Wo** sind die Kosten angefallen? Sie dient als Bindeglied zwischen der Kostenartenrechnung (Welche Kosten?) und der Kostenträgerrechnung (Wofür/Preiskalkulation).


![[kostenstellenrechnung.jpeg]]

#### 1. Der Betriebsabrechnungsbogen (BAB)

Das zentrale Werkzeug ist der BAB. Er verteilt die Gemeinkosten auf die Kostenstellen.
**Ablauf (Klausur-Checkliste):**
1. Primärkostenverteilung:
    Verteilung der Gemeinkosten auf alle Kostenstellen (Hilfs- und Hauptkostenstellen).
    - _Direkt:_ Über Belege (z.B. Entnahmeschein für Büromaterial, Stromzähler).
    - _Indirekt:_ Über **Verteilungsschlüssel** (wenn keine Zähler vorhanden).
        
2. Sekundärkostenverrechnung (IBL):
    Die Kosten der Hilfskostenstellen (Strom, Kantine, Reparatur) werden auf die Hauptkostenstellen umgelegt.
    - _Ziel:_ Hilfskostenstellen müssen am Ende auf **0,00 €** stehen!
        
3. Ermittlung der Zuschlagssätze:
    Berechnung der %-Sätze für die Endkalkulation.
    $$\text{GK-Zuschlagssatz} = \frac{\text{Gemeinkosten der Hauptkostenstelle}}{\text{Einzelkosten (Basis)}} \cdot 100$$
    

**Typische Fehlerquellen im BAB (Plausibilitäts-Check):**
- Summe der Verteilungsschlüssel (Zeile) muss **100 %** (bzw. 1/1) ergeben.
- Nach der Sekundärkostenverrechnung muss die Summe aller Kostenstellen gleich der Summe der Primärkosten sein (Kosten gehen nicht verloren, sie wandern nur).
- Hilfskostenstellen sind am Ende nicht entlastet (Wert $\neq 0$).

#### 2. Verteilungsschlüssel (Mengenschlüssel)
Wenn Kostenstelleneinzelkosten nicht direkt erfasst werden können (z.B. keine Zähler), werden Hilfsgrößen genutzt.

|**Schlüsselart**|**Beispiele**|
|---|---|
|**Menge/Zahl**|Anzahl Mitarbeiter (für Kantine), Anzahl Buchungen, Anzahl Telefone.|
|**Zeit**|Arbeitsstunden, Maschinenstunden.|
|**Raum**|Quadratmeter ($m^2$) für Miete/Heizung, Kubikmeter ($m^3$) umbauter Raum.|
|**Technik**|Anschlusswerte (kWh), PS, Gewicht.|

#### 3. Innerbetriebliche Leistungsverrechnung (IBL)
Verfahren zur Verteilung der Hilfskostenstellenkosten.
- **Anbauverfahren:** Ignoriert Beziehungen zwischen Hilfskostenstellen (ungenau).
- **Stufenleiterverfahren:** Verrechnet nur in eine Richtung (besser).
- **Gleichungsverfahren:** Mathematisch exakt. Berücksichtigt den gegenseitigen Leistungsaustausch (z.B. Stromstelle braucht Reparatur, Reparaturstelle braucht Strom).
    

Das Gleichungsverfahren (Mathematischer Ansatz):
Man stellt ein lineares Gleichungssystem auf.

$$\text{Primärkosten} + \text{empfangene Leistung} = \text{abgegebene Leistung} \cdot \text{Verrechnungspreis } q$$

**Beispielrechnung:**
- Primärkosten Stromstelle: **3.120 €**
- Gesamtproduktion Strom: 1.000 (Eigen) + 5.000 + 5.000 + 500 + 1.000 + 500 = **13.000 kWh**
- Eigenverbrauch: **1.000 kWh**

_Ansatz:_ Die Kostenstelle muss ihre gesamten Kosten (3.120 €) auf die _netto_ abgegebene Menge verteilen (oder mathematisch den Eigenverbrauch mitbewerten).

$$\text{Gesamtmenge} \cdot q = \text{Primärkosten} + (\text{Eigenverbrauch} \cdot q)$$

$$13.000 \cdot q = 3.120 + 1.000 \cdot q \quad | -1.000 q$$

$$12.000 \cdot q = 3.120$$

$$q = \frac{3.120}{12.000} = \mathbf{0,26 \text{ €/kWh}}$$

Verteilung:
Die 0,26 € werden nun mit dem Verbrauch der anderen Stellen multipliziert (z.B. Fertigung I: $5.000 \cdot 0,26 = 1.300 €$).

---
#### Flashcards

Was ist die Hauptaufgabe der Kostenstellenrechnung? :: Die Verteilung der Gemeinkosten auf den Ort ihrer Entstehung und die Ermittlung von Zuschlagssätzen.

Was passiert bei der "Primärkostenverteilung" im BAB? :: Gemeinkosten werden entweder direkt (Belege) oder indirekt (Schlüssel) auf die Kostenstellen verteilt.

Was ist das Ziel der "Sekundärkostenverrechnung"? :: Die Kosten der **Hilfskostenstellen** auf die Hauptkostenstellen umzulegen (Hilfskostenstellen sind danach auf 0).
<!--SR:!2025-12-17,1,230-->

Welches Verfahren der innerbetrieblichen Leistungsverrechnung ist mathematisch am genauesten? :: Das **Gleichungsverfahren** (berücksichtigt gegenseitigen Leistungsaustausch und Eigenverbrauch).

Wie lautet der mathematische Ansatz beim Gleichungsverfahren für eine Kostenstelle? :: $\text{Primärkosten} + \text{Sekundärkosten} = \text{Gesamtleistung} \times \text{Verrechnungspreis}$.

Auf welcher Basis werden Gemeinkostenzuschlagssätze im BAB berechnet? :: Als prozentualer Aufschlag auf die **Einzelkosten** der jeweiligen Hauptkostenstelle.

Nenne drei Beispiele für Mengenschlüssel zur Kostenverteilung. :: Quadratmeter (Miete), Mitarbeiterzahl (Kantine), Maschinenstunden (Energie/Abschreibung).
<!--SR:!2025-12-17,1,230-->

Woran erkennt man im BAB, dass die Sekundärkostenverrechnung abgeschlossen ist? :: Die Summe der Kosten in den **Hilfskostenstellen** ist Null.



---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Kostenstellenrechnung]]
SORT file.mtime DESC
```