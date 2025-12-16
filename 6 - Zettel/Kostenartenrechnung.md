#Note

2025-12-14

Tags: [[Grundlagen Finanzierung & Investition]], [[Grundlagen Kosten & Leistungsrechnung]], [[Kostenartenrechnung]] 
#finance

---
Die Kostenartenrechnung ist die erste Stufe der KLR.
Zentrale Frage: Welche Kosten sind in welcher Höhe entstanden?

#### 1. Gliederung der Kostenarten

Kosten lassen sich nach verschiedenen Kriterien systematisieren:

|**Gliederungskriterium**|**Bezeichnung & Unterscheidung**|
|---|---|
|**Nach Zurechenbarkeit**<br><br>  <br><br>(Verursacherprinzip)|**[[Einzelkosten]]:** Dem Kostenträger (Produkt) _direkt_ zurechenbar (z.B. Holz beim Tisch).<br><br>  <br><br>**[[Gemeinkosten]]:** Dem Kostenträger _nicht_ direkt zurechenbar; Verteilung über Kostenstellen (z.B. Miete der Halle).|
|**Nach Beschäftigungsabhängigkeit**<br><br>  <br><br>(Verhalten bei Mengenänderung)|**Variable Kosten:** Ändern sich mit der Produktionsmenge (atmen mit).<br><br>  <br><br>**Fixe Kosten:** Bleiben bei Beschäftigungsänderungen konstant (Bereitschaftskosten).|
|**Nach Art der Produktionsfaktoren**|Materialkosten, Personalkosten, Dienstleistungskosten, Kalk. Kosten.|

---

#### 2. Kostenfunktionen & Verlauf

Die Gesamtkostenfunktion: $K(x) = K_{fix} + K_{var}(x)$
Vereinfachter Ansatz: $K(x) = a \cdot x^b + K_f$

**A) Variable Kosten** (Reagieren auf Beschäftigung $x$)
- **Proportionale Kosten ($b=1$):** Steigen linear mit der Menge. Stückkosten bleiben konstant.
    
    - _Beispiel:_ Akkordlohn, Rohstoffverbrauch.
- **Degressive Kosten ($0 < b < 1$):** Steigen langsamer als die Menge (Rabatte bei großen Mengen).
- **Progressive Kosten ($b > 1$):** Steigen schneller als die Menge (Überstundenzuschläge).
    

**B) Fixe Kosten** (Reagieren nicht auf $x$)
- **Absolute fixe Kosten:** $K(x) = a$ (z.B. Miete).
- **Sprungfixe Kosten (Intervallfix):** Kosten steigen sprunghaft bei Kapazitätserweiterung (z.B. Kauf einer zweiten Maschine).
    

**C) Durchschnitts- und Grenzkosten**
- Durchschnittskosten (Stückkosten):
	$$k(x) = \frac{K(x)}{x}$$
    Hinweis: Bei fixen Kosten sinken die Stückkosten mit steigender Menge (Fixkostendegression).
    
- Grenzkosten: Kosten der letzten produzierten Einheit (1. Ableitung).
	$$K'(x) = \frac{dK}{dx}$$
    

---
#### 3. Abgrenzungs-Matrix (Beispiele)

Hier erfolgt die Einordnung in die Raster "Einzel/Gemein" und "Fix/Variabel".
Faustregel: Kalkulatorische Kosten sind in der Regel Fixe Gemeinkosten.

|**Kostenart**|**Einzelkosten**|**Gemeinkosten**|**Fixe Kosten**|**Variable Kosten**|
|---|---|---|---|---|
|**Fertigungslöhne** (Akkord)|x|||x|
|**Hilfslöhne**||x||x|
|**Gehalt für Meister**||x|x||
|**Kalk. Abschreibung**||x|x||
|**Kalk. Zinsen**||x|x||
|**Mieten**||x|x||
|**Energiekosten** (Maschinen)||x||x|
|**Betriebsstoffe** (Schmiermittel)||x||x|
|**Rohstoffe** (z.B. Miene/Klammer)*|x|||x|

_*Hinweis: Kleinteile (C-Teile) wie Klammern werden oft als "Unechte Gemeinkosten" behandelt, um den Erfassungsaufwand zu sparen, sind theoretisch aber Einzelkosten._

---

#### 4. Ermittlung des Materialverbrauchs

Wie viel Material wurde verbraucht?
1. Inventurmethode (Befundrechnung):
    
    Verbrauch wird durch Zählen ermittelt (IST).
    
    $$Verbrauch = \text{Anfangsbestand} + \text{Zugänge} - \text{Endbestand}$$
    
    Nachteil: Keine Info, wofür das Material verbraucht wurde (Schwund/Diebstahl nicht erkennbar).
    
