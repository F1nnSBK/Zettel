#Note

2025-12-15

Tags: [[Projektmanagement]], [[Planung]], [[PSP]], [[WBS]]
#pm

---
Der **Projektstrukturplan (PSP)** (engl. Work Breakdown Structure - WBS) ist die hierarchische Gliederung der Gesamtaufgabe des Projekts in plan- und kontrollierbare Teilaufgaben und Arbeitspakete. Er ist die "Mutter aller Pläne".

#### 1. Aufbau und Funktion
Der PSP zerlegt den kompletten Projektinhalt (Scope) in kleinere, handhabbare Einheiten.
- **Ziel:** Vollständige Erfassung aller zu erledigenden Aufgaben ("Was nicht im PSP steht, findet im Projekt nicht statt").
- **Ebene:** Vom Groben (Projekt) zum Detail (Teilprojekte $\rightarrow$ Teilaufgaben $\rightarrow$ Arbeitspakete).

#### 2. Das Arbeitspaket (AP)
Das **Arbeitspaket** (Work Package) ist das kleinste Element im PSP (die unterste Ebene).
- **Merkmale:**
    - Klare Ergebnisse (Liefergegenstände/Deliverables).
    - Einem Verantwortlichen zugeordnet.
    - Basis für die Schätzung von **Aufwand**, **Dauer** und **Kosten**.
    - Basis für die **Fortschrittsmessung** im Controlling (z.B. 0-100% Methode).
    

Pro-Tipp aus dem Risikomanagement:
Füge auch optionale Arbeitspakete hinzu, die nicht zwingend notwendig sind. Diese können bei Problemen weggelassen werden ("Scope als Puffer"), ohne das Projektziel zu gefährden.

#### 3. Gliederungsprinzipien
Wie zerlege ich das Projekt?

A) Funktionsorientierter PSP
Gliederung nach Tätigkeiten oder Phasen.
- _Beispiel:_ Analyse $\rightarrow$ Design $\rightarrow$ Implementierung $\rightarrow$ Test $\rightarrow$ Rollout.
- _Vorteil:_ Entspricht oft dem Projektablauf (Phasen).
    

B) Objektorientierter PSP
Gliederung nach Bestandteilen des Produkts (Physisch/Logisch).
- _Beispiel (Auto):_ Motor $\rightarrow$ Karosserie $\rightarrow$ Innenraum $\rightarrow$ Elektronik.
- _Vorteil:_ Klare Zuordnung von Verantwortlichkeiten für Komponenten.

_(In der Praxis oft gemischt: Ebene 1 nach Phasen, Ebene 2 nach Objekten)._


![[Pasted image 20251215185123.png]]

---
#### Flashcards

Was ist die Hauptaufgabe des Projektstrukturplans (PSP)? :: Er zerlegt den gesamten Projektumfang hierarchisch in planbare Teilaufgaben und Arbeitspakete.

Was befindet sich auf der untersten Ebene des PSP? :: Die **Arbeitspakete**.

Nach welchen zwei Hauptprinzipien kann ein PSP gegliedert werden? :: **Funktionsorientiert** (nach Tätigkeiten/Phasen) oder **Objektorientiert** (nach Gegenständen/Bauteilen).

Wofür bilden Arbeitspakete die Grundlage? :: Für die Termin- und Kostenplanung sowie die Fortschrittskontrolle.

Wie kann der PSP zum Risikomanagement beitragen? :: Durch die Definition von **optionalen Arbeitspaketen**, die als Manövriermasse (Puffer) dienen können.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Projektstrukturplan]]
SORT file.mtime DESC
```