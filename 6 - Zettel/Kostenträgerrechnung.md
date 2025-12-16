#Note

2025-12-15

Tags: [[Kosten- und Leistungsrechnung]], [[Kostenträgerrechnung]], [[Kalkulation]]
#finance

---
Die Kostenträgerrechnung ist die dritte und letzte Stufe der KLR.
Zentrale Frage: Wofür sind die Kosten angefallen? (Stückerfolgsrechnung).

#### 1. Grundlagen
Was sind Kostenträger?
Alle Leistungen, die Kosten verursacht haben.
- **Marktleistungen:** Für den Absatz bestimmt (verkaufte Produkte $x_a$ oder Lagerbestand $x_p$).
- **Innerbetriebliche Leistungen:** Selbst erstellte Anlagen (aktivierbar) oder Gemeinkostenleistungen (nicht aktivierbar).
    

**Aufgaben der Kostenträgerrechnung (Mind. 3 kennen!):**
1. **Preispolitik:** Ermittlung von Preisuntergrenzen (kurzfristig/langfristig) und Preisobergrenzen.
2. **Bewertung:** Herstellkosten für die Bilanzbewertung (Vorräte) nach HGB.
3. **Erfolgsermittlung:** Stückerfolg (Preis - Kosten) und Periodenerfolg.
4. **Planung & Kontrolle:** Soll-Ist-Vergleiche, Make-or-Buy-Entscheidungen.
    

**Wichtige Unterscheidung der Mengen:**
- **Herstellkosten:** Beziehen sich auf die _produzierte_ Menge ($x_p$).
- Selbstkosten: Beziehen sich auf die verkaufte Menge ($x_a$).
    (Differenz = Bestandsveränderung im Lager)

![[kostenträgerrechnung.jpeg]]

---

#### 2. Kalkulationsverfahren
Die Wahl des Verfahrens hängt vom Fertigungstyp ab.

|**Verfahren**|**Anwendungsbereich**|
|---|---|
|**Divisionskalkulation**|Ein-Produkt-Unternehmen (Massenfertigung, z.B. Strom, Zement).|
|**Äquivalenzziffernkalkulation**|Sortenfertigung (Artverwandte Produkte, z.B. Brauerei, Walzwerk).|
|**Zuschlagskalkulation**|Einzel- und Serienfertigung (Heterogene Produkte, z.B. Maschinenbau).|

---

#### 3. Die Äquivalenzziffernkalkulation

Dient dazu, Kosten artverwandter Produkte mittels Verhältniszahlen (Äquivalenzziffern) vergleichbar zu machen.
Beispiel Schokolade (Gewicht): 50g : 100g : 400g $\rightarrow$ ÄZ $1 : 2 : 8$.
Beispiel Eiffelturm (Volumen): Höhe 5cm : 15cm : 30cm.
- Längenverhältnis: $1 : 3 : 6$.
- Volumenverhältnis (kubisch!): $1^3 : 3^3 : 6^3 \rightarrow \mathbf{1 : 27 : 216}$.
    

![[äquivalenzziffern.jpeg]]

