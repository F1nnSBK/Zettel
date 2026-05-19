#Note

2026-05-19

Tags: [[Statistik]], [[Lineare Regression]], [[Deskriptive Statistik]], [[Regressionsanalyse]], [[Homoskedastizität]]
#statistik

---
**Heteroskedastizität** bezeichnet den Zustand in der Regressionsanalyse, bei dem die Varianz der Störtermkomponenten (Residuen) nicht konstant ist, sondern sich systematisch mit der Ausprägung der unabhängigen Variablen ändert.

### Mathematische Definition

Im klassischen linearen Regressionsmodell gilt für die Varianz der Fehlerterme $\epsilon_i$:

$$\text{Var}(\epsilon_i \mid x_i) = \sigma_i^2 \neq \text{konstant}$$

### Visuelle Merkmale & Ursachen

Das Phänomen tritt häufig in Querschnittsdaten auf (z. B. bei Unternehmensgrößen oder Haushaltsbefragungen). Visuell äußert sich Heteroskedastizität im Streu- oder Residualdiagramm meist als **Trichterform** (Megafoneffekt).

- **Lernprozesse:** Fehlerbarkeiten sinken mit der Zeit/Erfahrung (Varianz nimmt ab).
- **Wahlfreiheit:** Höheres Einkommen erlaubt eine breitere Streuung im Konsumverhalten (Varianz nimmt zu).
- **Datenagglomeration:** Zusammengefasste Daten aus ungleich großen Stichproben.
    

### Konsequenzen für die Inferenz

1. Die Schätzung der Regressionskoeffizienten $a$ und $b$ bleibt **erwartungstreu** ($\mathbb{E}[\hat{b}] = b$). Es liegt keine systematische Über- oder Unterschätzung der Parameter vor.
2. Der Schätzer ist **nicht mehr effizient**. Es gibt andere Schätzverfahren, die eine kleinere Varianz aufweisen.    
3. Die Standardfehler werden **falsch berechnet** (oft zu klein). Dadurch werden Konfidenzintervalle zu schmal und Hypothesentests ($t$-Test, $F$-Test) tendieren dazu, Effekte als statistisch signifikant zu deklarieren, die es eigentlich nicht sind.
    

### Gegenmaßnahmen

- **Robuste Standardfehler (White-Standardfehler):** Korrigiert die Standardfehler nachträglich, ohne die Koeffizienten selbst zu verändern. Die Tests werden dadurch wieder valide.
- **Varianzstabilisierende Transformationen:** Logarithmierung des Modells: $\log(Y) = a + b \cdot X + \epsilon$
- **Weighted Least Squares (WLS):** Datenpunkte mit einer bekannten hohen Fehlervarianz werden im OLS-Algorithmus geringer gewichtet als Punkte mit präzisen (kleinen) Varianzen.


---
#### Flashcards

Welche fundamentale Eigenschaft verliert der OLS-Schätzer bei Vorliegen von Heteroskedastizität?::Er verliert seine **Effizienz**; er ist nicht mehr der Schätzer mit der geringsten Varianz unter den linearen, erwartungstreuen Schätzern (BLUE-Eigenschaft).

Bleiben die berechneten Regressionskoeffizienten $a$ und $b$ bei Heteroskedastizität im Durchschnitt korrekt?::Ja, sie bleiben **erwartungstreu** (unbiased). Das bedeutet, das Modell schätzt die Linie im Mittel immer noch an der richtigen Position ein, die Unsicherheit über diese Position wird jedoch falsch berechnet.

Was ist das Ziel von robusten Standardfehlern nach White?
?
Sie korrigieren die Verzerrung der Standardfehler, die durch Heteroskedastizität verursacht wird. Dadurch werden die Ergebnisse von Signifikanztests ($t$-Tests) wieder verlässlich, ohne dass die ursprünglichen Regressionskoeffizienten angepasst werden müssen.

Warum führt ein multiplikatives Modell bei Einkommensdaten oft zu Heteroskedastizität in einer additiven OLS-Regression?
?
Weil die absolute Streuung der Ausgaben proportional mit dem Einkommen wächst. Ein additives Modell verlangt jedoch eine absolut konstante Streuung über die gesamte Achse, weshalb die Residuen nach rechts hin trichterförmig aufweiten.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Heteroskedastizität]]
SORT file.mtime DESC
```