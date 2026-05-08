
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

Vorteile und Gründe LoRA Full Fine Tuning Techniken (hensowrth, FullFT) vorzuziehen:
- Multi-Tenant Serving: Mehrere Adapter (die $A$ und $B$ Matrizen) können bei der Inferenz bereitgehalten werden und je nach Anwendungsfall benutzt werden (Hot Swapping).
- Layout Size for Training: Bei FullFT müssen die Gewichte und den Optimizer Status mitgespeichert werden, es braucht deutlich mehr Speicherplatz und mehr Rechenleistung. LoRA ist deutlich zugänglicher.
- Ease of Loading and Transfer: LoRA Adapter können schnell und einfach zwischen verschiedenen Machinen transportiert/aufgesetzt werden. 

LoRA beleibtheit wächst seit initial Paper aus 2021 ([LoRA: Low-Rank Adaptation of Large Language Models](https://arxiv.org/abs/2106.09685) (Hu et al, 2021)) aber es ist noch nicht so bekannt, wie LoRA im Vergleich zu FullFT performt.

Die Kernfrage ist, kommt LoRA an FullFT ran? - und wenn ja, unter welchen Bedingungen? Schulman zeigt -> Ja, wenn ein paar Details stimmen erreicht man eine sehr gute Performance, so wie beim FullFT.
