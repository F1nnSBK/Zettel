
#Note

2025-12-17

Tags: [[Software Engineering]]
#se

---
### 1. Aufbau & Struktur einer Entscheidungstabelle

Das Grundgerüst, um sich nicht zu verirren.

- **Definition:** Tabellarische Beschreibung logischer Zusammenhänge von Bedingungen, Aktionen und Regeln.
- **Die 4 Quadranten:**
    1. **Bedingungsanzeiger (oben links):** Auflistung aller relevanten Bedingungen ("Wenn...").
    2. **Bedingungseinträge (oben rechts):** Die logischen Werte (Ja/Nein bzw. Y/N) für jede Regel.
    3. **Aktionsanzeiger (unten links):** Auflistung aller möglichen Aktionen ("Dann...").
    4. **Aktionseinträge (unten rechts):** Markierung (X), welche Aktion ausgeführt wird.
- **Leserichtung:** Eine **Spalte** repräsentiert genau **eine Regel** (Wenn-Dann-Beziehung).

### 2. Der Erstellungsprozess (4 Schritte)

Der Algorithmus zum Bauen der Tabelle.

1. **Identifizieren:** Welche Bedingungen ($B$) und Aktionen ($A$) gibt es im Text/Szenario?
2. **Spezifizieren (Matrix):** Festlegen der Tabellengröße.
    - Formel für die Anzahl der theoretischen Regeln: $R = 2^B$ (bei binären Bedingungen Ja/Nein).
3. **Festlegen der Regeln:** Eintragen der Kombinationen (Y/N) und Zuordnen der Aktionen (X).
    - *Tipp:* Prüfen auf Unmöglichkeit (Widersprüche) $\rightarrow$ solche Spalten können gestrichen werden.
4. **Konsolidieren:** Vereinfachen der Tabelle (siehe Abschnitt 3).

### 3. Konsolidierung

Das "Eindampfen" der Tabelle – wichtig, um Redundanz zu vermeiden.

- **Ziel:** Übersichtlichkeit erhöhen, ohne die Logik zu verändern.
- **Regel:** Zwei Regeln (Spalten) können zu einer einzigen zusammengefasst werden, wenn sie:
    1. Zu den exakt **gleichen Aktionen** führen UND
    2. Sich in nur **einer einzigen Bedingung** unterscheiden.
- **Ergebnis:** Die irrelevante Bedingung wird als "Don't Care" (z.B. mit einem Strich "–") markiert. Das bedeutet: Für diese Regel ist es egal, ob die Bedingung Ja oder Nein ist, das Ergebnis bleibt gleich.

### 4. Interpretation: Regeln ableiten (Klausur-Fokus)

Hier übersetzen wir die Spalten ("Spalte 1", "Spalte 2") zurück in natürliche Sprache (Sätze).

- **Formel für einen Satz:**
$$WENN \quad (Bedingung\_1 = Wert) \quad UND \quad (Bedingung\_2 = Wert) \quad ... \quad DANN \quad (Aktion\_X)$$

- **Beispiel aus Drucker-Szenario:**
    - *Spalte R1:* $B1=N$ (Drucker nicht bereit), $B2, B3$ egal. Aktion: "Kabel prüfen".
    - *Satz:* "Wenn der Drucker **nicht** bereit ist, **dann** prüfen Sie das Druckerkabel (Verbindung)."

- **Wichtig:** Achte darauf, dass Bedingungen innerhalb einer Regel (Spalte) immer mit **UND** verknüpft sind.

---
#### Flashcards

Wie lautet die Formel für die maximale Anzahl an Regeln bei binären Bedingungen?
?
$2^B$ (wobei B = Anzahl der Bedingungen).
<!--SR:!2025-12-23,1,230-->

Welche vier Quadranten hat eine Entscheidungstabelle?
?
Bedingungsanzeiger, Bedingungseinträge, Aktionsanzeiger, Aktionseinträge.

Wann dürfen zwei Regeln in einer Entscheidungstabelle konsolidiert werden?
?
Wenn sie die gleichen Aktionen auslösen und sich nur in genau einer Bedingung unterscheiden.

Was bedeutet ein "Don't Care" (Strich) in einem Bedingungseintrag?
?
Dass der Wert dieser Bedingung (Ja oder Nein) für diese spezifische Regel keinen Einfluss auf die Aktion hat.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Entscheidungstabelle]]
SORT file.mtime DESC
```