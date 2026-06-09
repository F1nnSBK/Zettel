#Note

2026-06-09

Tags: [[Wissen]], [[Information]], [[Daten]], [[Datenbanksystem]]
#datenbanken

---
Von **Wissen** spricht man im Kontext der Datenmodellierung, wenn Informationen individuell verarbeitet und sinnvoll miteinander vernetzt werden. Dabei erhalten die Informationen einen mehr oder weniger starken Bezug zur eigenen Erfahrungswelt des Anwenders oder Systems.

Während _Informationen_ lediglich Daten mit einem semantischen Kontext sind, entsteht _Wissen_ erst dann, wenn diese Informationen mit Erfahrungen in Beziehung gesetzt und für konkrete Entscheidungen genutzt werden können.

#### Abgrenzung anhand der DIW-Pyramide

Der Unterschied zeigt sich am besten in der schrittweisen Transformation von rohen Fakten zu handlungsrelevantem Wissen:

| Ebene               | Definition                                                            | Beispiel 1 (Technisch)                      | Beispiel 2 (Alltag)                                          |
| ------------------- | --------------------------------------------------------------------- | ------------------------------------------- | ------------------------------------------------------------ |
| **[[Daten]]**       | Isolierte, uninterpretierte Fakten ohne Kontext.                      | "37"                                        | "Meier, Hauptstraße 12, Tübingen"                            |
| **[[Information]]** | Verknüpfte und mit semantischer Bedeutung versehene Daten.            | "37 °C Temperatur"                          | "Herr Meier wohnt in der Hauptstraße 12 in Tübingen."        |
| **[[Wissen]]**      | Vernetzte Informationen mit Erfahrungsbezug zur Entscheidungsfindung. | "Bei 37 °C muss der Server gekühlt werden." | "Mein ehemaliger Schulfreund Peter Meier wohnt auch hier..." |

#### Bedeutung für Datenbanksysteme

Klassische Relationale Datenbanken speichern auf physischer Ebene primär reine _Daten_. Durch das relationale Schema, Fremdschlüssel und SQL-Abfragen werden diese zu nutzbaren _Informationen_ aggregiert. Die Ableitung von _Wissen_ passierte historisch fast ausschließlich in der Anwendungsschicht (Business Logic) oder im Kopf des Nutzers.

Moderne Ansätze, wie etwa **Graphdatenbanken (Neo4j)**, versuchen zunehmend, dieses "Wissen" durch die physische Persistierung komplexer Beziehungen direkt im Datenmodell abzubilden (sog. _Knowledge Graphs_).

--------------------------------------------------------------------------------

### Flashcards

Was ist die formale Definition von Wissen im Datenbankkontext?::Wissen ist die sinnvolle Verknüpfung von Informationen zueinander und deren In-Beziehung-Setzung zu individuellen Erfahrungen.

Wie grenzt sich Wissen von Information ab?
?
Information entsteht durch die semantische Einbettung von Daten (z.B. "37 °C"). Wissen entsteht erst, wenn diese Information mit Erfahrungswerten vernetzt wird, um handlungsrelevant zu sein (z.B. "Bei 37 °C muss die Serverkühlung aktiviert werden").

Welche drei Stufen durchlaufen Fakten in der klassischen Theorie der Informationsverarbeitung?::Daten → Information → Wissen.

Warum tun sich klassische relationale Datenbanken schwer damit, "Wissen" abzubilden?
?
Weil relationales Design auf strikter Objektivität, Faktenisolierung (Normalisierung) und flachen Tabellen basiert. Wissen erfordert jedoch tiefe Vernetzung und subjektive Erfahrungsbezüge, weshalb es historisch oft in die Applikationsschicht ausgelagert wurde oder heute durch Graphdatenbanken gelöst wird.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Wissen]]
SORT file.mtime DESC
```