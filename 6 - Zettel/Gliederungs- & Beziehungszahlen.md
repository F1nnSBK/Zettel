#Note

2026-05-15

Tags: [[Statistik]], [[Verhältniszahlen]], [[Wirtschaftsstatistik]], [[Deskriptive Statistik]]
#deskriptive_statistik

---
Verhältniszahlen dienen dazu, absolute Zahlen vergleichbar zu machen. Man unterscheidet primär zwischen Gliederungszahlen, Beziehungszahlen und Messzahlen (Indizes).

### 1. Gliederungszahlen (Quoten)

Gliederungszahlen setzen eine Teilmenge in Beziehung zur Gesamtmenge. Sie beschreiben die innere Struktur einer Masse.

- **Logik:** $\frac{\text{Teilmasse}}{\text{Gesamtmasse}}$
- **Beispiele:** Arbeitslosenquote, Frauenanteil im Management, relative Häufigkeiten $r_i$.
- **Eigenschaft:** Werte liegen zwischen 0 und 1 (bzw. 0% - 100%). Die Summe aller Gliederungszahlen einer Masse ist immer 1.

### 2. Beziehungszahlen

Beziehungszahlen setzen zwei verschiedene Massen in Relation, die in einem sachlichen Zusammenhang stehen, aber keine Teil-Ganzes-Beziehung aufweisen.

- **Logik:** $\frac{\text{Merkmal A}}{\text{Merkmal B}}$
    
- **Beispiele:** Bevölkerungsdichte (Einwohner pro $km^2$)
    - Fuhrpark-Effizienz (Liter pro 100 km)
    - Kaufkraft pro Haushalt.

- **Eigenschaft:** Die Einheiten von Zähler und Nenner bleiben oft erhalten (z. B. Einwohner/$km^2$).

### 3. Messzahlen (Indexwerte)

Messzahlen vergleichen die Ausprägung eines Merkmals mit einem fixen Basiswert (meist zeitlich oder räumlich).

- **Logik:** $\frac{\text{Wert in Periode } t}{\text{Wert in Basisperiode } 0}$
- **Einsatz:** Visualisierung von zeitlichen Entwicklungen ohne absolute Volumina.

---

### Flashcards

Was ist der fundamentale Unterschied zwischen einer Gliederungszahl und einer Beziehungszahl?::Bei der Gliederungszahl ist der Zähler ein Teil des Nenners (Teil/Ganzes), während bei der Beziehungszahl zwei sachlich verschiedene Größen zueinander in Relation gesetzt werden.

Warum ist die relative Häufigkeit $r_i$ eine Gliederungszahl?::Weil sie die Anzahl der Beobachtungen einer Kategorie ($n_i$) ins Verhältnis zur Gesamtzahl aller Beobachtungen ($n$) setzt.
<!--SR:!2026-06-11,3,250-->

Gehört die "Umsatzrendite" (Gewinn / Umsatz) zu den Gliederungs- oder zu den Beziehungszahlen?
?
Es ist eine **Gliederungszahl**, da der Gewinn ein (erhoffter) Teil des Gesamtumsatzes ist. Es wird die innere Struktur des Umsatzes analysiert.

Welche Gefahr besteht bei der Interpretation von Beziehungszahlen wie "Umsatz pro Mitarbeiter" in einem wachsenden Unternehmen?
?
Die Kennzahl kann steigen, obwohl die absolute Effizienz sinkt, wenn die Mitarbeiterzahl (Nenner) schneller abnimmt als der Umsatz (Zähler). Man muss immer beide absoluten Komponenten im Blick behalten, um Fehlinterpretationen zu vermeiden.



---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Gliederungs- & Beziehungszahlen]]
SORT file.mtime DESC
```