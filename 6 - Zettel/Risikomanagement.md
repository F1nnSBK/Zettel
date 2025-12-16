#Note

2025-12-15

Tags: [[Projektmanagement]], [[Risikomanagement]], [[Risikomatrix]], [[Controlling]]
#pm

---
**Risikomanagement** zielt darauf ab, die Wahrscheinlichkeit und/oder die Auswirkungen negativer Ereignisse zu minimieren und Chancen zu nutzen.

#### 1. Definition Risiko

Ein Risiko ist ein Ereignis, das in der Zukunft mit einer **Wahrscheinlichkeit < 100%** eintritt und eine **negative Auswirkung** auf die Projektziele (Zeit, Kosten, Qualität) hat.
- _Abgrenzung:_ Wenn die Wahrscheinlichkeit 100% ist, ist es kein Risiko, sondern ein **Problem** (Tatsache).
    

#### 2. Der Risikomanagement-Prozess (Lebenszyklus)

Ein iterativer Kreislauf, der das gesamte Projekt begleitet:
1. **Planen:** Wie gehen wir mit Risiken um? (Budget, Rollen).
2. **Identifizieren:** Brainstorming, Checklisten, SWOT. Erstellung des **Risikoregisters**.
3. **Analysieren (Qualitativ):** Bewertung nach Eintrittswahrscheinlichkeit und Tragweite $\rightarrow$ **Risikomatrix**.
4. Analysieren (Quantitativ): Rechnerische Bewertung (z.B. in Euro).
$$\text{Risikowert} = \text{Eintrittswahrscheinlichkeit} \times \text{Schadenshöhe}$$

5. **Maßnahmen planen:** Strategien festlegen (siehe unten).
6. **Überwachen:** Regelmäßige Reviews (Sind neue Risiken aufgetaucht? Greifen die Maßnahmen?).
    

#### 3. Die Risikomatrix (Qualitative Analyse)

Visualisierung der Risiken zur Priorisierungg
- **X-Achse:** Eintrittswahrscheinlichkeit (Gering bis Hoch).
- **Y-Achse:** Auswirkung / Schadenshöhe (Gering bis Katastrophal).
- **Roter Bereich:** Sofortiger Handlungsbedarf (Top-Risiken).
    

#### 4. Die 4 Strategien der Risikobewältigung

Wie gehen wir mit einem identifizierten Risiko um?

|**Strategie**|**Beschreibung**|**Beispiel**|
|---|---|---|
|**1. Vermeiden**<br><br>  <br><br>(Avoid)|Die Ursache eliminieren oder den Projektplan ändern, um das Risiko komplett auszuschließen.|Anderen Lieferanten wählen, gefährliches Feature streichen.|
|**2. Vermindern**<br><br>  <br><br>(Mitigate)|Die **Eintrittswahrscheinlichkeit** oder die **Auswirkung** reduzieren.|Prototyp bauen (vermindert technisches Risiko), Redundante Systeme (vermindert Ausfallfolgen).|
|**3. Übertragen**<br><br>  <br><br>(Transfer)|Das Risiko an Dritte abgeben (oft gegen Geld).|**Versicherung** abschließen, Outsourcing an Experten (mit Festpreis).|
|**4. Akzeptieren**<br><br>  <br><br>(Accept)|Bewusstes Eingehen des Risikos (weil Eintritt unwahrscheinlich oder Kosten der Maßnahme > Schaden).|Bildung von **Risikopuffern** (Budget/Zeit) für den Fall der Fälle ("Selbstbehalt").|

#### 5. Das Risikoregister (Risk Log)

Das zentrale Dokument. Es enthält: ID, Beschreibung, Wahrscheinlichkeit, Auswirkung, Risikowert, Verantwortlichen und geplante Maßnahmen.

---

#### Flashcards

Was ist der Unterschied zwischen einem Risiko und einem Problem? :: Ein Risiko ist **unsicher** (Wahrscheinlichkeit < 100%), ein Problem ist eine bereits eingetretene Tatsache (100%).
<!--SR:!2025-12-17,1,230-->

Wie lautet die Formel zur Berechnung des Risikowertes (monetär)? :: Eintrittswahrscheinlichkeit $\times$ Schadenshöhe (Kosten).
<!--SR:!2025-12-16,1,230-->

Welche Strategie wählt man, wenn man eine Versicherung abschließt? :: **Übertragen** (Transfer).
<!--SR:!2025-12-16,1,230-->

Welche Strategie wählt man, wenn man den Projektplan ändert, um eine Gefahr komplett zu umgehen? :: **Vermeiden** (Avoid).
<!--SR:!2025-12-17,1,230-->

Welche Strategie wählt man, wenn die Kosten der Gegenmaßnahme höher wären als der mögliche Schaden? :: **Akzeptieren** (Accept).
<!--SR:!2025-12-16,1,230-->

Was sind die beiden Dimensionen der Risikomatrix? :: Eintrittswahrscheinlichkeit und Auswirkung (Schadenshöhe).
<!--SR:!2025-12-17,1,230-->



---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Risikomanagement]]
SORT file.mtime DESC
```