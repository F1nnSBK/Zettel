#Note

2026-05-15

Tags: [[Statistik]], [[Zeitreihenanalyse]], [[Komponentenmodell]], [[Business Intelligence]], [[Smoothing]], [[Zeitreihenkomponenten]]
#deskriptive_statistik #bi

---
Das **Komponentenmodell** der Zeitreihenanalyse geht davon aus, dass sich ein beobachteter Wert $y_t$ aus verschiedenen, sich überlagernden Teilkomponenten zusammensetzt.

### Die klassischen Komponenten

Nach Jeske unterscheidet man meist vier Komponenten:

1. **Trendkomponente ($T_t$):** Langfristige, glatte Entwicklung der Zeitreihe (z. B. durch technologischen Fortschritt).
2. **Konjunkturkomponente ($K_t$):** Mittelfristige, wellenförmige Schwingungen (Dauer $> 1$ Jahr). Oft werden $T_t$ und $K_t$ zur **glatten Komponente** zusammengefasst.
3. **Saisonkomponente ($S_t$):** Regelmäßige, sich innerhalb eines Jahres wiederholende Schwankungen (z. B. Quartals- oder Monatseffekte).
4. **Restkomponente ($R_t$):** Unregelmäßige, zufällige Störungen (Rauschen).

### Mathematische Verknüpfungstypen

Je nachdem, wie die Komponenten interagieren, wählt man das passende Modell:

- **Additives Modell:** Die Komponenten sind unabhängig voneinander. Die absolute Höhe der Saisonausschläge bleibt über die Zeit konstant.
$$y_t = T_t + K_t + S_t + R_t$$

- **Multiplikatives Modell:** Die Saison- und Restkomponenten wirken proportional zum Trend. Die Amplitude der Schwingungen wächst oder schrumpft mit dem Niveau der Zeitreihe.
$$y_t = T_t \cdot K_t \cdot S_t \cdot R_t$$

	_Hinweis:_ Ein multiplikatives Modell kann durch Logarithmierung in ein additives Modell überführt werden.

### Vorgehensweise der Zerlegung

1. **Trendbestimmung:** Meist durch gleitende Durchschnitte oder Regressionsrechnung.
2. **Saisonbereinigung:** Ermittlung der Durchschnittsabweichungen der einzelnen Perioden vom Trend (Saisonzahlen).
3. **Restanalyse:** Prüfung, ob die verbleibende Komponente $R_t$ zufällig um den Nullpunkt schwankt.

---

### Flashcards

Was ist der entscheidende visuelle Unterschied zwischen einem additiven und einem multiplikativen Komponentenmodell?::Im additiven Modell bleibt die Amplitude der Saisonschwankungen über die Zeit konstant, während sie im multiplikativen Modell proportional zum Trend zu- oder abnimmt.

Welche Komponenten werden in der deskriptiven Statistik häufig zur "glatten Komponente" zusammengefasst?::Die Trendkomponente ($T_t$) und die Konjunkturkomponente ($K_t$).

Warum ist die Restkomponente $R_t$ für die Qualität eines Modells entscheidend?
?
Die Restkomponente sollte idealerweise "Weißes Rauschen" (White Noise) sein. Enthält sie noch systematische Muster oder Autokorrelationen, wurde die Saisonalität oder der Trend nicht vollständig durch das Modell erfasst.

Wie interpretiert man eine Saisonzahl von $s_i = 1,15$ in einem multiplikativen Modell?
?
Der Wert in der Periode $i$ liegt im Durchschnitt um 15 % über dem langfristigen Trendniveau.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Komponentenmodell]]
SORT file.mtime DESC
```