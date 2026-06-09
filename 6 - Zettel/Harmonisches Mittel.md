#Note

2026-05-15

Tags:[[Statistik]], [[Deskriptive Statistik]], [[Lagemasse]], [[Harmonisches Mittel]]
#deskriptive_statistik

---
Das **harmonische Mittel** $\bar{x}_H$ wird verwendet, um den Durchschnitt von Verhältniszahlen (Raten) zu berechnen, wenn die Gewichtung über die Einheiten im Zähler erfolgt (z. B. „pro km“, „pro Euro“).

### Die Intuition: Konstante Wegstrecke

Stellen wir uns vor, eine Strecke wird in zwei gleich langen Abschnitten mit unterschiedlichen Geschwindigkeiten $v_1$ und $v_2$ durchfahren. Da man für den langsameren Abschnitt **mehr Zeit** benötigt, geht dieser Wert mit einem höheren Zeitgewicht in die Durchschnittsgeschwindigkeit ein. Das harmonische Mittel kompensiert diesen Effekt automatisch.

### Definition

Für $n$ positive Messwerte $x_i > 0$:

$$\bar{x}_H = \frac{n}{\sum_{i=1}^n \frac{1}{x_i}} = \frac{n}{\frac{1}{x_1} + \frac{1}{x_2} + \dots + \frac{1}{x_n}}$$

### Anwendungsszenarien

- **Durchschnittsgeschwindigkeit:** Bei konstanten Teilstrecken (z. B. Hin- und Rückweg).
- **Preise:** Durchschnittlicher Aktienkurs, wenn man für einen fixen Euro-Betrag kauft (Cost-Average-Effekt).
- **Leistung:** Wenn mehrere Maschinen mit unterschiedlicher Kapazität die gleiche Menge an Arbeit verrichten.

### Mathematische Hierarchie (Pythagoreische Mittel)

Für positive Zahlen gilt stets die Ordnung:

$$\bar{x}_H \le \bar{x}_G \le \bar{x}_A$$

Das harmonische Mittel liefert also den kleinsten Wert der drei klassischen Mittelwerte.

---

### Flashcards

Wann muss das harmonische Mittel anstelle des arithmetischen Mittels verwendet werden?::Wenn der Durchschnitt von Verhältnisgrößen (Raten) berechnet werden soll, deren Bezugsgröße (Zähler, z. B. Strecke oder Budget) über alle Beobachtungen hinweg konstant bleibt.
<!--SR:!2026-06-09,1,230-->

Was ist der fundamentale Unterschied zwischen dem Harmonischen Mittel und dem Geometrischen Mittel in der Anwendung?
?
Das **Geometrische Mittel** wird für multiplikative Prozesse (Wachstumsraten, Zinsen) genutzt, um den durchschnittlichen Skalierungsfaktor zu finden. Das **Harmonische Mittel** wird für Raten (z. B. km/h) genutzt, wenn die im Zähler stehende Einheit (km) fix ist, sich aber die benötigte Zeit (Nenner) ändert.
<!--SR:!2026-06-09,1,230-->

Warum ist die Durchschnittsgeschwindigkeit bei zwei gleichen Wegstrecken $s$ mit $v_1=60$ und $v_2=120$ nicht 90 km/h?
?
Da man für die langsame Strecke doppelt so viel Zeit benötigt wie für die schnelle, ist das Zeitgewicht von $v_1$ höher. Das harmonische Mittel berücksichtigt dies:

$$\bar{v}_H = \frac{2}{\frac{1}{60} + \frac{1}{120}} = \frac{2}{\frac{3}{120}} = 80 \text{ km/h}$$


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Harmonisches Mittel]]
SORT file.mtime DESC
```