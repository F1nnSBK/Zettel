#Note

2026-05-15

Tags: [[Statistik]], [[Visualisierung]], [[Deskriptive Statistik]], [[Normalverteilung]]
#deskriptive_statistik 

---
Der **Quantil-Quantil-Plot (QQ-Plot)** ist ein exploratives grafisches Werkzeug, um zu prüfen, ob eine empirische Stichprobe einer bestimmten theoretischen Verteilung (meist der Normalverteilung) folgt oder ob zwei empirische Stichproben aus der gleichen Verteilung stammen.

### Funktionsweise

Auf der x-Achse werden die theoretischen Quantile der Referenzverteilung (z. B. $z_p$ der Standardnormalverteilung) abgetragen, auf der y-Achse die empirischen Quantile der sortierten Daten $x_{(i)}$.

- Jeder Punkt repräsentiert ein Paar aus (theoretischem Quantil, beobachtetem Quantil).
- Bei Identität der Verteilungsform liegen alle Punkte auf der Winkelhalbierenden $y = x$ (bzw. auf einer Geraden, falls sich nur Lage- und Skalenparameter unterscheiden).

### Interpretation von Abweichungen

Das Muster der Punkte verrät die Art der Abweichung von der Referenzverteilung:

- **Gerade:** Die Daten sind (annähernd) normalverteilt.
- **S-Form:** Die Verteilung hat „schwerere“ oder „leichtere“ Enden (Kurtosis) als die Referenz.
- **Bananen-Form (gekrümmt):** Die Verteilung ist schief (Skewness) im Vergleich zur Referenz.
- **Ausreißer:** Einzelne Punkte, die weit abseits der Geraden an den Rändern liegen.

### Mathematischer Hintergrund

Für eine Normalverteilung $N(\mu, \sigma^2)$ gilt die lineare Beziehung:

$$x_p = \mu + \sigma \cdot z_p$$

Dabei ist $x_p$ das Quantil der Daten und $z_p$ das Quantil der Standardnormalverteilung. Im Plot entspricht $\mu$ dem Achsenabschnitt und $\sigma$ der Steigung der Geraden.

---

### Flashcards

Was ist das primäre Ziel eines QQ-Plots in der deskriptiven Statistik?::Die visuelle Überprüfung, ob eine empirische Datenmenge einer theoretischen Referenzverteilung (meist der Normalverteilung) folgt.

Wie lässt sich die Standardabweichung $\sigma$ einer Stichprobe im QQ-Plot ablesen, wenn gegen die Standardnormalverteilung geplottet wird?::Die Standardabweichung entspricht der Steigung der Geraden, auf der die Quantil-Punkte liegen.

Warum liegen die Punkte in einem QQ-Plot bei normalverteilten Daten auf einer Geraden, auch wenn die Daten nicht standardnormalverteilt ($\mu \neq 0, \sigma \neq 1$) sind?
?
Weil Quantile verschiedener Normalverteilungen über eine lineare Transformation $x_p = \mu + \sigma \cdot z_p$ miteinander verknüpft sind. Die Linearität bleibt also erhalten, lediglich Steigung und Lage der Geraden ändern sich.

Was deutet eine nach oben gebogene Kurve (Bananenform) im QQ-Plot beim Vergleich gegen eine Normalverteilung an?
?
Es deutet auf eine rechtsschiefe Verteilung hin, bei der die hohen empirischen Quantile deutlich größer sind als die theoretisch erwarteten Quantile der Normalverteilung.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[QQ-Plot]]
SORT file.mtime DESC
```