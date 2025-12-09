#Note

2025-12-08

Tags: [[Dynamische Investitionsrechenverfahren]], [[Grundlagen Finanzierung & Investition]]
#finance

---
Die **Interne Zinsfußmethode** ist ein dynamisches Verfahren, das Investitionsentscheidungen auf Basis der Rendite ([[Interner Zinsfuß]]) trifft.

Im Gegensatz zur Kapitalwertmethode (die den absoluten Gewinn in € misst), beantwortet diese Methode die Frage: **"Zu wie viel Prozent verzinst sich mein gebundenes Kapital?"**.

#### Algorithmus & Entscheidung
1. Berechne den [[Interner Zinsfuß|internen Zinsfuß]] ($i_{IZF}$), bei dem der Kapitalwert $0$ ist.
2. Vergleiche $i_{IZF}$ mit der Hurdle Rate (Kalkulationszins / Finanzierungskosten).

**Regeln:**
- **Absolute Vorteilhaftigkeit:** Investiere, wenn $i_{IZF} > \text{Finanzierungskosten}$.
- **Relative Vorteilhaftigkeit:** Bei Auswahl zwischen Alternativen wähle das Projekt mit dem **höheren** $i_{IZF}$.

#### Kritische Analyse
- **Vorteile:** Liefert eine prozentuale Rendite (Return on Investment), die intuitiv mit Kapitalkosten vergleichbar ist.
- **Nachteile & Risiken:**
    - Bei kleinen Investitionsbeträgen ist die %-Rendite irreführend (50% auf 1€ vs. 10% auf 1 Mio. €).
    - **Wichtig:** Bei Konflikt mit der [[Kapitalwertmethode]] (unterschiedliche Rangfolge) gilt immer: **Kapitalwert schlägt Zinsfuß**, da absoluter Vermögenszuwachs zählt.
    
---
#### Flashcards

Wann ist eine Investition nach der IZF-Methode absolut vorteilhaft? :: Wenn der interne Zinsfuß ($i_{IZF}$) höher ist als der Kalkulationszinssatz (Finanzierungskosten).

Welche Entscheidung triffst du beim Vergleich zweier Projekte nach der IZF-Methode? :: Wähle das Projekt mit dem **höheren** internen Zinsfuß.

Warum ist die IZF-Methode bei sehr kleinen Investitionsbeträgen irreführend? :: Weil eine hohe prozentuale Rendite auf einen winzigen Betrag (z.B. 50% auf 1€) kaum absoluten Vermögenszuwachs bringt.

Was ist die "Goldene Regel" bei einem Konflikt zwischen Kapitalwert und IZF? :: Der **Kapitalwert** hat immer Vorrang, da er den absoluten Nutzen (Wertschaffung) maximiert.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Interne Zinsfußmethode]]
SORT file.mtime DESC
```