#Note

2025-12-15

Tags: [[Kosten- und Leistungsrechnung]], [[Deckungsbeitragsrechnung]], [[Break-Even-Analyse]], [[Entscheidungsrechnung]]
#finance

---
Die **Deckungsbeitragsrechnung** (Teilkostenrechnung) ist das zentrale Instrument für kurzfristige unternehmerische Entscheidungen. Im Gegensatz zur Vollkostenrechnung verrechnet sie **keine Fixkosten** auf die Produkteinheit.

#### 1. Grundbegriffe & Formeln

Der Deckungsbeitrag (DB)
Der Betrag, der zur Deckung der Fixkosten zur Verfügung steht.

- Stück-Deckungsbeitrag ($db$):
    $$db = p - k_v$$
    
- Gesamt-Deckungsbeitrag ($DB$):
    $$DB = (p - k_v) \cdot x \quad \text{oder} \quad DB = U - K_v$$
    
- Betriebsergebnis (BE):
    $$BE = DB - K_{fix}$$

---
#### 2. Break-Even-Analyse (Gewinnschwelle)

Der Punkt, an dem Erlöse und Kosten gleich hoch sind (Gewinn = 0).
Hier gilt: Der Deckungsbeitrag deckt exakt die Fixkosten.

Formel (Break-Even-Menge):
$$x_{BE} = \frac{K_{fix}}{p - k_v} = \frac{K_{fix}}{db}$$

Formel (Break-Even-Umsatz):
$$U_{BE} = x_{BE} \cdot p$$

**Beispiel "Kindy" (Schlumpf-Häuser):**
- Fixkosten ($K_f$) = 30.000 €
- Preis ($p$) = 40 €
- Variable Kosten ($k_v$) = 30 €
- $db = 40 - 30 = 10 €$

$$x_{BE} = \frac{30.000}{10} = 3.000 \text{ Stück}$$

Interpretation: Ab dem 3.001. Haus macht das Unternehmen Gewinn.

**Die 5 Gewinnsituationen:**

|**Situation**|**Bedingung**|**Ergebnis**|
|---|---|---|
|**1. Negativer DB**|$p < k_v$|**Fataler Verlust.** Produktion sofort stoppen (jeder Verkauf vernichtet Geld).|
|**2. DB ist Null**|$p = k_v$|**Verlust** in Höhe der Fixkosten.|
|**3. Unterdeckung**|$0 < DB < K_f$|**Verlust** (Verlustzone), aber jeder Verkauf mindert den Verlust.|
|**4. Break-Even**|$DB = K_f$|**Gewinn = 0**.|
|**5. Gewinnzone**|$DB > K_f$|**Gewinn**.|

---

#### 3. Steuerung von Rabatten (Sensitivitätsanalyse)

Wenn ich Rabatte gebe, sinkt mein $db$. Um den _gleichen absoluten Gewinn_ zu halten, muss die Menge ($x$) massiv steigen ("Mengenhebel").
_Faustregel:_ Je geringer der ursprüngliche Deckungsbeitrag, desto gefährlicher sind Rabatte.

Beispiel:
Bei einer Marge von 20% führt ein Rabatt von 10% dazu, dass sich der notwendige Absatz fast verdoppeln muss (+90%), um den Gewinnverlust auszugleichen.

---

#### 4. Entscheidungsfehler der Vollkostenrechnung

Szenario "Sortimentsbereinigung" (Flauschy):
Ein Produkt (A) erwirtschaftet einen Verlust, wenn man ihm volle Fixkosten zurechnet.
- **Entscheidung Vollkosten:** "Produkt A streichen, da Verlustbringer." $\rightarrow$ **FALSCH!**
- **Der Fehler:** Die Fixkosten (z.B. Miete, Abschreibung) entfallen nicht, wenn Produkt A wegfällt ("Fixkostenremangenz"). Sie verteilen sich nur auf die verbleibenden Produkte B und C, die dadurch plötzlich auch schlechter aussehen.
- **Entscheidung Teilkosten:** Solange der **DB > 0** ist, trägt das Produkt zur Deckung der Fixkosten bei. Streicht man es, fehlt dieser Deckungsbeitrag, und der Gesamtverlust des Unternehmens _steigt_.
    

---

#### 5. Optimales Produktionsprogramm (Engpass-Theorie)

Welche Produkte soll ich produzieren, wenn meine Kapazität begrenzt ist?
**Das Entscheidungs-Schema:**
1. Kein Engpass:
    Produziere alles, was einen positiven Deckungsbeitrag ($db > 0$) hat, bis zur Absatzobergrenze.
