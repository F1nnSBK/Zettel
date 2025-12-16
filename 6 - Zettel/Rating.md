#Note

2025-12-11

Tags: [[Grundlagen Finanzierung & Investition]], [[Risikomanagement]], [[Fremdkapital]], [[Rating]]
#finance

---
Das **Rating** ist eine ordinalskalierte Bewertung der Bonität eines Unternehmens. Es drückt die Wahrscheinlichkeit aus, dass ein Schuldner seinen Zahlungsverpflichtungen (Zins und Tilgung) nicht nachkommen kann (**Ausfallwahrscheinlichkeit** / Probability of Default - PD).

#### 1. Arten des Ratings

A) Internes Rating (Banken)
Banken sind durch [[Basel II]] / Basel III verpflichtet, eigene Ratingsysteme zu nutzen, um das Risiko ihrer Kreditportfolios zu steuern.
- **Ziel:** Bestimmung der Eigenkapitalunterlegung der Bank. Je schlechter das Rating der Kunden, desto mehr Eigenkapital muss die Bank vorhalten.
    

B) Externes Rating (Ratingagenturen)
Professionelle Einschätzung durch unabhängige Agenturen. Dies ist Voraussetzung für den Zugang zum internationalen Kapitalmarkt (z.B. für die Emission von Anleihen).
- **Die "Big Three":** S&P (Standard & Poor’s), Moody’s, Fitch.
#### 2. Rating-Skalen & Kategorien

Die wichtigste Unterscheidung am Kapitalmarkt ist die Grenze zwischen "sicher" und "spekulativ".

| **Kategorie**                                                 | **S&P / Fitch**      | **Moody's**          | **Bedeutung**                                                                                                              |
| ------------------------------------------------------------- | -------------------- | -------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| **Investment Grade**                                          | **AAA** bis **BBB-** | **Aaa** bis **Baa3** | **Anlagewürdig.** Geringes Ausfallrisiko. Voraussetzung für viele konservative Investoren (Versicherungen, Pensionsfonds). |
| **Non-Investment Grade**<br><br>  <br><br>(Speculative Grade) | **BB+** bis **D**    | **Ba1** bis **C**    | **Spekulativ ("Junk Bonds").** Höheres Ausfallrisiko, dafür höhere Rendite (High Yield).                                   |
| **Default**                                                   | **D**                | **C**                | **Zahlungsausfall.** Unternehmen ist insolvent.                                                                            |

![[rating.jpeg]]
#### 3. Einflussfaktoren auf das Rating

Das Rating-Urteil setzt sich aus zwei Komponenten zusammen:
1. Quantitative Faktoren (Hard Facts):
    Finanzkennzahlen aus dem Jahresabschluss.
    - _Beispiele:_ Eigenkapitalquote, [[Kapitaldienstfähigkeit]], Verschuldungsgrad, EBITDA-Marge, Zinsdeckungsgrad.
2. Qualitative Faktoren (Soft Facts):
    Subjektive Einschätzung der Zukunftsfähigkeit.
    - _Beispiele:_ Qualität des Managements, Marktposition, Branchenrisiko, Nachfolgeregelung, Strategie.
#### 4. Auswirkung des Ratings

Das Rating bestimmt direkt die **Finanzierungskosten** (Cost of Debt).
$$\text{Zinssatz} = \text{Basiszinssatz (Risk Free)} + \text{Credit Spread (Risikoprämie)}$$

- **Investment Grade:** Niedriger Spread (z.B. 0,5% - 2,0%).
- **Non-Investment Grade:** Hoher Spread (z.B. 3,0% - 10,0%), um Investoren für das Risiko zu entschädigen.
    

---
#### Flashcards

Was ist der primäre Zweck eines Ratings? :: Die Einschätzung der **Ausfallwahrscheinlichkeit** (Bonität) eines Schuldners.
<!--SR:!2025-12-17,1,228-->

Welche drei großen Ratingagenturen dominieren den Markt? :: Standard & Poor's (S&P), Moody's, Fitch.

Was versteht man unter "Investment Grade"? :: Ratingklassen (ab BBB- aufwärts), die eine hohe Sicherheit signalisieren und für institutionelle Anleger (Versicherungen) geeignet sind.

Wie werden Anleihen im "Non-Investment Grade" Bereich auch genannt? :: **High Yield Bonds** (Hochzinsanleihen) oder umgangssprachlich **Junk Bonds** (Ramschanleihen).
<!--SR:!2025-12-17,1,228-->

Welche Auswirkung hat eine Verschlechterung des Ratings (Downgrade) auf die Kapitalkosten? :: Die Kapitalkosten steigen, da der **Credit Spread** (Risikoprämie) steigt und oft auch der Aktienkurs fällt.
<!--SR:!2025-12-17,1,230-->

In welche zwei Kategorien werden die Rating-Faktoren unterteilt? :: **Quantitative Faktoren** (Bilanzkennzahlen) und **Qualitative Faktoren** (Management, Markt, Strategie).

Ab welchem Rating (S&P) beginnt der "Non-Investment Grade" Bereich (Ramsch-Status)? :: Ab **BB+** (alles unterhalb von BBB-).



---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Rating]]
SORT file.mtime DESC
```