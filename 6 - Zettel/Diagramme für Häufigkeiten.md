#Note

2026-01-02

Tags: [[Statistik]], [[Deskriptive Statistik]], [[Visualisierung]], [[Python]]
#deskriptive_statistik

---

Einfache Grafiken dienen der Visualisierung von Häufigkeitsverteilungen (absolut $n_i$​ oder relativ $r_i$​). Im Gegensatz zum [[Histogramm]] (für klassierte Daten) ist hier meist die **Höhe** (bei Säulen/Stäben) oder der **Winkel** (bei Kreisen) proportional zur Häufigkeit. Sie eignen sich besonders für diskrete oder gruppierte Daten.

---

1. Kreisdiagramm (Tortendiagramm)
Die Daten werden als Kreissektoren dargestellt. Der Winkel αi​ eines Sektors entspricht dem Anteil der relativen Häufigkeit ri​ am Vollkreis.

$α_i​=r_i​⋅360^∘$

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

2. Blockdiagramm (Balken-/Säulendiagramm)
Die Häufigkeit bestimmt die **Höhe** der Blöcke. Die Breite ist meist willkürlich, die Blöcke berühren sich oft nicht, um die Diskretheit der Merkmale zu betonen.

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

3. Stabdiagramm
Ähnlich dem Blockdiagramm, jedoch werden die Häufigkeiten durch dünne Stäbe (Linien) visualisiert. Dies betont den Charakter isolierter Ereignisse bei diskreten Merkmalen.

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

4. Polygonzug (Liniendiagramm)
Verbindet die Endpunkte der Häufigkeiten (z. B. Spitzen der Stäbe) mit Linien, um den Verlauf der Verteilung zu verdeutlichen.

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
#### Flashcards

Wie berechnet man den Winkel αi​ in einem Kreisdiagramm?
?
$α_i​=r_i​⋅360^∘$ (relative Häufigkeit mal 360 Grad).

Was ist der Unterschied in der Darstellung zwischen Block- und Stabdiagramm? :: Beim Blockdiagramm werden Rechtecke (Säulen) verwendet, beim Stabdiagramm dünne Linien; beide repräsentieren die Häufigkeit über die Höhe.

Welche Diagrammform verbindet die Spitzen der Häufigkeiten miteinander? :: Der Polygonzug (Liniendiagramm).

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Diagramme für Häufigkeiten]]
SORT file.mtime DESC
```