#Note

2026-05-03

Tags: [[Mathematik]], [[Machine Learning]], [[Unsupervised learning]], [[Statistik]], [[Distanzmetriken]]
#UL

---
Wenn Features unterschiedliche Skalen besitzen, dominiert das Feature mit dem größten Wertebereich die Distanzberechnung. Datenvorverarbeitung transformiert den Raum auf eine vergleichbare Basis.

**[[Z-Score]] Normalisierung (Standardisierung):** Zentriert Daten auf den Ursprung ($\mu=0$) und skaliert auf eine Standardabweichung von 1. Sensibel gegenüber Ausreißern.

$$z_i = \frac{x_i - \mu_i}{\sigma_i}$$
**Min-Max Scaling:** Zwingt Werte in ein fixes Intervall (meist $[0, 1]$). Extrem anfällig für Ausreißer, da ein einzelner extremer Wert die gesamte Skala staucht.

$$x'_i = \frac{x_i - min_i}{max_i - min_i}$$



---
#### Flashcards

Welche Auswirkungen hat ein fehlendes Min-Max-Scaling oder eine fehlende Z-Score-Normalisierung auf die euklidische Distanzberechnung in einem Datensatz mit Features unterschiedlicher Größenordnungen?
?
Das Feature mit dem größten Wertebereich (Magnitude) wird die Distanzberechnung vollständig dominieren, wodurch Variationen in kleiner skalierten Features de facto ignoriert werden.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Feature-Transformation]]
SORT file.mtime DESC
```