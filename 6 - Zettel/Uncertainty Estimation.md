#Note

2026-05-03

Tags: [[Uncertainty Estimation]], [[Aleatoric]], [[Epistemic]], [[OOD Detection]], [[Unsupervised Learning]]
#UL

---
In der Anwendung ist es entscheidend, nicht nur Vorhersagen zu treffen, sondern zu wissen, wie sehr man diesen vertrauen kann. Neuronale Netze neigen dazu, auf unbekannten Daten (Out-of-Distribution) mit hoher Konfidenz falsch zu liegen, da die **Softmax-Funktion** Ausgaben immer auf eins normiert und somit eher interne Ähnlichkeit als absolute Korrektheit widerspiegelt. Sie wissen nicht, was sie nicht wissen!


### Die zwei Quellen der Unsicherheit

- **Aleatorische Unsicherheit:** Beschreibt das inhärente Rauschen in den Daten (z. B. Sensorrauschen). Sie ist „irreduzibel“, was bedeutet, dass sie auch durch das Sammeln von mehr Trainingsdaten nicht verschwindet.

- **Epistemische Unsicherheit:** Beschreibt die Unwissenheit des Modells aufgrund fehlender Erfahrung in einem Datenbereich. Sie ist „reduzierbar“, da sie durch die Aufnahme von mehr Daten aus diesem Bereich verringert werden kann.


### Methoden zur Unsicherheitsschätzung

Da Standardmodelle keine eingebaute Unsicherheitsmetrik haben, werden spezialisierte Ansätze genutzt:

- **MC Dropout:** Während der Inferenz wird Dropout aktiv gelassen (stochastisches Rauschen in den Parametern). Die Varianz mehrerer Durchläufe dient als Schätzer für die epistemische Unsicherheit.

- **Confidence by Reconstruction:** Basierend auf VAE-Architekturen wird ein Input rekonstruiert. Liegt ein Input außerhalb der gelernten Verteilung, kollabiert die Rekonstruktion auf die bekannte Domäne, was zu einem hohen Rekonstruktionsfehler führt und so Out-of-Distribution (OOD) Samples markiert.

- **Calibration (ECE):** Die statistische Anpassung der Konfidenzwerte an die tatsächliche empirische Genauigkeit des Modells.

- **Confidence Head:** Ein separater Teil des Netzwerks wird darauf trainiert, vorherzusagen, ob das Hauptmodell bei einem gegebenen Input wahrscheinlich richtig liegt.

### Operative Anwendung

- **ODD (Operational Design Domain):** Definiert den Bereich, für den ein System ausgelegt wurde. Unsicherheitsschätzung erkennt, wenn das Modell die ODD verlässt.
- **Anomaly Detection:** Modelle werden auf „normalen“ Daten trainiert, um alles Ungewöhnliche ohne explizite Label als Anomalie zu flaggen.

---
#### Flashcards

Was unterscheidet aleatorische von epistemischer Unsicherheit hinsichtlich der Datenmenge? :: Aleatorische Unsicherheit ist durch mehr Daten nicht reduzierbar (inhärentes Rauschen), während epistemische Unsicherheit durch das Training mit zusätzlichen Daten in unbekannten Regionen verringert werden kann.
<!--SR:!2026-06-08,0,230-->

Warum ist eine hohe Softmax-Konfidenz bei OOD-Daten (Out-of-Distribution) problematisch?
?
Softmax erzwingt eine Normierung der Ausgaben auf 1, wodurch das Modell gezwungen wird, eine Wahrscheinlichkeit zu vergeben, selbst wenn der Input keiner gelernten Klasse ähnelt. Dies führt zu „High-Confidence-Fehlern“.
<!--SR:!2026-06-09,1,230-->

Wie schätzt MC Dropout die Unsicherheit eines Modells zur Testzeit?
?
Durch das Beibehalten von Dropout-Layern während der Inferenz werden für denselben Input leicht unterschiedliche Ergebnisse generiert. Die Varianz (Streuung) dieser Ergebnisse korreliert mit der epistemischen Unsicherheit des Modells.
<!--SR:!2026-06-08,0,230-->

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Uncertainty Estimation]]
SORT file.mtime DESC
```