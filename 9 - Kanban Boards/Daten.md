#Note

2026-06-09

Tags: [[Datenbanken]], [[Grundlagen]], [[Datenmodellierung]]
 #datenbanken

---
**Daten** sind isolierte, uninterpretierte Fakten und maschinell verarbeitbare Repräsentationen von Ereignissen oder Konzepten in formalisierter Form (z. B. als Zahlen, Texte, Symbole). Sie besitzen von sich aus keine eigene Semantik und erhalten erst durch einen spezifischen fachlichen Kontext eine Bedeutung. Ein klassisches Beispiel ist die isolierte Zahl "37" oder "42".

Die 5 Kerneigenschaften von Daten

Damit Fakten als Daten in einem System maschinell genutzt werden können, weisen sie folgende Kerneigenschaften auf:

|Eigenschaft|Beschreibung|Beispiel|
|---|---|---|
|**Rohcharakter**|Sie existieren zunächst als reine, uninterpretierte Fakten.|„42“|
|**Objektivität**|Sie sind völlig unabhängig von ihrer späteren Bedeutung.|„2025-08-27“|
|**Speicherbarkeit**|Sie können analog (Papier) oder digital erfasst werden.|Datenbankeintrag|
|**Verarbeitbarkeit**|Sie lassen sich automatisiert von Maschinen verarbeiten.|SQL-Abfrage, Excel|
|**Kontextabhängigkeit**|Erst der Zusammenhang entscheidet über die Nutzbarkeit.|Ist „42“ ein Alter oder eine Temperatur?|

Strukturierungsgrade von Daten

Die Effizienz der Speicherung und Auswertbarkeit von Daten in Datenbanksystemen hängt massiv von ihrem logischen Strukturierungsgrad ab. Diese Klassifizierung ist besonders für die Unterscheidung von Relationalen vs. NoSQL Datenbanken zentral:

- **Strukturierte Daten:** Liegen in einem explizit vorab definierten Schema (Strukturinformation) vor (z. B. Excel-Tabellen, Kundendatenbanken). Sie bilden die Basis für klassische _Relationale Datenbanken_.
- **Halbstrukturierte Daten:** Sind nicht streng typisiert, besitzen aber eine inhärente, erkennbare Struktur, die sie selbst mitbringen (oft baumartig verschachtelt, z. B. XML, JSON). Sie sind die Domäne der _Dokumentendatenbanken (NoSQL)_.
- **Unstrukturierte Daten:** Folgen überhaupt keinem definierten Schema; sie existieren als reine Bitfolge (z. B. Bilder, Videos, E-Mails).

**Hinweis für Big Data:** Die massive Zunahme von unstrukturierten und halbstrukturierten Daten ("Variety" aus den 6 V's) sowie schiere Datenmengen ("Volume") machen Daten heute mit herkömmlichen Werkzeugen oft nicht mehr beherrschbar. Dies erzwang den Paradigmenwechsel hin zu NoSQL-Datenbanken.

Code-Implementation

```
// Beispiel für halbstrukturierte Daten (JSON Format).
// Die Struktur ist direkt in den Daten selbst gekapselt (Key-Value), ohne dass vorab ein fixes Tabellenschema erzwungen wird (Schemafreiheit).
{
  "ID": 1,
  "Vorname": "Tom",
  "E-Mail": "tom@example.com",
  "Vorlieben": ["Mode", "Spass", "Einkaufen"]
}
```

--------------------------------------------------------------------------------

### Flashcards

Was sind Daten im datenbanktheoretischen Sinn?::Isolierte, darstellbare und maschinell verarbeitbare Repräsentationen von Fakten ohne eigenen Kontext.

Welche 5 Kerneigenschaften charakterisieren Daten?::Rohcharakter, Objektivität, Speicherbarkeit, Verarbeitbarkeit, Kontextabhängigkeit.

Wie unterscheiden sich strukturierte von halbstrukturierten Daten?
?
**Strukturierte Daten** haben ein vorab explizit definiertes, fixes Schema (z. B. relationale Tabellenspalten). **Halbstrukturierte Daten** sind nicht streng typisiert, bringen ihre logische Struktur aber selbst mit (z. B. durch baumartig verschachtelte JSON-Dokumente).

Welche Rolle spielen unstrukturierte und halbstrukturierte Daten im Kontext von NoSQL und Big Data?
?
Da unstrukturierte Daten keinem Schema folgen und halbstrukturierte Daten flexible Strukturen aufweisen (Merkmal "Variety" der 6 V's), können sie oft schwer oder gar nicht in starren relationalen Datenbanken verarbeitet werden. Dies führte zur Entwicklung von NoSQL-Datenbanken (z.B. Dokumentendatenbanken).


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Daten]]
SORT file.mtime DESC
```