#Note

2026-06-09

Tags: [[Datenbanken]], [[Datenbankentwurf]], [[Entity-Relationship-Modell]]
#datenbanken 

---
Die **Assoziation** ist im konzeptionellen Datenbankentwurf die konkrete Beschreibung eines Beziehungstyps zwischen Entitätstypen. Sie benennt die Art der Interaktion in der Miniwelt (meist durch aktive oder passive Verben, z.B. "Kunde _erteilt_ Auftrag" oder "Abteilung _wird geleitet von_ Mitarbeiter").

Abgrenzung: Assoziation vs. [[Kardinalität]]

Diese beiden Begriffe werden oft synonym verwendet, sind aber logisch getrennt zu betrachten:

- **Assoziation:** Beschreibt die _logische Verbindung_ zwischen zwei Entitätstypen qualitativ.
- **Kardinalität:** Spezifiziert die Assoziation _quantitativ_. Sie legt fest, wie viele Instanzen (Entities) des einen Typs mit wie vielen Instanzen des anderen Typs in Beziehung stehen können (z.B. eins-zu-eins, eins-zu-viele).

Richtungsdualität (Bidirektionalität)

Eine Assoziation funktioniert im ERM zwingend in beide Richtungen. Um sie fehlerfrei zu modellieren und später die richtigen Kardinalitäten zu setzen, muss die Assoziation immer in **zwei gerichtete Teilbeziehungen** zerlegt und hinterfragt werden:

1. Fragestellung A → B: _Wie viele Lieferanten können einen Artikel grundsätzlich liefern?_
2. Fragestellung B → A: _Wie viele Artikel kann ein Lieferant grundsätzlich liefern?_

Physische Abbildung im [[Relationenmodell]]

Während die Assoziation im konzeptionellen Entity-Relationship-Modell (ERM) als Raute gezeichnet wird, muss sie im logischen Entwurf übersetzt werden (Abbildungsregeln):

- **Über Fremdschlüssel (Foreign Keys):** Um Assoziationen darzustellen, werden im Relationenmodell Spalten genutzt, die einen Verweis auf den Primärschlüssel einer anderen Tabelle herstellen.
- **Über Assoziationstabellen:** Bei n:m-Assoziationen reicht ein einfacher Fremdschlüssel nicht aus; es wird eine eigene Beziehungs- bzw. Assoziationstabelle generiert, die beide Primärschlüssel als zusammengesetzten Schlüssel aufnimmt.

--------------------------------------------------------------------------------

### Flashcards

Was bezeichnet der Begriff "Assoziation" im Entity-Relationship-Modell?::Die konkrete inhaltliche Beschreibung eines Beziehungstyps zwischen zwei [[Entität]]stypen (z.B. "Kunde erteilt Auftrag").
<!--SR:!2026-06-10,0,230-->

Wie grenzt sich die Assoziation von der Kardinalität ab?
?
Die Assoziation beschreibt die Beziehung rein qualitativ (dass und wie zwei Typen in Verbindung stehen). Die Kardinalität hingegen spezifiziert die Assoziation quantitativ (wie viele Instanzen miteinander interagieren, z.B. 1:n).

Warum muss eine Assoziation bei der Modellierung immer bidirektional betrachtet werden?
?
Weil Beziehungen in der Realität in beide Richtungen funktionieren. Um die korrekte mengenmäßige Ausprägung zu finden, muss man die Assoziation in zwei Teilbeziehungen zerlegen (z.B. "Lieferant liefert wie viele Artikel?" und "Artikel wird geliefert von wie vielen Lieferanten?").
<!--SR:!2026-06-10,0,230-->

Wie werden Assoziationen im klassischen relationalen Datenbankmodell physisch implementiert?
?
Sie werden durch Fremdschlüssel (Foreign Keys) dargestellt, die referenzielle Integrität zu einem Primärschlüssel einer anderen Tabelle herstellen, oder bei n:m-Kardinalitäten durch die Erstellung einer eigenen Assoziationstabelle.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Assoziation]]
SORT file.mtime DESC
```