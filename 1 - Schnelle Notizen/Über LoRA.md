
https://thinkingmachines.ai/blog/lora/

Pre-Training -> trillionen von Parametern auf trillionen von Tokens trainiert
Post-Training -> tausende bis millionen Parameter (viel weniger) um auf ein spezifisches Problem angepasst zu reagieren.

Konflikt: Terabit an Gewichten für nur gigabit oder megabit an Trainingsdaten?
-> Sieht aus wie Verschwendung / Ineffizienz

Lösung: PEFT (Parameter efficient fine tuning) -> Ziel ist ein Barebone (Pretrained Model) mit nur wenigen Anpassungen auf eine Anwendung anzupassen

Die führende Methode in PEFT ist low-rank Adaptation (LoRA). LoRA updatet jede Gewichtsmatrix $W$ eines Models mit einer modifizierten Version $W'$:
$$W' = W + \gamma AB$$
Dabei sind $B$ und $A$ Matrizen mit einem geringeren Rang (Sie haben weniger Parameter als $W$) und $\gamma$ ist ein konstanter Skalierungsfaktor. 
LoRA erzeugt also eine niederdimensionale Repräsentation der Updates, die beim Fine Tuning notwendig sind (Grundlage [[Singulärwertzerlegung]]).


