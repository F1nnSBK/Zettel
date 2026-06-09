
Was sind künstliche Neuronen
Vektor x. geht rein, irgendwas wird berechnet, zahl y kommt raus

Häufig aber nicht immer in Schichten geordnet
Auch genannt: Multi Layer Perceptron
Dense Laysers - Fully Connected (Alle Neuronen sind mit jedem Neuron der Nächsten Schicht verbunden)
Frage: Ist ein MLP vll einfach ein gerichteter azyklischer Graph?

Durchbruch mit Stable Diffusion
Anwendungen
AlphaFold, Chemie SMILES Bombardelli et al., Physik Tompson et al. (2016) mit CNNs

Grenzen: Qualität
Halluzination, Verständnis, Context, ...
Folie S.27
zvonx ist gleich w hoch t mal x plus b 
Neuron als schachtelung von funktionen, f von x ist gleich g von z von x ist gleich g von w hoch t mal x + b
x einfabe f von ist ist ausgabe z von x ist voraktivierung (linearer Operator), w gewichte und b bias und g(cdot) aktivierungsfunktion, erweiterungen Spiking Neurons, Quantum Neurons

Aktivierungsfunktionen
Nichtlinearer Teil mit wichtiger Eigenschaft, differenzierbar bei 0 setzen wir nen wert fets, also auch 0 weil die funktion an 0 nicht analytisch differenzierbar ist. Zb quadireren / Absolutwert
Sigmoid Aktivierungsufnktionm logistische ufnktion/sigmoid funktion ist das gleiche

Mehrere Klassem aug einem Bild -> SIGMOID
TanH Avtivation
Anknüpfungspunkte Stat/ML
Einzelnes Neuron: Lineares Regressionsmodell
wenn SIGMOID Aktivierung: Logistische RgressionnN
Neuronales Netz:

Neuronales Netz - Inferenz
Matrixmultiplikation 2. 39
Jeades neuron ist eig nix anderes als ein skalarprofkut + Bias
Matrixmultiplikation gut auf parallerer Hardware GPU/TPU
Spaltenweise / Teilenweise aufpassen, gerne ist das mal vertauscht

x - f - f(x)

Computation Graph
x - z - sigma - z - sigma - f(x)
   W_0             W_1

Trick um den Bias in das Skalarprodukt reinzuziehen mit Designmatrix, heißt eine Spalte mit nur 1en in $\vec{x}$ und dann darf $\vec{b}$ in $\vec{w}^T$ hinein.

Muss nicht strikt sequentiell erfolgen

Training von Parameter / Gewichte finden
S.50
Loss Differenzierbar muss sein
Merkmale: s: 51
Oft auch mit Regularisierung um die Modellkomplexität zu steuern

Verkettung differenzierbarer Knoten (Backpropagation)
Über die Kettenregel der Differentialrechnung
Forward Pass rechnen können für die Klausur, Loss dabei haben als Ende der Berechnung
Optimierung mit Backprop und Gradient Descent S.53

Modellarchitektur 
CNN, Skip / Residual, Rekurrente Schichten, LSTM, GRU, Transformer Blöcke
Die Architektur selbst kann nicht direkt durch Backprop optimiert werden
Neural Architecture Search