2. Skontrationsmethode (Fortschreibung):
    Verbrauch laut Materialentnahmescheinen (IST).
    
    $$Verbrauch = \sum \text{Materialentnahmescheine}$$
    
3. Retrograde Methode (Rückrechnung):
    Verbrauch wird aus den produzierten Stückzahlen abgeleitet (SOLL).
    
    $$Verbrauch = \text{Produzierte Menge} \cdot \text{Soll-Verbrauch pro Stück}$$
    
    Nachteil: Ungenau, da Ausschuss nicht erfasst wird.

4. Behelfsmethode (Zugang = Abgang)


---
#### 5. Kalkulatorische Kosten

Kosten, denen in der FiBu kein Aufwand gegenübersteht (Zusatzkosten) oder in anderer Höhe (Anderskosten).

A) Kalkulatorische Abschreibung
Basis ist der Wiederbeschaffungswert (WBW), nicht die Anschaffungskosten (AK), um die Substanz real zu erhalten.

$$Abschreibung_{kalk} = \frac{WBW - RW}{\text{Nutzungsdauer } n}$$

$$WBW = AW \cdot (1 + \text{Inflationsrate})^n$$

B) Kalkulatorische Zinsen

Verzinsung des betriebsnotwendigen Kapitals (EK & FK). Man nutzt die Durchschnittsmethode.

- Ohne Restwert:
    $$\text{Kalk. Zinsen} = \frac{AW}{2} \cdot i$$
    
- Mit Restwert (RW):
    $$\text{Kalk. Zinsen} = \frac{AW + RW}{2} \cdot i$$
    

Beispiel: Maschine für 200.000 €, RW 40.000 €, $i=5\%$.
Kapitalbindung $\O = \frac{200.000 + 40.000}{2} = 120.000 €$.
Zinsen $= 120.000 \cdot 0,05 = 6.000€$.

---
#### Flashcards (Kostenartenrechnung)

Was ist die zentrale Frage der Kostenartenrechnung? :: **Welche** Kosten sind in welcher Höhe entstanden?
<!--SR:!2025-12-17,1,230-->

Was sind Einzelkosten? :: Kosten, die einem Kostenträger (Produkt) **direkt** zugerechnet werden können (z.B. Fertigungsmaterial, Akkordlohn).

Was sind Gemeinkosten? :: Kosten, die einem Kostenträger **nicht direkt** zugerechnet werden können und über Kostenstellen verteilt werden müssen (z.B. Miete, Gehälter, Strom).

Was sind variable Kosten? :: Kosten, die sich bei einer Änderung der Beschäftigung (Produktionsmenge) verändern (z.B. Rohstoffe).

Was sind fixe Kosten? :: Kosten, die unabhängig von der Beschäftigung (in einem bestimmten Intervall) konstant bleiben (z.B. Miete, zeitabhängige Abschreibung).
<!--SR:!2025-12-17,1,230-->

Was versteht man unter Fixkostendegression? :: Das Sinken der **Stückkosten** bei steigender Produktionsmenge, da sich die Fixkosten auf mehr Einheiten verteilen.

Wie lautet die Formel für die Inventurmethode (Materialverbrauch)?
?
$$Verbrauch = \text{Anfangsbestand} + \text{Zugänge} - \text{Endbestand}$$

Wie funktioniert die Retrograde Methode (Materialverbrauch)? :: Rückrechnung vom Output auf den Input: $\text{Produktionsmenge} \times \text{Sollverbrauch pro Stück}$.

Wie funktioniert die Skontrationsmethode (Fortschreibung)?
?
Verbrauch laut Materialentnahmescheinen (IST).
$$Verbrauch = \sum \text{Materialentnahmescheine}$$

Wie kann eine Behelfsmethode aussehen? :: Zugänge = Abgänge

Worauf basiert die kalkulatorische Abschreibung (im Gegensatz zur bilanziellen)? :: Auf dem **Wiederbeschaffungswert** (statt Anschaffungskosten) und der tatsächlichen Nutzungsdauer.

Wie lautet die Formel für kalkulatorische Zinsen (Durchschnittsmethode mit/ohne Restwert)?
?
$$\text{Kalk. Zinsen} = \frac{\text{Anschaffungswert} + \text{Restwert}}{2} \cdot \text{Zinssatz}$$ bzw.
$$\text{Kalk. Zinsen} = \frac{\text{Anschaffungswert}}{2} \cdot \text{Zinssatz}$$

Sind kalkulatorische Kosten in der Regel Einzel- oder Gemeinkosten? :: Meistens **Fixe Gemeinkosten**.
<!--SR:!2025-12-17,1,230-->

Wie unterstützt die Kostenartenrechnung die statische Investitionsrechnung? :: Sie liefert die Daten (Kosten und Erlöse) für den **Kostenvergleich** und den Gewinnvergleich.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Kostenartenrechnung]]
SORT file.mtime DESC
```