#Note

2026-05-19

Tags: [[Statistik]], [[Stochastik]], [[Wahrscheinlichkeitsrechnung]], [[Mengenlehre]]
#stochastik

---
Die **Ereignisalgebra** nutzt die Werkzeuge des **Mengenkalküls**, um logische Verknüpfungen zwischen verschiedenen Ereignissen mathematisch exakt zu beschreiben. Der Grundraum $\Omega$ fungiert dabei als die "Allmenge" (das Universum).

### Die Kernoperationen

|**Stochastischer Begriff**|**Logische Bedeutung**|**Mengensymbol**|**Mathematische Notation**|
|---|---|---|---|
|**Gegenereignis (Komplement)**|"Nicht $A$"|$\bar{A}$ oder $A^c$|$\{\omega \in \Omega \mid \omega \notin A\}$|
|**Vereinigungsereignis**|"$A$ oder $B$ (oder beide)"|$A \cup B$|$\{\omega \in \Omega \mid \omega \in A \lor \omega \in B\}$|
|**Durchschnittsereignis**|"$A$ und $B$ gleichzeitig"|$A \cap B$|$\{\omega \in \Omega \mid \omega \in A \land \omega \in B\}$|
|**Differenzereignis**|"$A$, aber nicht $B$"|$A \setminus B$|$\{\omega \in \Omega \mid \omega \in A \land \omega \notin B\}$|

### Wichtige Spezialfälle & Gesetze

- **Sicheres Ereignis:** Der gesamte Grundraum $\Omega$. Es tritt immer ein ($P(\Omega) = 1$).
    
- **Unmögliches Ereignis:** Die leere Menge $\emptyset$. Es kann niemals eintreffen ($P(\emptyset) = 0$).
    
- **Disjunktheit (Unvereinbarkeit):** Wenn zwei Ereignisse keine gemeinsamen Elementarereignisse besitzen:
    
    $$A \cap B = \emptyset$$
    
    _Bedeutung:_ Beide Ereignisse können niemals gleichzeitig eintreffen (z.B. "Würfeln einer 3" und "Würfeln einer 4").
    

### Die Gesetze von De Morgan

Unerlässlich für das Vereinfachen komplexer Terme in Beweisen oder Berechnungen:

1. $\overline{A \cup B} = \bar{A} \cap \bar{B}$ (Das Gegenteil von "$A$ oder $B$" ist "Nicht $A$ UND nicht $B$")
    
2. $\overline{A \cap B} = \bar{A} \cup \bar{B}$ (Das Gegenteil von "$A$ und $B$" ist "Nicht $A$ ODER nicht $B$")
    
---
### Flashcards

Was bedeutet das Symbol $A \cap B = \emptyset$ für das gleichzeitige Auftreten der beiden Ereignisse?::Die Ereignisse sind **disjunkt** (unvereinbar); sie besitzen keine gemeinsamen Schnittpunkte und können folglich niemals gleichzeitig eintreffen.

Wie übersetzt man den mathematischen Ausdruck $A \cup B$ in die stochastische Umgangssprache?::Das Ereignis $A$ **oder** das Ereignis $B$ tritt ein, wobei das "Oder" inklusiv ist – es können also auch beide Ereignisse gleichzeitig eintreffen.

Was besagt das erste Gesetz von De Morgan ($\overline{A \cup B} = \bar{A} \cap \bar{B}$) in Worten?
?
Dass das Nicht-Eintreffen von mindestens einem der beiden Ereignisse ($A$ oder $B$) genau dann gegeben ist, wenn weder $A$ eintrifft **noch** $B$ eintrifft.

Aus welchen Elementarereignissen besteht das Differenzereignis $A \setminus B$?
?
Aus allen Elementarereignissen, die in der Menge $A$ enthalten sind, aber **nicht** gleichzeitig in der Menge $B$ liegen.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Ereignisalgebra]]
SORT file.mtime DESC
```