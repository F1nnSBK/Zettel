#Note

2025-12-17

Tags: [[]], [[]], [[]]
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

1. **Identifizieren:** Welche Bedingungen ($B$) und Aktionen ($A$) gibt es im Text/Szenario?.
    
2. **Spezifizieren (Matrix):** Festlegen der Tabellengröße.
    
    - Formel für die Anzahl der theoretischen Regeln: $R = 2^B$ (bei binären Bedingungen Ja/Nein).
        
3. **Festlegen der Regeln:** Eintragen der Kombinationen (Y/N) und Zuordnen der Aktionen (X).
    
    - _Tipp:_ Prüfen auf Unmöglichkeit (Widersprüche) $\rightarrow$ solche Spalten können gestrichen werden.
        
4. **Konsolidieren:** Vereinfachen der Tabelle (siehe nächste Notiz).

### 4. Interpretation: Regeln ableiten (Klausur-Fokus)

Hier übersetzen wir die Spalten ("Spalte 1", "Spalte 2") zurück in natürliche Sprache (Sätze).

- Formel für einen Satz:
    
    $$WENN \quad (Bedingung\_1 = Wert) \quad UND \quad (Bedingung\_2 = Wert) \quad ... \quad DANN \quad (Aktion\_X)$$
    
- **Beispiel aus Drucker-Szenario:**
    
    - _Spalte R1:_ $B1=N$ (Drucker nicht bereit), $B2, B3$ egal. Aktion: "Kabel prüfen".
        
    - _Satz:_ "Wenn der Drucker **nicht** bereit ist, **dann** prüfen Sie das Druckerkabel (Verbindung)".
        
- **Wichtig:** Achte darauf, ob Bedingungen mit **UND** verknüpft sind (innerhalb einer Spalte sind sie das immer!).

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Entscheidungstabelle]]
SORT file.mtime DESC
```