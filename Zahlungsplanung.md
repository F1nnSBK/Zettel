#Note

2025-12-04

Tags: [[Cash Flow]], [[Dynamische Investitionsrechenverfahren]], [[Zeitwert des Geldes]]

---
Bei der **Zahlungsplanung** werden die erwarteten Cash Inflows und Cash Outflows aus einer [[Investition]] für den Zeitraum der Durchführung geschätzt. Als Ergebnis bleibt der Erwartete Free Cash Flow.

|                        | Jahr 1 | Jahr t |
| ---------------------- | ------ | ------ |
| Investitions-Cash Flow | -100   | ...    |
| + Operativer Cash Flow | 30     | ...    |
| = Free Cash Flow       | -70    | ...    |

#### Zeitstrahl
Der Zeitstrahl ist oft bei langfristigen Projekten ein erstes Werkzeug um [[Cash Flow|Cash Flows]] über den Projektzeitraum darzustellen.


Bei Vergleichen von langfristigen Projekten sollten die Projekte mit dem höchsten Gesamtzahlungszufluss gewählt werden. Allerdings gelten hier wichtige Regeln:

**Regel 1:** Nur Zahlungen zum gleichen Zeitpunkt können verglichen oder zusammengelegt werden Ein Euro heute und ein Euro in einem Jahr sind nicht gleichwertig. Heute Geld zu besitzen ist wertvoller, da dieses einen Zinsertrag erwirtschaften kann. Um daher Zahlungen vergleichen zu können, müssen sie auf den gleichen Zeitpunkt "verschoben" werden. Hier kommt Regel 2 zur Anwendung.

**Regel 2:** Zahlungen in die Zukunft verschieben Um eine Zahlung um ein Jahr in die Zukunft zu verschieben, wird die Annahme getroffen, dass wir das Geld für ein Jahr anlegen und einen Zinssatz $i$ erhalten können. Dies wird als Aufzinsung bezeichnet.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Zahlungsplanung]]
SORT file.mtime DESC
```