2. Ein Engpass (z.B. Maschinenstunden):
    Entscheidung nach dem Relativen Deckungsbeitrag.
    $$db_{rel} = \frac{\text{Stück-Deckungsbeitrag}}{\text{Engpassbeanspruchung pro Stück}}$$
    
    Logik: Welches Produkt holt pro Minute Maschinenzeit am meisten Geld herein?
1. Zwei Engpässe:
    Grafische Lösung (Lineare Optimierung).
    
2. Mehr als zwei Engpässe:
    Simplex-Algorithmus (Operations Research).
    

---

#### 6. Make-or-Buy Entscheidung

Soll ich selbst produzieren oder zukaufen (Outsourcing)?
Der "Mercedes-Fehler":

Oft wird argumentiert: "Fremdbezug kostet 60 €, Eigenfertigung (Vollkosten) kostet 100 €. Also kaufen wir zu!"
- **Problem:** In den 100 € stecken Fixkosten (Halle, "Mercedes des Chefs"), die auch beim Fremdbezug weiterbezahlt werden müssen.
- Korrekte Entscheidung (bei Unterbeschäftigung):
    Vergleiche Variable Kosten ($k_v$) der Eigenfertigung mit dem Zukaufspreis.
    - Wenn $k_v (50 €) < \text{Zukaufspreis} (60 €) \rightarrow$ **Make** (Selbst herstellen).
    - Die Fixkosten sind entscheidungsirrelevant ("Sunk Costs").

---

#### 7. Übersicht: Wann welches System?

|**Entscheidung**|**Vollkostenrechnung**|**Teilkostenrechnung (DB)**|
|---|---|---|
|**Langfristige Preisuntergrenze**|**Ja** (Alle Kosten decken)|Nein|
|**Kurzfristige Preisuntergrenze**|Nein|**Ja** (Nur var. Kosten decken)|
|**Sortimentsentscheidung**|Nein (Gefahr der Fehlsteuerung)|**Ja** (Positiver DB?)|
|**Engpass-Optimierung**|Nein|**Ja** (Relativer DB)|
|**Make-or-Buy**|Nein|**Ja** (Vergleich mit $k_v$)|
|**Unikate / Großprojekte**|**Ja** (Kalkulation)|Bedingt|

---
#### Flashcards (Deckungsbeitragsrechnung)
Wie lautet die Formel für den Stück-Deckungsbeitrag?
?
$$db = p - k_v$$
$$DB = (p - k_v) \cdot x \quad \text{oder} \quad DB = U - K_v$$
(Preis - variable Stückkosten)
<!--SR:!2025-12-17,1,230-->

Wie lautet die Formel für die Break-Even-Menge?
?
$$x_{BE} = \frac{K_{fix}}{p - k_v} = \frac{K_{fix}}{db}$$
<!--SR:!2025-12-17,1,230-->

Wann liegt die "Kurzfristige Preisuntergrenze" vor? :: Wenn der Preis genau die variablen Kosten deckt ($p = k_v$ bzw. $db = 0$).
<!--SR:!2025-12-17,1,230-->

Wie errechnet man das Betriebsergebnis BE? :: $BE = DB - K_{fix}$

Warum führt die Vollkostenrechnung bei der Sortimentsbereinigung oft zu falschen Entscheidungen? :: Weil sie **Fixkosten proportionalisiert**. Fällt ein Produkt weg, bleiben die Fixkosten bestehen und belasten die restlichen Produkte stärker (Fixkostenremangenz).

Was ist die Entscheidungsregel beim "Optimalen Produktionsprogramm" mit **einem** Engpass? :: Wähle die Produkte mit dem höchsten **relativen Deckungsbeitrag** ($db$ pro Engpasseinheit).

Wie entscheidet man kurzfristig bei "Make-or-Buy" (bei freien Kapazitäten)? :: Man vergleicht die **variablen Kosten** der Eigenfertigung mit dem Fremdbezugspreis (Fixkosten sind irrelevant).

Was passiert mit dem Break-Even-Punkt, wenn die Fixkosten steigen? :: Der Break-Even-Punkt steigt (man muss mehr verkaufen, um die Kosten zu decken).
<!--SR:!2025-12-17,1,230-->

Was passiert mit dem Break-Even-Punkt, wenn der Preis ($p$) steigt? :: Der Break-Even-Punkt sinkt (man erreicht die Gewinnschwelle früher).


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Deckungsbeitragsrechnung]]
SORT file.mtime DESC
```