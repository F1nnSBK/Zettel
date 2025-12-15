#Note

2025-12-15

Tags: [[Projektmanagement]], [[Qualitätsmanagement]], [[Methoden]]
#pm

---
Qualitätswerkzeuge dienen dazu, Fehlerursachen zu finden, Probleme zu priorisieren und die Einhaltung von Standards sicherzustellen.

#### 1. Analysetechniken (Fehlersuche)

**A) Ishikawa-Diagramm (Fischgräten-Diagramm)** Ein Ursache-Wirkungs-Diagramm zur systematischen Analyse von Problemursachen.
- **Aufbau:** Der "Kopf" ist das Problem (Wirkung). Die "Gräten" sind die Hauptursachen-Kategorien.
- **Die 5-M-Methode (Kategorien):**
    - **M**ensch (Mitarbeiter qualifiziert?)
    - **M**aschine (Werkzeug defekt?)
    - **M**aterial (Rohstoff schlecht?)
    - **M**ethode (Prozess falsch?)
    - **M**ilieu (Umgebung/Lärm?)
    - _(oft ergänzt um **M**essung)_
        
- **Ziel:** Finden der _Wurzel_ des Problems (Root Cause Analysis).
    

**B) Pareto-Diagramm (80/20-Regel)** Ein Säulendiagramm zur Priorisierung von Fehlerursachen.
- **Prinzip:** 80% der Probleme werden durch 20% der Ursachen ausgelöst.
- **Vorgehen:** Fehler zählen, nach Häufigkeit sortieren und kumulieren.
- **Ziel:** Sich auf die "Vital Few" (die wenigen Wichtigen) konzentrieren, statt sich mit den "Trivial Many" (den vielen Unwichtigen) zu verzetteln.
    

#### 2. Prüftechniken (Sicherung & Kontrolle)

**A) Checklisten** Einfachstes, aber effektivstes Mittel gegen Vergesslichkeit. Sicherstellung der Vollständigkeit (z.B. "Wurde das Backup erstellt?", "Ist der Raum gebucht?").
**B) Reviews & Audits**
- **Review:** Das Team oder Kollegen prüfen ein Ergebnis (z.B. Code-Review, Dokumenten-Review). Fokus: Inhaltliche Korrektheit.
- **Audit:** Eine _unabhängige_ Instanz prüft, ob Prozesse und Standards eingehalten wurden. Fokus: Prozesskonformität (Compliance).
    

**C) Retrospektive (Lessons Learned)** Regelmäßiges Team-Meeting (besonders im Agilen), um die _Zusammenarbeit_ und _Prozesse_ zu verbessern.
- Frage: Was lief gut? Was lief schlecht? Was ändern wir? (KALM)
- Ziel: Kontinuierliche Verbesserung (KVP / CIP).
    

---
#### Flashcards

Welches Diagramm nutzt man zur Ursache-Wirkungs-Analyse? :: Das **Ishikawa-Diagramm** (Fischgräten-Diagramm).

Welches Diagramm nutzt man zur Priorisierung von Fehlerursachen nach Häufigkeit? :: Das **Pareto-Diagramm**.

Was sind die "5 M" im Ishikawa-Diagramm? :: Mensch, Maschine, Material, Methode, Milieu.

Was ist das Ziel einer Retrospektive? :: Die kontinuierliche Verbesserung der Prozesse und der Zusammenarbeit im Team (Lernen aus Erfahrung).

Was ist der Unterschied zwischen Qualitätssicherung (QA) und Qualitätskontrolle (QC)? :: **QA** ist präventiv (Prozessverbesserung, Fehlervermeidung), **QC** ist reaktiv (Testen, Fehlerfinden am Produkt).




---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Qualitätswerkzeuge]]
SORT file.mtime DESC
```