**Rechenschema:**
1. **Einheitsmenge bestimmen:** $\text{Produktionsmenge } m_i \cdot \text{ÄZ } a_i = \text{Recheneinheiten}$.
2. **Kosten pro Einheit ($k'$):** $\frac{\text{Gesamtkosten}}{\sum \text{Recheneinheiten}}$.
3. **Stückkosten der Sorte:** $k' \cdot \text{ÄZ } a_i$.

| **Sorte** | **Menge ($m_i$​)** | **ÄZ ($a_i$​)** | **Recheneinheiten RE ($m_i$​⋅$a_i​$)** | **Kosten je Sorte**    | **Stückkosten ($k_{Sorte}$​)** |
| --------- | ------------------ | --------------- | -------------------------------------- | ---------------------- | ------------------------------ |
| **A**     | $m_1$              | $a_1$           | $m_1 \cdot a_1$                        | $\text{RE}_1 \cdot k'$ | $k' \cdot a_1$                 |
| **B**     | $m_2$              | $a_2$           | $m_2 \cdot a_2$                        | $\text{RE}_2 \cdot k'$ | $k' \cdot a_2$                 |
| **Summe** |                    |                 | $\sum \text{RE}$                       | $K_{gesamt}$           |                                |

---

#### 4. Die Zuschlagskalkulation (Differenzierend)

Trennung in Einzel- und Gemeinkosten.
Zentrale Formel für Zuschlagssätze:

$$\text{Zuschlagssatz} (\%) = \frac{\text{Gemeinkosten}}{\text{Bezugsbasis (Einzelkosten)}} \cdot 100$$

**Kalkulationsschema:**

|**Position**|**Kostenart**|**Berechnung / Anmerkung**|
|---|---|---|
|**+**|**Fertigungsmaterial (MEK)**|Materialeinzelkosten (direkte Zurechnung)|
|+|Materialgemeinkosten (MGK)|(In der Regel als %-Satz von MEK)|
|**=**|**Materialkosten (MK)**|Summe aus MEK + MGK|
|+|Fertigungslöhne (FEK)|Fertigungseinzelkosten (direkte Zurechnung)|
|+|Fertigungsgemeinkosten (FGK)|(In der Regel als %-Satz von FEK)|
|+|Sondereinzelkosten der Fertigung|Z.B. spezielle Werkzeuge, Patente|
|**=**|**Fertigungskosten (FK)**|Summe aus FEK + FGK + Sondereinzelkosten d. Fertigung|
|**=**|**Herstellkosten (HK) der Erzeugung**|(HK bezogen auf die produzierte Menge $x_p$)|
|+/-|Bestandsveränderung|Erhöhung/Verminderung des Bestands an fertigen/unfertigen Erzeugnissen|
|**=**|**Herstellkosten (HK) des Umsatzes**|(HK bezogen auf die abgesetzte Menge $x_a$)|
|+|Verwaltungsgemeinkosten (VwGK)|(Als %-Satz von HK d. Erzeugung/Umsatz)|
|+|Vertriebsgemeinkosten (VtGK)|(Als %-Satz von HK d. Erzeugung/Umsatz)|
|+|Sondereinzelkosten des Vertriebs|Z.B. Provisionen, Verpackungskosten|
|**=**|**Selbstkosten (SK)**|Kosten des gesamten abgesetzten Umsatzes|

_(Hinweis: Basis für VwGK/VtGK sind in der Regel die HK des Umsatzes)._

---
#### 5. Handelskalkulation

Hier fallen keine Fertigungskosten an. Wichtig sind die Umrechnungsfaktoren.

![[handelskalk.jpeg]]

**Formeln:**
1. Handelsspanne (in % vom VK):
    $$HS = \frac{VK - EK}{VK} \cdot 100$$
    
2. Kalkulationszuschlag (in % vom EK):
    $$KZ = \frac{VK - EK}{EK} \cdot 100$$
    
3. Kalkulationsfaktor (Multiplikator):
    $$KF = \frac{VK}{EK} = 1 + \frac{KZ}{100}$$
    

Übung 1: Fahrradtour
Gegeben: $VK = 400 €$, $HS = 60 \%$.
Gesucht: Einstandspreis (EK), Kalkulationszuschlag (KZ), Faktor (KF).

- **EK:** $400 € \cdot (1 - 0,60) = 160 €$.
- **KF:** $\frac{VK}{EK} = \frac{400}{160} = \mathbf{2,5}$.
- **KZ:** $(KF - 1) \cdot 100 = \mathbf{150 \%}$.

Übung 2: Perlenglanz (Rückwärtskalkulation)
Ist das Angebot gewinnbringend bei 45% Ziel-Handelsspanne?

1. Listeneinkaufspreis: 420,00 €
2. - Lieferantenrabatt (10%): 42,00 €
3. = Zieleinkaufspreis: 378,00 €
4. - Lieferantenskonto (2%): 7,56 €
5. = Bareinkaufspreis: 370,44 €
6. - Bezugskosten: 10,60 €
7. **= Bezugspreis (Einstandspreis): 381,04 €**
    

**Check:**
- Netto-Verkaufspreis: 680,00 €
- Tatsächliche Handelsspanne: $\frac{680 - 381,04}{680} = \mathbf{43,96 \%}$
- **Ergebnis:** Die Zielspanne von 45% wird **nicht** erreicht (Angebot ist knapp unter Zielvorgabe).
    

---
#### Flashcards

Was ist die zentrale Frage der Kostenträgerrechnung? :: **Wofür** sind die Kosten angefallen? (Ermittlung der Stückkosten).

Nenne drei Aufgaben der Kostenträgerrechnung. :: Preispolitik (Preisuntergrenzen), Bewertung (Bilanzansatz Vorräte), Planung & Kontrolle (Soll-Ist-Vergleich), Erfolgsermittlung.

Auf welche Menge beziehen sich die Herstellkosten? :: Auf die **produzierte** Menge ($x_p$).

Auf welche Menge beziehen sich die Selbstkosten (und Vertriebskosten)? :: Auf die **verkaufte** Menge ($x_a$).

Wann wendet man die Äquivalenzziffernkalkulation an? :: Bei **Sortenfertigung** (artverwandte Produkte, die sich nur in Größe/Material unterscheiden, z.B. Bier, Ziegel).
<!--SR:!2025-12-17,1,230-->

Wie steigen die Äquivalenzziffern bei einer Volumenänderung (z.B. Würfel Kantenlänge)? :: **Kubisch** (hoch 3). Wenn Länge verdoppelt (Faktor 2), verachtfacht sich das Volumen (Faktor 8).
<!--SR:!2025-12-17,1,230-->

Wie lautet die Formel für den Gemeinkostenzuschlagssatz?
?
$$\text{Zuschlagssatz} = \frac{\text{Gemeinkosten}}{\text{Einzelkosten}} \cdot 100$$

Was ist die Bezugsbasis für den Materialgemeinkostenzuschlag? :: Das **Fertigungsmaterial** (Materialeinzelkosten).

Was ist die Bezugsbasis für den Verwaltungsgemeinkostenzuschlag? :: Die **Herstellkosten** (des Umsatzes).

Wie lautet die Formel für die Handelsspanne?
?
$$HS = \frac{\text{Verkaufspreis} - \text{Einstandspreis}}{\text{Verkaufspreis}} \cdot 100$$

Wie lautet die Formel für den Kalkulationszuschlag?
?
$$KZ = \frac{\text{Verkaufspreis} - \text{Einstandspreis}}{\text{Einstandspreis}} \cdot 100$$

Wie hängen Kalkulationsfaktor (KF) und Kalkulationszuschlag (KZ) zusammen? :: $KF = 1 + KZ$ (als Dezimalzahl). Beispiel: $KZ = 50\% \rightarrow KF = 1,5$.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Kostenträgerrechnung]]
SORT file.mtime DESC
```