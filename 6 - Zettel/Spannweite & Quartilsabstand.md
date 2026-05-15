#Note

2026-05-15

Tags: [[Statistik]], [[Deskriptive Statistik]], [[Streuungsmasse]], [[Boxplot]]
#deskriptive_statistik 

---
Während Lagemaße das Zentrum einer Verteilung beschreiben, messen die **Spannweite** und der **Quartilsabstand**, wie weit die Beobachtungen auseinanderliegen.

### Spannweite (Range)

Die Spannweite $R$ ist die Differenz zwischen dem größten und dem kleinsten Wert der Urliste.

$$R = x_{(n)} - x_{(1)} = x_{max} - x_{min}$$

- **Einsatzzweck:** Schneller Überblick über die totale Ausdehnung.
- **Nachteil:** Extrem empfindlich gegenüber Ausreißern. Ein einziger Messfehler am Rand verzerrt das gesamte Maß.

### Quartilsabstand (Interquartile Range - IQR)

Der IQR misst die Differenz zwischen dem dritten und dem ersten Quartil. Er beschreibt die Länge des Intervalls, in dem die zentralen 50% der Daten liegen.

$$IQR = Q_{0,75} - Q_{0,25} = Q_3 - Q_1$$

- **Einsatzzweck:** Kernkomponente des Boxplots; Identifikation von Ausreißern.
- **Vorteil:** **Robustes Maß**. Da die äußeren 25% an beiden Enden ignoriert werden, haben Ausreißer keinen Einfluss auf den IQR.

### Mittlere absolute Abweichung (MAD) - Exkurs

Häufig als Alternative zur Varianz genutzt, wenn Quadrierung (und damit die Übergewichtung von Ausreißern) vermieden werden soll. Sie misst den Durchschnitt der absoluten Distanzen zum Median oder Mittelwert.

---

### Flashcards

Warum wird der Quartilsabstand (IQR) in der explorativen Datenanalyse oft der Spannweite vorgezogen?::Da der IQR robust gegenüber Ausreißern ist; er konzentriert sich auf die zentralen 50% der Daten und wird nicht durch extreme Einzelwerte an den Rändern der Verteilung verzerrt.

Wie verändern sich Spannweite und IQR, wenn jeder Wert eines Datensatzes um den Faktor $c=2$ multipliziert wird?::Beide Maße verdoppeln sich ebenfalls ($R_{neu} = 2 \cdot R_{alt}$), da sie Distanzen auf der Merkmalsachse darstellen, die linear mit der Skalierung wachsen.

Was sagt ein im Verhältnis zur Spannweite sehr kleiner IQR über die Form der Verteilung aus?
?
Es deutet auf eine sehr hohe Datendichte im Zentrum hin (steile Verteilung/Leptokurtosis). Die Masse der Daten ist eng konzentriert, während die Ränder (Tails) weit auslaufen oder vereinzelte Ausreißer enthalten.

In welcher Beziehung stehen die Whiskers eines Standard-Boxplots zum IQR?
?
Die Whiskers sind auf maximal das 1,5-fache des IQR begrenzt ($1,5 \cdot IQR$). Datenpunkte außerhalb dieser Zone werden explizit als Ausreißer markiert, da sie signifikant weit vom "Zentrum der Masse" entfernt liegen.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Spannweite & Quartilsabstand]]
SORT file.mtime DESC
```