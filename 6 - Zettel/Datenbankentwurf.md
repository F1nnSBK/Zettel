#Note

2026-06-09

Tags: [[Datenbanken]], [[Grundlagen]], [[Datenmodellierung]]
#datenbanken 

---
Die Entwicklung eines [[Datenbanksystem|Datenbanksystems]] ist ein schrittweiser Abstraktions- und Transformationsprozess. Er übersetzt die Anforderungen einer Fachdomäne (die sog. Miniwelt) über mehrere Schichten bis hin zur physischen Speicherung auf der Festplatte.

Die 6 Phasen des [[Daten]]bankentwurfs

|Phase|Ziel & Output|Eigenschaften & Werkzeuge|
|---|---|---|
|**1. Anforderungsanalyse**|Sammlung der funktionalen und informationellen Anforderungen der Use-Cases. Output: **Pflichtenheft**.|Definiert die "Miniwelt" (den relevanten Ausschnitt der Realität). Oft in Prosa, Tabellen oder Formularen verfasst.|
|**2. Konzeptioneller Entwurf**|Erstellung eines abstrakten Datenmodells, das _völlig technologieunabhängig_ ist.|Output: Konzeptuelles Schema (meist als grafisches **[[Entity-Relationship-Modell]]**). Reduziert Komplexität auf wesentliche Strukturen.|
|**3. Logischer Entwurf**|Übersetzung des konzeptionellen Modells in das Paradigma des gewählten DBMS (z. B. das Relationenmodell).|Beinhaltet die **[[Abbildungsregeln]]** (z.B. für Tabellen) und die **[[Normalisierung]]**, um Anomalien und Redundanzen zu verhindern.|
|**4. Datendefinition**|Physische Umsetzung des logischen Schemas im eigentlichen Datenbanksystem.|Die Tabellen und Integritätsbedingungen werden mittels Data Definition Language (**DDL**), z. B. `CREATE TABLE`, angelegt.|
|**5. Physischer Entwurf**|Definition des _Internen Schemas_ zur Festlegung hardwarenaher Zugriffsmechanismen.|Fokus liegt auf der reinen Performance-Optimierung (z. B. Festlegung, auf welche Festplatten sich eine Tabelle verteilt oder Index-Erstellung).|
|**6. Implementierung & Wartung**|Laufender Betrieb und ggf. dynamische Anpassungen.|Gewährleistung von Performance und Integrität. Kann heute teilweise durch Self-Tuning-Mechanismen automatisiert werden.|

--------------------------------------------------------------------------------

### Flashcards

Was ist das Kernziel des konzeptionellen Datenbankentwurfs?::Die Erstellung eines komplett DBMS-unabhängigen, abstrakten Datenmodells (z. B. ERM), das die Informationsanforderungen (Use-Cases) der Fachdomäne abbildet.
<!--SR:!2026-06-10,0,230-->

Wie unterscheidet sich der konzeptionelle vom logischen Entwurf?
?
Der konzeptionelle Entwurf (Phase 2) ist reine Modellierung der Realität und völlig technologieunabhängig. Der logische Entwurf (Phase 3) transformiert dieses Modell zwingend in die Struktur des gewählten Datenbanksystems (z. B. in relationale Tabellen) und wendet Regeln wie die Normalisierung an.

Welche Rolle spielt die DDL in den Phasen des Datenbankentwurfs?::Sie wird in der "Datendefinitions-" bzw. Implementierungsphase eingesetzt, um das logisch entworfene Schema physisch in der Datenbank per SQL-Befehl (z. B. `CREATE TABLE`) anzulegen.

Worauf fokussiert sich der physische Entwurf einer Datenbank?
?
Auf die Festlegung der konkreten Zugriffsmechanismen und der Speicherorganisation (Internes Schema). Das primäre Ziel ist die Optimierung der Performance, z. B. durch Indexierung oder die Verteilung der Daten auf verschiedene physische Festplatten.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Datenbankentwurf]]
SORT file.mtime DESC
```