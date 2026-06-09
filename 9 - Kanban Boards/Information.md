#Note

2026-06-09

Tags: [[Datenbanken]], [[Grundlagen]], [[Datenmodellierung]]
#datenbanken

---
**Informationen** sind Daten, die interpretiert und in einen fachlichen oder semantischen Kontext gesetzt wurden. Während Daten lediglich darstellbare Repräsentationen von Fakten sind (z. B. die isolierte Zahl "37"), liefert erst die Information den entscheidenden Bedeutungskontext (z. B. "37 °C Temperatur").

Die 7 immateriellen Eigenschaften von Information

Im Gegensatz zu materiellen Wirtschaftsgütern weist Information laut Skript spezifische Charakteristika auf:

1. **Darstellung:** Information wird stets durch zugrundeliegende Daten spezifiziert (Daten fungieren als Trägermedium).
2. **Verarbeitung:** Information kann durch Algorithmen in Datenbanksystemen übermittelt, gespeichert, klassifiziert und transformiert werden.
3. **Kombination:** Information ist beliebig kombinierbar, was Manipulationen jederzeit möglich macht. Die Herkunft einzelner Teile ist oft schwer nachweisbar.
4. **Alterung:** Information unterliegt keinem physikalischen Alterungsprozess (Verschleiß).
5. **Originalität:** Information ist verlustfrei und beliebig kopierbar. Das Konzept eines "Originals" existiert hier nicht.
6. **Vagheit:** Information kann unpräzise sein und besitzt je nach Anwendung eine unterschiedliche Qualität oder Aussagekraft.
7. **Trägerunabhängigkeit:** Information erfordert keinen fixierten, materiellen Träger und ist somit ortsunabhängig.

Abgrenzung: Daten vs. Information vs. Wissen

Das Verständnis der Transformation von Daten zu Wissen ist die Basis für jedes Datenbanksystem:

|Ebene|Definition|Beispiel|
|---|---|---|
|**Daten**|Rohwerte, Zeichen oder Messungen ohne eigenen Kontext.|"37"|
|**Information**|Daten, die interpretiert und in einen Kontext gesetzt wurden.|"37 °C Temperatur"|
|**Wissen**|Vernetzte Informationen, die mit Erfahrung verknüpft für Entscheidungen genutzt werden.|"Bei 37 °C muss der Server gekühlt werden."|

--------------------------------------------------------------------------------

Flashcards

Was ist der grundlegende Unterschied zwischen Daten und Informationen?::Daten sind uninterpretierte Rohwerte, während Informationen Daten sind, die in einen semantischen Kontext gesetzt und interpretiert wurden.

Besitzt Information ein "Original" oder kann sie physisch altern?::Nein, Information ist beliebig kopierbar (kennt keine Originale) und unterliegt keinem physikalischen Alterungsprozess.

Wie verhalten sich Daten, Information und Wissen in der Prozesskette?
?
Aus isolierten Rohwerten (Daten, z. B. "37") wird durch Kontextualisierung Information ("37 °C Temperatur"). Durch die erfahrungsbasierte Vernetzung dieser Information entsteht handlungsrelevantes Wissen ("Bei 37 °C muss der Server gekühlt werden").

Nenne mindestens vier spezifische Eigenschaften von Information, die sie von materiellen Gütern unterscheiden.
?
1. Beliebig kopierbar (kein Original).
2. Kein physikalischer Alterungsprozess.
3. Trägerunabhängig / ortsunabhängig.
4. Beliebig kombinier- und manipulierbar.
5. Besitzt oft Vagheit (unterschiedliche Aussagekraft/Präzision).

--------------------------------------------------------------------------------

Verwendung

```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Informationen]]
SORT file.mtime DESC
```
