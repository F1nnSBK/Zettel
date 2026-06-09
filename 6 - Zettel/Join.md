#Note

2026-06-09

Tags: [[Relationenalgebra]], [[Relationale Datenbank]], [[Kartesisches Produkt]], [[Relationenorientierte Operatoren]], [[Datenbankentwurf]], [[Normalisierung]], [[Relationenmodell]], [[Datenintegrität]], [[Attribut]]
#datenbanken 

---
Ein **Join (Verbund)** verknüpft zwei Relationen (Tabellen) über eine definierte Verbundbedingung (das Join-Prädikat). Während man in alten SQL-Versionen Joins umständlich in der `WHERE`-Klausel definierte (was Filter- und Verknüpfungslogik furchtbar vermischte), nutzt man seit dem SQL-92 Standard die explizite `JOIN ... ON`-Syntax.

Um Verwechslungen zu vermeiden (z.B. wenn beide Tabellen eine Spalte namens `customer_id` haben), arbeitet man bei Joins exzessiv mit **[[Alias]]en** (Abkürzungen wie `customer AS c`).

Die 5 wichtigsten Join-Arten (mit Beispielen)

1. INNER JOIN (Der Standard)

Liefert **nur die Schnittmenge**. Es werden nur die Datensätze zurückgegeben, bei denen es in _beiden_ Tabellen exakt passende Werte gibt.

**Aufgabe:** Zeige Kunden und ihre passenden Bank-Accounts.

```sql
SELECT c.firstname, c.lastname, a.account_number 
FROM customer AS c
INNER JOIN account AS a 
  ON c.customer_id = a.customer_id;
```

_(Zeilen von Kunden ohne Account, oder Accounts ohne Kunde fallen komplett weg__.)_

2. LEFT / RIGHT OUTER JOIN (Die Toleranten)

Ein Outer Join nimmt den Inner Join und hängt zusätzlich die Datensätze der linken (LEFT) oder rechten (RIGHT) Tabelle an, **die keinen Partner gefunden haben**. Die leeren Stellen der fehlenden Partnertabelle werden mit `NULL` aufgefüllt.

**Aufgabe:** Zeige _alle_ Kunden, egal ob sie eine Rechnung haben oder nicht.

```sql
SELECT c.first_name, c.last_name, i.invoice_id 
FROM customer c
LEFT JOIN invoice i 
  ON c.customer_id = i.customer_id;
```

_(Kunden ohne Rechnung tauchen in der Liste auf, bei_ _invoice_id_ _steht dann einfach_ _NULL__.)_

Ein **FULL OUTER JOIN** ist schlicht die Kombination aus Left und Right Join.

3. SELF JOIN (Die Rekursion)

Hierbei wird eine Tabelle **mit sich selbst** verknüpft. Das ist zwingend nötig bei hierarchischen Daten (z.B. "Mitarbeiter und ihre Vorgesetzten", die beide in derselben Personen-Tabelle stehen). Hierbei _müssen_ Aliase vergeben werden, damit die Datenbank weiß, ob man gerade auf die Mitarbeiter-Kopie oder die Manager-Kopie zugreift.

**Aufgabe:** Welcher Mitarbeiter arbeitet unter welchem Manager?

```sql
SELECT m.Name AS Mitarbeiter, mgr.Name AS Manager 
FROM Mitarbeiter m
LEFT JOIN Mitarbeiter mgr 
  ON m.ManagerID = mgr.MitarbeiterID;
```

4. NON-EQUI JOIN (Vergleich ohne "=")

Die meisten Joins sind "Equi Joins" (sie verwenden das "=" Zeichen). Ein Non-Equi Join verknüpft Tabellen über andere Operatoren, meistens `BETWEEN`.

**Aufgabe:** In welche Gehaltsklasse (Gehaltsspanne) fällt ein Mitarbeiter?

```sql
SELECT m.Name, m.Gehalt, g.KlassenName
FROM Mitarbeiter m
JOIN Gehaltsspannen g 
  ON m.Gehalt BETWEEN g.MinGehalt AND g.MaxGehalt;
```

5. JOIN-Ketten (Mehr als 2 Tabellen)

Man kann Joins beliebig aneinanderreihen. Regel: Ein Join über n Tabellen erfordert immer mindestens n−1 JOIN-Bedingungen.

**Aufgabe:** Zeige den Tracknamen, das Album und den Künstler.

```sql
SELECT t.name, al.title, ar.name
FROM track AS t
JOIN album AS al  ON t.album_id = al.album_id
JOIN artist AS ar ON al.artist_id = ar.artist_id;
```

Die gefährlichste Join-Falle: Filterung im ON vs. WHERE

Gerade bei OUTER JOINS macht es einen gewaltigen Unterschied, wo man filtert:

- **Filterung im** **JOIN ON****:** Dies passiert _vor_ bzw. _während_ dem Join. Der LEFT JOIN bleibt erhalten, auch wenn die Bedingung nicht zutrifft.
- **Filterung im** **WHERE****:** Dies passiert _nachdem_ der Join gebaut wurde. Filtert man hier auf Felder der rechten Tabelle (z.B. `WHERE invoice_date > '2021-01-01'`), fliegen alle Kunden ohne Rechnung wieder aus dem Resultat, weil bei ihnen `NULL` stand. **Aus dem LEFT JOIN wird effektiv unbeabsichtigt wieder ein INNER JOIN!**.

--------------------------------------------------------------------------------

### Flashcards

Was ist der mathematische Unterschied zwischen einem JOIN und einer Mengenoperation (UNION)?::Ein JOIN verknüpft Tabellen **horizontal** (Spalten werden nebeneinandergelegt). Eine Mengenoperation verknüpft Tabellen **vertikal** (Zeilen werden untereinandergelegt).

Welches Ergebnis liefert ein INNER JOIN zwischen zwei Tabellen?::Er liefert nur die Schnittmenge, also exakt die Datensätze, bei denen es in beiden Tabellen passende Werte gemäß der ON-Bedingung gibt.

Was ist der Hauptunterschied zwischen einem INNER JOIN und einem LEFT OUTER JOIN?
?
Ein LEFT OUTER JOIN gibt _alle_ Zeilen der linken Tabelle zurück, auch wenn es in der rechten Tabelle keinen passenden Partner gibt. Beim INNER JOIN würden diese partnerlosen Zeilen einfach wegfallen.

In welchem Szenario nutzt man einen SELF JOIN? Nenne ein Beispiel.
?
Wenn eine Tabelle eine rekursive Beziehung zu sich selbst besitzt, um Hierarchien abzubilden. Beispiel: Die Zuordnung von Mitarbeitern zu ihren Managern (Vorgesetzten), wenn beide in derselben "Mitarbeiter"-Tabelle gespeichert sind.

Warum sollte man den SQL-Befehl `NATURAL JOIN` in der Praxis niemals verwenden?::Er ist intransparent und fehleranfällig, da er völlig blind und vollautomatisch Tabellen über gleichnamige Spalten verknüpft, was bei späteren Schema-Anpassungen zu katastrophalen Fehlern führen kann.

Was passiert bei einem LEFT OUTER JOIN, wenn man in der WHERE-Klausel eine Filterbedingung (z.B. `< 2022`) auf ein Feld der angebundenen rechten Tabelle setzt?::Die Bedingung filtert das Ergebnis _nachträglich_. Dadurch werden alle Zeilen eliminiert, die auf der rechten Seite `NULL` waren (also keinen Partner hatten). Der LEFT OUTER JOIN wird dadurch effektiv zu einem reinen INNER JOIN degradiert.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Join]]
SORT file.mtime DESC
```