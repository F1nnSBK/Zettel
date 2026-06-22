#Note

2026-06-22

Tags: [[IT-Sicherheit]], [[Risikomanagement]], [[Projektmanagement]]
#it_security

---

### PDCA- und SDCA-Zyklus

In der IT-Sicherheit und im Qualitätsmanagement werden der **PDCA-** und der **SDCA-Zyklus** als komplementäre Steuerungsmodelle eingesetzt, um kontinuierliche Verbesserung (KVP) und betriebliche Stabilität sicherzustellen.

```
       ▲  [PDCA] (Verbesserung/Optimierung) -> Hebt das Niveau
       │  Plan -> Do -> Check -> Act
  ─────┼──────────────────────────────────────────────────────────
       │  [SDCA] (Stabilisierung/Erhaltung) -> Sichert das Niveau
       ▼  Standardize -> Do -> Check -> Act
```

---

#### 1. Der PDCA-Zyklus (Plan-Do-Check-Act)
Der PDCA-Zyklus (auch Deming-Kreis) dient der **Weiterentwicklung und Verbesserung** von Prozessen.
* **Plan (Planen)**: Analyse des Ist-Zustands, Definition von Zielen und Entwurf von Maßnahmen.
* **Do (Umsetzen)**: Testen und Implementieren der Maßnahmen in einem kleinen/kontrollierten Rahmen.
* **Check (Überprüfen)**: Messen der Ergebnisse und Vergleich mit den Zielen aus der Plan-Phase.
* **Act (Handeln/Verankern)**: Großflächige Einführung der Maßnahme oder Anpassung bei Fehlern.

---

#### 2. Der SDCA-Zyklus (Standardize-Do-Check-Act)
Der SDCA-Zyklus dient der **Standardisierung und Stabilisierung** bestehender Prozesse, um Abweichungen zu verhindern.
* **Standardize (Standardisieren)**: Etablierung klarer Vorgaben und Richtlinien (z. B. SOPs, Playbooks) auf Basis bewährter Abläufe.
* **Do (Ausführen)**: Durchführung der Arbeit exakt nach dem festgelegten Standard.
* **Check (Überprüfen)**: Kontinuierliche Messung, ob der Standard eingehalten wird und wie stabil der Prozess läuft.
* **Act (Handeln)**: Korrekturmaßnahmen ergreifen, falls Abweichungen vom Standard auftreten.

---

#### ⚖️ Zusammenwirken in der Praxis
PDCA und SDCA arbeiten in einem fortlaufenden Wechselspiel:
1. **Stabilisierungsphase (SDCA)**: Ein IT-System wird nach festgelegten Sicherheitsrichtlinien betrieben. Routineüberprüfungen stellen sicher, dass alle Systeme gepatcht sind (Standard wird gehalten).
2. **Verbesserungsphase (PDCA)**: Ein schwerer Vorfall oder eine neue Bedrohungslage erfordert die Einführung eines neuen Sicherheitstools (z. B. EDR). Ein PDCA-Zyklus wird gestartet, um das Tool zu evaluieren und einzuführen.
3. **Etablierung des neuen Standards**: Nach erfolgreichem PDCA wird das Tool in den regulären Betrieb übernommen. Es startet ein neuer SDCA-Zyklus auf diesem höheren Sicherheitsniveau.

**Verknüpfte Zettel:**
- [[Projektmanagement]] (Allgemeine Ablauf- und Steuerungsmodelle)

---
#### Flashcards

Wofür stehen die Abkürzungen PDCA und SDCA?::PDCA steht für Plan-Do-Check-Act; SDCA steht für Standardize-Do-Check-Act.

Wie unterscheiden sich PDCA und SDCA in ihrer Zielsetzung?::PDCA zielt auf die kontinuierliche Verbesserung und Hebung des Sicherheitsniveaus ab. SDCA zielt auf die Erhaltung und Stabilisierung eines bereits erreichten Standards ab.

Wann geht ein PDCA-Zyklus in einen SDCA-Zyklus über?::Sobald eine neue Sicherheitsmaßnahme (PDCA) erfolgreich implementiert und verifiziert wurde, wird sie als neuer Standard festgeschrieben und geht in die Überwachung (SDCA) über.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[PDCA- und SDCA-Zyklus]]
SORT file.mtime DESC
```
