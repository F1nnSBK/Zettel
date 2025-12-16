#Note

2025-12-15

Tags: [[Projektmanagement]], [[Vorgehensmodelle]], [[Agile]], [[Wasserfall]]
#pm

---
Vorgehensmodelle (Entwicklungsansätze) strukturieren den Projektlebenszyklus. Die Wahl des Modells hängt von der Stabilität der Anforderungen und der Komplexität ab.

#### 1. Übersicht: Die zwei Welten

|**Merkmal**|**Plangetrieben (Predictive / Klassisch)**|**Adaptiv (Agil / Change-driven)**|
|---|---|---|
|**Fokus**|Planerfüllung|Kundenwert & Flexibilität|
|**Magisches Dreieck**|**Scope ist fest**; Zeit & Kosten werden geschätzt.|**Zeit & Kosten sind fest**; Scope ist variabel (geschätzt).|
|**Änderungen**|Werden vermieden (Change Request nötig).|Werden begrüßt (Competitive Advantage).|
|**Vorgehen**|Sequenziell (Schritt-für-Schritt).|Iterativ & Inkrementell.|
|**Beispiele**|Wasserfall, V-Modell|Scrum, Kanban, XP|

#### 2. Klassische Modelle

**A) Wasserfall-Modell**
- **Prinzip:** Streng lineare Abfolge von Phasen (Analyse $\rightarrow$ Design $\rightarrow$ Umsetzung $\rightarrow$ Test $\rightarrow$ Betrieb).
- **Regel:** Eine Phase muss zu 100% abgeschlossen sein (Meilenstein/Abnahme), bevor die nächste beginnt.
- **Vorteil:** Einfach planbar, hohe Disziplin.
- **Nachteil:** Fehler werden spät entdeckt (Big Bang), unflexibel bei neuen Anforderungen.
    

**B) V-Modell**
- **Prinzip:** Erweiterung des Wasserfalls. Jeder Entwicklungsphase (linker Schenkel) steht eine Testphase (rechter Schenkel) gegenüber.
- **Fokus:** Qualitätssicherung, **Verifikation** (Machen wir das Produkt richtig?) und **Validierung** (Machen wir das richtige Produkt?).
- **Einsatz:** Häufig bei Hardware-Entwicklung oder im öffentlichen Dienst.
    

#### 3. Agile / Adaptive Modelle
**Prinzip:** Arbeit in kurzen Zyklen (Iterationen/Sprints), um schnell Feedback zu erhalten.
- **Iterativ:** Wiederholung von Schritten zur Verfeinerung.
- **Inkrementell:** Lieferung von nutzbaren Teilprodukten in kleinen Stücken.
- **Ziel:** Schnelle Lieferung von Geschäftswert, Umgang mit Unsicherheit ("Cone of Uncertainty" wird schrittweise reduziert).
    

#### 4. Wann welches Modell? (Stacey-Matrix)
- **Einfach/Kompliziert:** Anforderungen & Technologie sind klar $\rightarrow$ **Wasserfall / V-Modell**.
- **Komplex:** Anforderungen unklar oder Technologie neu $\rightarrow$ **Agil (Scrum)**.
- **Chaotisch:** Sofortiges Handeln nötig (Krisenmanagement) $\rightarrow$ Kanban / "Just do it".

---
#### Flashcards

Was ist der fundamentale Unterschied im "Magischen Dreieck" zwischen klassischem und agilem PM? :: **Klassisch:** Scope ist fest, Zeit/Kosten variabel. **Agil:** Zeit/Kosten sind fest (Timebox), Scope ist variabel.
<!--SR:!2025-12-17,1,210-->

Wann ist das Wasserfall-Modell geeignet? :: Wenn Anforderungen stabil, klar definiert und Änderungen unwahrscheinlich sind (z.B. Bauwesen).
<!--SR:!2025-12-17,1,210-->

Was ist das besondere Merkmal des V-Modells? :: Es stellt jeder Entwicklungsphase direkt eine entsprechende **Testphase** gegenüber (Fokus auf Qualitätssicherung).
<!--SR:!2025-12-17,1,210-->

Was bedeutet "Inkrementell" im Kontext von Vorgehensmodellen? :: Das Produkt wird in nutzbaren **Teilstücken** (Inkrementen) geliefert und erweitert, statt alles am Ende auf einmal.
<!--SR:!2025-12-17,1,210-->

Welches Vorgehensmodell eignet sich am besten für Projekte mit unklaren Anforderungen und hoher Komplexität? :: Ein **agiles / adaptives** Modell (z.B. Scrum).
<!--SR:!2025-12-17,1,210-->



---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Vorgehensmodelle]]
SORT file.mtime DESC
```