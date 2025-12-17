#Note

2025-12-17

Tags: [[Software Engineering]], [[Prozessmodelle]]
#se

---
- **Wasserfallmodell:**
    - Klassisches, dokumentengetriebenes Modell, bei dem Phasen (Anforderung, Analyse, Entwurf, Codierung, Test, Betrieb) streng sequenziell durchlaufen werden.
    
    - **Vorteile:** Einfach, verständlich, gut plan- und steuerbar (hohe Management-Sicht).
    - **Nachteile:** Starr, späte Fehlererkennung ("Big Bang" am Ende), keine Rücksprünge vorgesehen, Gefahr der "Dokumentenfriedhöfe".
        
- **V-Modell (Klassisch & XT):**
    - Erweiterung des Wasserfallmodells. Die linke Seite des V stellt die Spezifikationsphasen (Analyse/Entwurf) dar, die rechte Seite die entsprechenden Testphasen (Integration/Abnahme).
    - Jede Entwurfsphase hat eine korrespondierende Testphase (z.B. Grobentwurf $\leftrightarrow$ Systemtest).
        
- **Verifikation vs. Validation:**
    - **Verifikation:** "Wird das Produkt _richtig_ gebaut?" – Überprüfung der formalen Korrektheit und Konsistenz (z.B. entspricht der Code dem Entwurf?).
    - **Validation:** "Wird das _richtige_ Produkt gebaut?" – Überprüfung aus Anwendersicht, ob das System die tatsächlichen Anforderungen erfüllt (z.B. durch Prototypen).
        
- **QS-Maßnahmen:**
    - **Analytische QS (Produktqualität):** Fehlersuche im fertigen Produkt/Dokument. Beispiele: Tests (dynamisch), Reviews, Inspektionen, Walkthroughs (statisch).
        
    - **Konstruktive QS (Prozessqualität):** Fehlervermeidung durch vorbeugende Maßnahmen. Beispiele: Einsatz von Methoden, Standards, Richtlinien, Checklisten, Werkzeugen.

---
#### Flashcards

Was ist das Hauptmerkmal des Wasserfallmodells? :: Es ist ein sequenzielles, dokumentengetriebenes Modell, bei dem jede Phase abgeschlossen sein muss, bevor die nächste beginnt.

Was ist der Unterschied zwischen Verifikation und Validation? :: Verifikation prüft die formale Korrektheit ("Produkt richtig gebaut?"), Validation prüft die Eignung für den Anwender ("Richtige Produkt gebaut?").

Welche zwei Arten von QS-Maßnahmen gibt es? :: Analytische QS (Fehlersuche, z.B. Tests) und Konstruktive QS (Fehlervermeidung, z.B. Richtlinien).

Wie erweitert das V-Modell das Wasserfallmodell? :: Es stellt jedem Entwurfsschritt auf der linken Seite eine entsprechende Teststufe auf der rechten Seite gegenüber.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Squenzielle Prozessmodelle]]
SORT file.mtime DESC
```