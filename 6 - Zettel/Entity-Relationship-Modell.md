#Note

2026-06-09

Tags: 
#datenbanken 

---
Das **Entity-Relationship-Modell (ERM)** wurde 1976 von Peter Chen entwickelt und ist ein semantisches [[Datenmodell]] für den konzeptionellen [[Datenbankentwurf]]. Es dient als universelles Kommunikationsmittel zwischen Anwendern, Analysten und Entwicklern, da es die Fachanforderungen abstrakt und völlig unabhängig von einer spezifischen Datenbanksoftware (z.B. SQL oder [[NoSQL]]) visualisiert.

#### Die 3 Grundbausteine (Chen-Notation)

Das klassische Modell stützt sich auf drei logische Pfeiler:

1. **Entity ([[Entität]]) / Entitytyp:** Ein abgrenzbares Objekt der Miniwelt (Realität). Ein _Entitytyp_ fasst gleichartige Entities strukturiert zusammen (z. B. der Typ "Kunde", das konkrete Entity "Max Mustermann"). Darstellung: **Rechteck**.
2. **[[Attribut]]:** Eine Eigenschaft, die einen Entitytyp detailliert beschreibt (z. B. Name, Preis). Darstellung: **Ellipse / Oval**.
3. **Relationship ([[Beziehung]]) / Relationshiptyp:** Die logische Verknüpfung zwischen zwei oder mehreren Entities (z. B. "Kunde erteilt Auftrag"). Darstellung: **Raute**.

#### Schlüssel und spezielle Attribute

Um Entities eindeutig identifizieren und komplexe Eigenschaften abbilden zu können, definiert das ERM spezifische Attributsformen:

- **Identifikationsschlüssel (Primärschlüssel):** Eine minimale Menge von Attributen, die ein Entity absolut eindeutig macht (z. B. "Kunden-Nr"). Sie werden im ERM durch **Unterstreichung** markiert.
- **Zusammengesetztes Attribut:** Ein Attribut, das in kleinere Folgeattribute unterteilt werden kann (z. B. "Adresse" → "PLZ", "Ort", "Straße").
- **Mehrfachattribut:** Ein Attribut, das für ein einzelnes Entity mehrere Werte gleichzeitig speichern kann (z. B. "vorher besuchte Schulen").

#### Notation und Diagrammsymbole

Das Skript verwendet die klassische **Chen-Notation** sowie die **modifizierte Chen-Notation (MC-Kardinalitäten)**.

| Element            | Darstellung                |
| ------------------ | -------------------------- |
| Entitytyp          | Rechteck                   |
| Relationshiptyp    | Raute                      |
| Attribut           | Ellipse                    |
| Schlüsselattribut  | Unterstrichen              |
| Beziehungsattribut | Ellipse an einer Beziehung |
|                    |                            |

##### Kardinalitäten (Chen)

| Notation | Bedeutung |
|-----------|-----------|
| 1:1 | Eins-zu-eins |
| 1:n | Eins-zu-viele |
| n:m | Viele-zu-viele |

Die klassische Chen-Notation beschreibt die maximale Anzahl möglicher Beziehungen zwischen Entitäten.

##### MC-Kardinalitäten (Modifizierte Chen-Notation)
Die MC-Kardinalität erweitert die klassische Kardinalität um Mindestbeteiligungen.

| Symbol | Bedeutung                |
| ------ | ------------------------ |
| 1      | genau eine               |
| c      | keine oder eine          |
| m      | eine oder mehrere        |
| mc     | keine, eine oder mehrere |

Beispiele:

- Mitarbeiter ist genau einer Abteilung zugeordnet → 1
- Mitarbeiter leitet eventuell eine Abteilung → c
- Jedes Projekt hat mindestens einen Mitarbeiter → m
- Mitarbeiter können an mehreren Projekten arbeiten, müssen aber nicht → mc

--------------------------------------------------------------------------------

### Flashcards

Wie wird ein Entitytyp in der Chen-Notation dargestellt?::Durch ein Rechteck.
<!--SR:!2026-06-14,4,270-->

Wie wird ein Relationshiptyp in der Chen-Notation dargestellt?::Durch eine Raute.
<!--SR:!2026-06-10,0,230-->

Wie wird ein Attribut in der Chen-Notation dargestellt?::Durch eine Ellipse bzw. ein Oval.

Welche Notation verwendet das Skript für ER-Diagramme?::Die klassische Chen-Notation sowie die modifizierte Chen-Notation (MC-Kardinalitäten).

Was bedeutet die Kardinalität 1:n?::Einer Entität können viele Entitäten der Gegenseite zugeordnet sein.

Was bedeutet die Kardinalität n:m?::Viele Entitäten beider Seiten können miteinander in Beziehung stehen.
<!--SR:!2026-06-13,3,250-->

Was bedeutet die MC-Kardinalität 1?::Genau eine Entität ist zugeordnet.
<!--SR:!2026-06-10,0,230-->

Was bedeutet die MC-Kardinalität c?::Keine oder eine Entität ist zugeordnet.

Was bedeutet die MC-Kardinalität m?::Eine oder mehrere Entitäten sind zugeordnet.

Was bedeutet die MC-Kardinalität mc?::Keine, eine oder mehrere Entitäten sind zugeordnet.
<!--SR:!2026-06-10,0,230-->

Wozu dienen MC-Kardinalitäten?::Sie präzisieren die Mindestbeteiligung einer Entität an einer Beziehung.

Wer hat das Entity-Relationship-Modell entwickelt und wann?::Peter Chen im Jahr 1976.
<!--SR:!2026-06-11,1,230-->

Was ist der Hauptvorteil des ER-Modells im Datenbankentwurf?::Es ist technologieunabhängig, reduziert Komplexität durch Abstraktion und dient als visuelle Kommunikationsbasis zwischen Fachabteilung und IT.

Was ist der Unterschied zwischen einem Entity und einem Entitytyp?
?
Ein **Entity** ist ein ganz spezifisches, einzelnes, reales Objekt (z. B. "Anna Schmidt"). Ein **Entitytyp** ist die abstrakte Zusammenfassung gleichartiger Entities in einer Klasse (z. B. "Kunde" oder "Mitarbeiter").

Wie werden Primärschlüssel in der klassischen Chen-Notation dargestellt?::Durch eine Unterstreichung des jeweiligen Attributnamens im Oval.

Was ist ein Mehrfachattribut im ERM?
?
Ein Attribut, das für ein einzelnes Entity mehrere Werte gleichzeitig aufnehmen kann, z. B. das Attribut "Vorher besuchte Schulen" bei einem Schüler. Es wird im Chen-Modell oft durch eine doppelte Ellipse dargestellt.
<!--SR:!2026-06-10,0,230-->


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Entity-Relationship-Modell]]
SORT file.mtime DESC
```