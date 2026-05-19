#Note

2026-05-18

Tags: [[Statistik]], [[Visualisierung]], [[Bivariate Daten]], [[Python]]
#deskriptive_statistik

---
Das **Streudiagramm** (Scatter Plot) dient der Analyse der Beziehung zwischen zwei metrischen Merkmalen. Es ist der erste Schritt jeder bivariaten Analyse, um die Struktur der Datenwolke zu verstehen.

### Einsatzzweck & Interpretation

- **Korrelationscheck:** Liegen die Punkte annähernd auf einer Linie? (Positiv/Negativ/Null-Korrelation).
- **Mustererkennung:** Sind die Daten gleichmäßig verteilt oder bilden sie Gruppen (**Cluster**)?
- **Anomalieerkennung:** Identifikation von **Ausreißern**, die nicht zum restlichen Trend passen.
- **[[Homoskedastizität]]:** Prüfen, ob die Streuung von $Y$ über den gesamten Bereich von $X$ konstant bleibt.
### Vor- und Nachteile

- **Vorteil:** Maximale Detailtiefe; zeigt jeden einzelnen Datenpunkt; deckt nicht-lineare Zusammenhänge auf.
- **Nachteil:** Bei sehr großen Datensätzen tritt **Overplotting** ein (Punkte überlagern sich); keine direkte Information über die Häufigkeit in dichten Bereichen ohne Transparenz-Effekte.
    
### Implementation

```Python
import matplotlib.pyplot as plt
import numpy as np

# Generate synthetic data
np.random.seed(42)
x = np.random.normal(50, 15, 200)
y = 0.8 * x + np.random.normal(0, 10, 200)

# Create scatter plot
plt.figure(figsize=(8, 6))
plt.scatter(x, y, alpha=0.6, edgecolors='w', label='Data points')
plt.title("Scatter Plot: Bivariate Relationship")
plt.xlabel("Independent Variable (X)")
plt.ylabel("Dependent Variable (Y)")
plt.grid(True, linestyle='--', alpha=0.7)
plt.legend()
plt.show()
```

---
### Flashcards

Was ist das Hauptziel eines Streudiagramms vor der Durchführung einer Regressionsanalyse?::Die visuelle Prüfung auf Linearität des Zusammenhangs und die Identifikation von Ausreißern, die das Modell verzerren könnten.

Was versteht man unter "Overplotting" in einem Streudiagramm?::Das Problem, dass bei hohen Datenmengen viele Punkte auf derselben Koordinate liegen und somit eine einzige schwarze Fläche bilden, wodurch die Information über die lokale Dichte verloren geht.

Warum ist ein Streudiagramm für nominalskalierte Daten (z.B. Nationalität) ungeeignet?
?
Da nominale Daten keine numerische Ordnung haben. Die Position im Koordinatensystem wäre rein willkürlich und würde keinen interpretierbaren "Trend" oder "Abstand" ergeben.

Welche visuelle Eigenschaft eines Streudiagramms deutet auf eine starke Korrelation hin?
?
Die Punkte konzentrieren sich eng um eine (gedachte) Gerade oder Kurve. Je schmaler die "Datenwolke", desto stärker ist der statistische Zusammenhang.

---

### Verwendung

Code-Snippet

```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Streudiagramm]]
SORT file.mtime DESC
```