#Note

2026-05-15

Tags: [[Statistik]], [[Deskriptive Statistik]], [[Lagemasse]], [[Nominalskala]]
#deskriptive_statistik

---
Der **Modus** (auch Modalwert) $x_{mod}$ ist der Wert einer Beobachtungsreihe, der am häufigsten vorkommt. Er repräsentiert das "Zentrum" im Sinne der Popularität oder größten Dichte.

### Definition und Eigenschaften

- **Anforderung:** Erfordert lediglich Nominalskalenniveau (ist aber für alle Skalenniveaus berechenbar).
- **Eindeutigkeit:** Er muss nicht eindeutig sein. Treten zwei Werte mit der gleichen maximalen Häufigkeit auf, nennt man die Verteilung **bimodal**, bei mehr als zwei **multimodal**.
- **Robustheit:** Er ist absolut unempfindlich gegenüber Ausreißern.

### Berechnung

In einer Urliste oder Häufigkeitstabelle sucht man einfach den Wert $a_i$ mit der maximalen absoluten Häufigkeit $n_i$ (oder relativen Häufigkeit $r_i$).

$$x_{mod} = \{x_i \mid n_i = \max(n_1, \dots, n_k)\}$$

### Einsatz im Kontext

- **Nominal:** "Welches ist die meistverkaufte Automarke?" (Hier gibt es keine Alternative zum Modus).
- **Metrisch:** Bei stark asymmetrischen Verteilungen (z. B. Einkommen) liegt der Modus oft weit weg vom Mittelwert und zeigt, wo die "Masse" der Menschen tatsächlich liegt.

---

### Flashcards

Warum ist der Modus das einzige Lagemaß für nominalskalierte Merkmale?::Da nominale Daten keine natürliche Rangfolge (für den Median) und keine numerische Verrechenbarkeit (für das Mittel) besitzen, bleibt nur die Häufigkeit der Ausprägungen als Kriterium.

Was bedeutet es für eine Verteilung, wenn sie als "bimodal" bezeichnet wird?::Es existieren zwei voneinander getrennte Merkmalsausprägungen, die beide die gleiche maximale Häufigkeit aufweisen (zwei "Gipfel").

Wann ist die Angabe des Modus bei metrischen Daten irreführend?
?
Wenn die Daten sehr breit gestreut sind und der häufigste Wert nur geringfügig öfter vorkommt als andere, oder wenn die Daten stetig sind und jeder Wert nur genau einmal vorkommt (hier ist eine Klassierung zwingend erforderlich).


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Modus]]
SORT file.mtime DESC
```