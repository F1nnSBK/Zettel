
Motivation: Trainingsfehler & Testfehler sind oft nicht gleich -> wegen Bias - Variance Tradeoff
Vorsichtig beim Treffen von Entscheidungen je nach Datenbasis (Training/Test - bei Training Overfitting und bei Test Data Leakage Entscheidungen auf Basis von Test Daten heißen auchn, das Modell hat die Daten bereits "gesehen")
-> Wir brauchen 3 geteilte Daten - Train/Val/Test

Terminologie
Trainingsdaten + Validierungsdaten -> Dev-Set
Testdaten

Hold-Out Validation
Re-Training eines Modells mit verschiedenen Teilmengen des Dev-Sets
Nachteile Fehlereinschätzung

K-fold cross-validation
Leave-One-Out CV (LOOCV) Vorteile, wenn es eine "Abkürzung"? gibt
Bootstrap aus der Statistik - auch interessant für Ensembles
Mit dem eigenen Stiefel aus dem Sumpf ziehen
Baron Munchausen?
kennst man zb auch mit booten von anderen Systemen (Informatik) - etwas anders
Gerne großes K aber dann wird Val Set klein also Bootstrap mit zufälligen Aufteilungen und ziegen MIT Zurücklegen Duplikate -> Ja aber nicht schlimm
Man landet oft bei 1/3 Val und 2/3 Training (Statistisch oft so)

Was richtig sein kann und schiefgehen könnte
Falsche Anwendung der Validierungs-Methoden s.29 Beispie
Trainingsdatenset so groß wie das Dev-Set
Fehler Overfitting S.30 sehr anschaulich
Passiert gern durch Ease-of-use und Flüchtigkeit/fehlende Fachkenntnisse
Nested Cross Validation
















