#Note

2026-01-02

Tags: [[Statistik]], [[Deskriptive Statistik]], [[Visualisierung]], [[Python]]
#deskriptive_statistik

---
Einfache Grafiken dienen der Visualisierung von Häufigkeitsverteilungen (absolut $n_i$ oder relativ $r_i$). Im Gegensatz zum Histogramm (für klassierte Daten) ist hier meist die Höhe (bei Säulen/Stäben) oder der Winkel (bei Kreisen) proportional zur Häufigkeit.
### Kreisdiagramm (Tortendiagramm)
Stellt die Anteile der Ausprägungen am Gesamten dar.

- **Einsatzzweck:** Nominalskalierte Daten mit wenigen Ausprägungen (max. 5-7).
- **Vorteil:** Schnelle Erfassung von Mehrheiten/Proportionalität zum Ganzen.
- **Nachteil:** Vergleiche zwischen ähnlichen Anteilen sind schwer; hoher Platzbedarf für Beschriftungen.
- **Mathematik:** Winkel $\alpha_i = r_i \cdot 360^\circ$.
    

```Python
import matplotlib.pyplot as plt
kategorien = ['A', 'B', 'C', 'D']
anteile = [0.1, 0.4, 0.3, 0.2]

fig, ax = plt.subplots()
ax.pie(anteile, labels=kategorien, autopct='%1.1f%%', startangle=90)
ax.axis('equal')
plt.title("Kreisdiagramm")
plt.show()
```

### Blockdiagramm (Balken-/Säulendiagramm)
Die Häufigkeit wird durch die Länge (Balken) oder Höhe (Säulen) repräsentiert.

- **Einsatzzweck:** Nominal- oder ordinalskalierte Daten; diskrete metrische Daten.
- **Vorteil:** Exakter Vergleich von Werten durch gemeinsame Basislinie; verträgt viele Kategorien.
- **Nachteil:** Kann bei sehr vielen Ausprägungen unübersichtlich werden.
- **Wichtig:** Die Balken berühren sich nicht (Abgrenzung zu stetigen Daten/Histogramm).


```Python
import matplotlib.pyplot as plt
kategorien = ['1', '2', '3', '4', '5']
haeufigkeiten = [2, 3, 4, 5, 6]

plt.bar(kategorien, haeufigkeiten, width=0.6)
plt.xlabel("Merkmalsausprägung")
plt.ylabel("Häufigkeit")
plt.title("Blockdiagramm")
plt.show()
```

### Stabdiagramm
Reduziert die Säulen auf dünne Linien (Nadeln).

- **Einsatzzweck:** Diskrete metrische Merkmale (z. B. Kinderzahl, Fehleranzahl).
- **Bedeutung:** Unterstreicht die Punkthafte Natur der Daten; es gibt keine Werte „zwischen“ den Stäben.
- **Vorteil:** Minimale visuelle Überladung; mathematisch präzise für diskrete Wahrscheinlichkeitsmassen.


```Python
import matplotlib.pyplot as plt
x = ["6", "8-11", "12-15"]
y = [1, 8, 9]

plt.stem(x, y, basefmt=" ")
plt.xlabel("Merkmalsausprägung")
plt.ylabel("Häufigkeit")
plt.title("Stabdiagramm")
plt.show()
```

### Polygonzug (Liniendiagramm)
Verbindet Häufigkeitspunkte durch Geraden.

- **Einsatzzweck:** Ordinale oder metrische Daten; Darstellung von Trends oder zeitlichen Verläufen.    
- **Vorteil:** Verdeutlicht die Gestalt (Shape) der Verteilung (z. B. Symmetrie, Steilheit).
- **Gefahr:** Suggeriert Kontinuität zwischen den Kategorien, die bei diskreten Daten nicht existiert.


```Python
import matplotlib.pyplot as plt
x = ["6", "8-11", "12-15"]
y = [1, 8, 9]

plt.plot(x, y, marker='o', linestyle='-')
plt.xlabel("Merkmalsausprägung")
plt.ylabel("Häufigkeit")
plt.title("Polygonzug")
plt.grid(True)
plt.show()
```

---

### Flashcards

Warum ist das Stabdiagramm für diskrete metrische Merkmale besser geeignet als ein Säulendiagramm? :: Das Stabdiagramm betont durch die fehlende Breite der Stäbe, dass die Häufigkeit nur an exakten Punkten (Isolierte Ereignisse) existiert und keine Masse in den Zwischenbereichen liegt.
Was ist die mathematische Bedingung für die Konstruktion eines Kreisdiagramms? :: Die Summe der relativen Häufigkeiten muss exakt 1 ergeben ($\sum r_i = 1$), da der Vollkreis ($360^\circ$) die Gesamtheit der Grundgesamtheit repräsentiert.
<!--SR:!2026-06-09,1,230-->

Welches Diagramm eignet sich am besten, um die Rangfolge (Ordinalskala) von 15 verschiedenen Kategorien vergleichbar zu machen?
?
Das **Balkendiagramm** (horizontal). Es erlaubt durch die gemeinsame vertikale Achse einen präzisen Längenvergleich der Häufigkeiten und bietet Platz für die Beschriftung vieler Kategorien.

Warum sollte man für nominale Daten keinen Polygonzug verwenden?
?
Weil die Verbindungslinien zwischen den Punkten eine Ordnung und eine kontinuierliche Veränderung suggerieren, die bei nominalen Daten (ohne natürliche Rangfolge) nicht existiert. Die Steigung der Linie wäre rein zufällig von der Sortierung der x-Achse abhängig.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Diagramme für Häufigkeiten]]
SORT file.mtime DESC
```