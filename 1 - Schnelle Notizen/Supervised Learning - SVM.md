
Hyperebene
affiner Unterraum - affin? Mit Dimension d-1
$f(\vec{x})=n_{}+ \vec{n}^T\vec{x}$

Hard Margin Clf
Support Vektoren -> Punkte exakt auf den Margingrenzen

Maximierung des Margins S.14 -> Training Hard Margin Clf
Bzw wenn eindeutige Trennung nicht möglich ist -> Soft Margin Clf (Support Vector Classification). Wir haben NB aufgeweicht, einige Punkte dürfen Margin verletzen S. 18

Kernel 
Erweiterung der Feature-Raumes
zb mit Polynomen -> Hat auch Probleme zb geschlossene Kreise, Frage nach der Ordnung, ...
andere Möglichkeit, nicht mit Polynomen
Abstände zwischen den Punkten zu "Zentroiden" Radial-Kernel {RBF Kernelfunktion} -> Radial (Symmetrie und Definitheit -> Hier nicht die von Matrizen sondern von Funktionen)

Kernel-Trick
-> Vermeidung des Curse of Dimensionality
Skalarprodukt ist inneres Produkt und in der Kernelfunktion ist auch ein inneres Produkt NACHDEM man es in einen hochdimensionalen Raum transformiert hat (schöne Folie S.32/33)
Problem man kann Mapping-Funktion $\phi(\vec{x}_i)$ nicht bestimmen

Hyperebenengleichung transformiert:

Was macht das gamma bei der exp() -> Wenn es größer wird, Modell wird komplexer
$$$$ S.33!
Trick des Tricks ist -> Übertragung in den hochdimensionalen Raum mit genauer Mapping Function nicht notwendig, die Kernelfunktion reicht uns wiel wir die Mapping Funktion dazu umschreiben können -> $\alpha_i$ kann 0 werden, dann hat ein Datenpunkt keine Einwirkung, alles wo $\alpha_i$ nicht null ist, ist ein Stützverktor (Support Vector)
Bestimmung der Klasse über Vorzeichen: S. 35
One vs. All (OVA) -> Eine gegen alle
One vs. One (OVO) -> Alle paarweisen Vergleiche

Welches Modell wann wählen?
Linear? Exakt Trennbar? Nichtlinear? Wahrscheinlichkeiten (Explainability)? Komplex?
Schreibe die verschienden Modelle für ihre Einsatzbereiche auf
Kernel auch für LR und LDA
C als Parameter für die Verletzung der Margins gern auch als Kehrwert
SVMs Overfitten schnell wegen hochdimensionalem Raum -> Regularisierung?







