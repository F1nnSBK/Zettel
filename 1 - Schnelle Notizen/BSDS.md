#bsds 


1:
Nennen Sie die 4 zu modellierenden Sichten!
?
1. **Datensicht** (Welche Informationen?)
2. **Funktionssicht** (Was wird getan?)
3. **Organisationssicht** (Wer tut es?)
4. **Steuerungssicht** (Verbindung der anderen Sichten, zeitlicher/logischer Ablauf)
<!--SR:!2025-12-21,1,230-->

Erläutern Sie den Begriff der Semantischen Lücke :: Die „Semantische Lücke“ bezeichnet die Diskrepanz und das Verständigungsproblem zwischen der **natursprachlichen Anforderung** (Sicht des Anwenders/Fachseite) und der **formalen Spezifikation/technischen Umsetzung** (Sicht des Entwicklers/Maschine).
<!--SR:!2025-12-21,1,230-->

Nennen + erläutern Sie 2 Gründe für das Scheitern von FISCUS
?
1. **Komplexität durch Föderalismus:** Der Versuch, die unterschiedlichen Steuersysteme und Prozesse von 16 Bundesländern und dem Bund unter einen Hut zu bringen, scheiterte an partikularen Interessen und heterogenen Altsystemen.
2. **„Big Bang“-Ansatz:** Statt kleiner, beherrschbarer Schritte wurde ein riesiges Gesamtsystem geplant, was zu Unmanagbarkeit und Kostenexplosion führte.
<!--SR:!2025-12-21,1,230-->

Grenzen Sie Prinzipien von Methoden ab! :: **Prinzipien** sind grundlegende Gesetzmäßigkeiten, Regeln oder Leitlinien („Was“ und „Warum“), die meist dauerhaft gültig sind. **Methoden** sind konkrete Verfahren, Handlungsanweisungen oder Techniken („Wie“), um Aufgaben zu lösen; sie operationalisieren die Prinzipien.
<!--SR:!2025-12-21,1,230-->

Nennen Sie 3 Merkmale des Wasserfallmodells!
?
1. **Sequenzielle Phasen:** Strenge Abfolge (z. B. Analyse -> Design -> Imp -> Test).
2. **Dokumentengetrieben:** Jede Phase muss vollständig abgeschlossen und dokumentiert sein (Meilensteine), bevor die nächste beginnt.
3. **Späte Risikoprüfung:** Funktionale Tests finden erst ganz am Ende statt; Rücksprünge sind schwierig und teuer.
<!--SR:!2025-12-21,1,230-->

Definieren Sie den Begriff der SW-Technik (Software Engineering) :: Software Engineering ist die zielorientierte Bereitstellung und Anwendung von **Prinzipien, Methoden und Werkzeugen** für die arbeitsteilige, **ingenieurmäßige** Entwicklung, den Betrieb und die Wartung von (umfangreichen) Softwaresystemen.
<!--SR:!2025-12-21,1,230-->

Erläutern Sie das Magische Dreieck!
?
Das Magische Dreieck beschreibt die **Zielkonkurrenz** im Projektmanagement zwischen drei Parametern:
1. **Zeit** (Termine)
2. **Kosten** (Budget/Ressourcen)
3. **Qualität/Leistung** (Scope)
Eine Änderung an einer Ecke (z. B. Budgetkürzung) hat zwangsläufig negative Auswirkungen auf die anderen Ecken (z. B. weniger Qualität oder längere Dauer).
<!--SR:!2025-12-21,1,230-->

Worin unterscheiden sich das evolutionäre und das inkrementelle Prozessmodell? :: **Inkrementell:** Das System wird in _abgeschlossenen Teilen_ (Inkrementen) stückweise erweitert („Anbau-Prinzip“). Die Anforderungen sind weitgehend bekannt. **Evolutionär:** Das System entwickelt sich durch _Versuch, Irrtum und Feedback_ weiter. Anforderungen sind anfangs unklar; man arbeitet oft mit Prototypen, die verfeinert oder verworfen werden („Reifungs-Prinzip“).
<!--SR:!2025-12-21,1,230-->

---

2:
Erläutern Sie, was vertikale und horizontale Prototypen sind
?
**Horizontaler Prototyp:** Realisiert eine einzelne Schicht (meist die Benutzerschnittstelle) sehr breit, aber ohne tiefe Funktionalität. ("Fassade", gut für UI-Tests).
**Vertikaler Prototyp:** Realisiert einen ausgewählten funktionalen Ausschnitt durch alle Schichten hindurch (UI bis Datenbank). ("Durchstich", gut für Machbarkeitsstudien).
<!--SR:!2025-12-21,1,230-->

Warum wird die klassische SE als „schwergewichtig“ bezeichnet?
?
1. **Dokumentenlastigkeit:** Hoher Aufwand für Erstellung und Pflege umfangreicher Dokumente.
2. **Starrheit:** Strenge Phasenabfolgen und hoher Planungsaufwand machen Änderungen teuer und langsam.
3. **Bürokratie:** Viele formale Prozesse und Genehmigungen (z. B. bei Change Requests).
<!--SR:!2025-12-21,1,230-->

Erläutern Sie die analytische und die konstruktive QS!
?
**Konstruktive QS:** Maßnahmen zur *Fehlervermeidung*, die *während* der Erstellung wirken (z. B. Richtlinien, Checklisten, Methodenwahl, Pair Programming).
**Analytische QS:** Maßnahmen zur *Fehlerfindung*, die *nach* der Erstellung (oder eines Teils) wirken (z. B. Tests, Reviews, statische Codeanalyse).
<!--SR:!2025-12-21,1,230-->

Erläutern Sie das Agile Manifest
?
Das Agile Manifest basiert auf 4 Leitsätzen, die eine Wertverschiebung ausdrücken (links wichtiger als rechts):
1. **Individuen und Interaktionen** mehr als Prozesse und Werkzeuge.
2. **Funktionierende Software** mehr als umfassende Dokumentation.
3. **Zusammenarbeit mit dem Kunden** mehr als Vertragsverhandlung.
4. **Reagieren auf Veränderung** mehr als das Befolgen eines Plans.
<!--SR:!2025-12-21,1,230-->

Nennen Sie die 5 von uns betrachteten Prozessmodelle und worauf sie jeweils ihren Fokus haben
?
1. **Wasserfallmodell:** Fokus auf Planung und klare Phasenabgrenzung.
2. **V-Modell:** Fokus auf Qualitätssicherung (Verifikation & Validierung).
3. **Inkrementelles Modell:** Fokus auf frühe Nutzbarkeit durch Auslieferung in Teilen (Wachstum).
4. **Evolutionäres Modell:** Fokus auf Risikominimierung und Anforderungsklärung durch Versuche (Reifung).
5. **Agile Modelle (z. B. Scrum):** Fokus auf Flexibilität und Kundenwert durch Iterationen.
<!--SR:!2025-12-21,1,230-->

Nennen Sie 3 Prinzipien der Agilen SE
?
(Auswahl möglicher Prinzipien):
1. **Timeboxing:** Feste Zeitrahmen für Iterationen (Sprints).
2. **Selbstorganisation:** Teams entscheiden eigenverantwortlich, wie sie Aufgaben lösen.
3. **Kundenzentrierung:** Kontinuierliches Feedback und Einbindung des Kunden.
4. **Iterativ-inkrementelles Vorgehen:** Schrittweise Entwicklung in kurzen Zyklen.
<!--SR:!2025-12-21,1,230-->

Erläutern Sie das klassische V-Modell
?
Das V-Modell erweitert das Wasserfallmodell um explizite Maßnahmen der Qualitätssicherung.
* Die linke Seite des „V“ zeigt die **Spezifikations- und Entwurfsphasen** (vom Groben zum Detail).
* Die rechte Seite zeigt die korrespondierenden **Testphasen** (vom Unit-Test bis zum Abnahmetest).
* Jede Entwurfsstufe hat eine direkt zugeordnete Teststufe (Verifikation/Validierung).
<!--SR:!2025-12-21,1,230-->

Nennen + erläutern Sie die 3 Arten von Prototypen
?
1. **Explorativer Prototyp:** Dient zur Klärung unklarer Anforderungen (Wegwerf-Prototyp).
2. **Experimenteller Prototyp:** Dient zur Überprüfung der technischen Machbarkeit oder Architektur (Wegwerf-Prototyp).
3. **Evolutionärer Prototyp:** Wird schrittweise zum fertigen System weiterentwickelt (Kein Wegwerf-Produkt).
<!--SR:!2025-12-21,1,230-->

---

3 == 2

---

4:
Nennen + erläutern Sie "Brook's Law"
?
**"Adding manpower to a late software project makes it later."** (Fred Brooks) Das Hinzufügen von Personal zu einem bereits verspäteten Projekt führt zu noch mehr Verzögerung. **Gründe:**
1. **Einarbeitungsaufwand:** Neue Mitarbeiter müssen von den produktiven Mitarbeitern eingearbeitet werden, was deren Produktivität vorübergehend senkt ("Ramp-up").
2. **Kommunikationsaufwand:** Der Koordinationsbedarf steigt mit jedem neuen Teammitglied nicht linear, sondern kombinatorisch (n*(n-1)/2 Beziehungen), was die Komplexität erhöht.
<!--SR:!2025-12-21,1,230-->

---

5:
Was ist ein Area Product Owner?
?
Eine Rolle im Skalierungsframework **LeSS Huge** (Large-Scale Scrum Huge).
Da ein einzelner Product Owner bei sehr vielen Teams (über 8) überlastet wäre, wird das Produkt in Anforderungsbereiche (Requirement Areas) unterteilt.
Der **Area Product Owner** ist für das Backlog und die Priorisierung innerhalb eines solchen Bereichs zuständig und arbeitet mit dem übergeordneten (Main) Product Owner zusammen.
<!--SR:!2025-12-21,1,230-->

Für wieviele Teams sind LeSS und LeSS Huge gedacht? :: **LeSS:** Bis zu 8 Teams (ca. 50 Personen). **LeSS Huge:** Ab 8 Teams (bis zu einigen tausend Personen).
<!--SR:!2025-12-21,1,230-->

Wofür steht INVEST?
?
Ein Akronym für Qualitätskriterien von User Stories (nach Bill Wake):
* **I**ndependent (Unabhängig)
* **N**egotiable (Verhandelbar)
* **V**aluable (Werthaltig für den Kunden)
* **E**stimable (Schätzbar)
* **S**mall (Klein genug für einen Sprint)
* **T**estable (Testbar / Akzeptanzkriterien vorhanden)
<!--SR:!2025-12-21,1,230-->

Erläutern Sie das Spotify-Modell
?
Ein Organisationsmodell zur Skalierung von Agilität (ursprünglich von Spotify), das auf Autonomie und Alignment setzt.
Wichtige Elemente:
* **Squads:** Kleine, autonome, cross-funktionale Teams (wie Scrum Teams).
* **Tribes:** Zusammenfassung mehrerer Squads, die an einem ähnlichen Geschäftsbereich arbeiten.
* **Chapters:** Fachliche Gruppen innerhalb eines Tribes (z. B. alle Frontend-Entwickler), geführt vom Chapter Lead (Personalverantwortung).
* **Guilds:** Freiwillige Interessensgemeinschaften über das gesamte Unternehmen hinweg (Wissensaustausch).
<!--SR:!2025-12-21,1,230-->

Welcher Art von QS ist die Sprint Retrospective zuordenbar? :: Sie zählt zur **konstruktiven Qualitätssicherung**. Da hier der Arbeitsprozess und die Zusammenarbeit verbessert werden, um zukünftige Fehler zu vermeiden (Fehlerprävention), wirkt sie prozessverbessernd und nicht produktprüfend (analytisch).
<!--SR:!2025-12-21,1,230-->

Erläutern Sie den Begriff DoR oder DoD
?
**DoD (Definition of Done):** Eine Checkliste von Kriterien, die ein Inkrement erfüllen muss, um als "fertig" und potenziell auslieferbar zu gelten (z. B. "Code gecheckt", "Tests grün", "Doku aktualisiert"). Sichert die Qualität am Sprint-Ende.
**DoR (Definition of Ready):** Kriterien, die eine User Story erfüllen muss, *bevor* sie in den Sprint aufgenommen werden darf (z. B. "INVEST erfüllt", "UI-Entwürfe da"). Sichert die Planbarkeit zu Sprint-Beginn.
<!--SR:!2025-12-21,1,230-->

Ist das Scrum-Modell ein evolutionäres oder ein inkrementelles Prozessmodell? :: Es ist ein **iterativ-inkrementelles** Prozessmodell. Es ist **inkrementell**, weil am Ende jedes Zyklus ein nutzbares Produktteil (Inkrement) steht. Es ist **evolutionär (iterativ)**, weil Anforderungen und Lösungen schrittweise verfeinert werden und sich das System durch Feedback weiterentwickelt.
<!--SR:!2025-12-21,1,230-->

Was ist/sind die Aufgabe eines Scrum Masters?
?
Der Scrum Master ist ein **Servant Leader** für das Team und die Organisation.
Seine Aufgaben sind:
1. **Beseitigung von Hindernissen** (Impediments), die das Team stören.
2. **Moderation** der Scrum Events (sofern gewünscht/nötig).
3. **Coaching** des Teams, des PO und der Organisation in Selbstorganisation und agilem Mindset.
4. **Schutz** des Teams vor unberechtigten Eingriffen von außen.
5. Sicherstellen, dass der **Scrum-Prozess** verstanden und eingehalten wird.
<!--SR:!2025-12-21,1,230-->

---

6:
Nennen Sie die 3 Einflussfaktoren auf die Wahl der richtigen Erhebungstechnik
?
1. **Faktor Mensch / Quelle:** Verfügbarkeit, Motivation und Artikulationsfähigkeit der Stakeholder.
2. **Faktor Wissen:** Art des Wissens (bewusst/explizit vs. unbewusst/implizit).
3. **Faktor Rahmenbedingungen:** Zeit, Budget und verfügbare Hilfsmittel im Projekt.
<!--SR:!2025-12-21,1,230-->

Welche Arten von Ereignissen gibt es?
?
(Meist im Kontext von Zustandsdiagrammen oder Prozessmodellen):
1. **Zeitereignis:** Ein bestimmter Zeitpunkt oder Ablauf einer Frist (z. B. "Jeden Montag", "nach 10 Min").
2. **Externes Ereignis (Signal):** Ein Anstoß von außen durch einen Akteur oder ein Nachbarsystem (z. B. "Button gedrückt", "Daten empfangen").
3. **Internes Ereignis (Zustandsänderung):** Eine Bedingung im System wird wahr (z. B. "Speicher voll", "Temperatur > 50°C").
<!--SR:!2025-12-21,1,230-->

Nennen und erläutern Sie 2 Dimensionen der Methodenauswahl „klassisch“ <-> „agil“
?
(Oft basierend auf dem "Home Ground"-Modell von Boehm/Turner):
1. **Dynamik der Anforderungen:** Stabil/Bekannt (-> Klassisch) vs. Volatil/Unbekannt (-> Agil).
2. **Kritikalität (Schadenshöhe):** High Safety/Life-Critical (-> Klassisch, da dokumentenlastig/sicher) vs. Low Criticality/Comfort (-> Agil).
3. **Teamgröße:** Großes Team (-> Klassisch) vs. Kleines Team (-> Agil).
<!--SR:!2025-12-21,1,230-->

Was bedeutet der Begriff der Essenz? :: **Essenz** bezeichnet den rein fachlichen Kern einer Anforderung (z. B. in einem Use Case), **völlig losgelöst von der technischen Realisierung** oder Oberflächen-Details. Es beschreibt das "Was" ohne das "Wie" (technologie-neutral).
<!--SR:!2025-12-21,1,230-->

Welche 3 Arten der Zerlegung kennen Sie?
?
1. **Funktionale Zerlegung:** Aufteilung nach Teilaufgaben/Funktionen (Prozessorientiert).
2. **Datenorientierte Zerlegung:** Aufteilung anhand der Datenstrukturen (z. B. Jackson-Diagramme).
3. **Objektorientierte Zerlegung:** Kapselung von Daten und Funktionen in Objekten/Klassen.
<!--SR:!2025-12-21,1,230-->

Ist das zu modellierende System ein Akteur im Use Case? Begründen Sie Ihre Antwort.
?
**Nein.**
**Begründung:** Ein Akteur ist immer eine Entität **außerhalb** der Systemgrenze, die mit dem System interagiert (Mensch oder Nachbarsystem). Das zu modellierende System ist der Gegenstand der Betrachtung (SuD – System under Design) und kann daher nicht sein eigener externer Benutzer sein.
<!--SR:!2025-12-21,1,230-->

Nennen Sie die Elemente der Use-Case-Schablone
?
(Typische Elemente nach Cockburn):
1. **Name/ID:** Eindeutige Bezeichnung.
2. **Kurzbeschreibung:** Ziel des Use Cases.
3. **Akteure:** Primäre und sekundäre Beteiligte.
4. **Vorbedingungen:** Was muss erfüllt sein, damit der UC starten kann?
5. **Nachbedingungen:** Zustand nach Erfolg (oder Misserfolg).
6. **Standardablauf (Main Flow):** Der "Happy Path" ohne Fehler.
7. **Alternativabläufe (Extensions):** Abweichungen, Fehlerfälle.
8. **Auslöser (Trigger):** Was startet den Use Case?
<!--SR:!2025-12-21,1,230-->


---

7:
Was fällt auf, wenn man die UC-Checklisten von Balzert und Cockburn vergleicht?
?
**Balzert:** Sehr umfangreich, formal, viele Attribute und Verwaltungsdaten ("Deutsch-gründlich"). Fokus auf Vollständigkeit und Dokumentation.
**Cockburn:** Pragmatischer, fokussiert auf den Textfluss und das Ziel ("Wurfweite"). Weniger Metadaten, mehr Fokus auf Verständlichkeit und Kommunikation.
<!--SR:!2025-12-21,1,230-->

Muss es eine Nachbedingung "Fehlschlag" in einem Use Case geben? Begründen Sie Ihre Antwort!
?
Es ist **empfehlenswert**, eine sogenannte **Minimalgarantie** (Minimal Guarantee) zu definieren. Diese beschreibt, in welchem Zustand sich das System befindet, wenn das Ziel *nicht* erreicht wurde (z. B. "Systemzustand unverändert", "Fehler protokolliert").
Zwingend ist sie formal **nicht**, wenn das System im Fehlerfall schlicht nichts ändert, aber sie schafft Sicherheit für die Entwickler.
<!--SR:!2025-12-21,1,230-->

Nennen Sie 3 Lessons Learned zu Use Cases
?
(Häufige Fehler, die vermieden werden sollen):
1. **Keine GUI-Details:** Beschreibe *was* getan wird, nicht *wie* (kein "Klicke Button X", sondern "Wählt Option").
2. **Kein "If-Then-Else" im Hauptablauf:** Verzweigungen gehören in die Alternativabläufe/Extensions, der Standardablauf bleibt linear ("Happy Path").
3. **System ist kein Akteur:** Das System handelt nicht mit sich selbst.
4. **Aktiv statt Passiv:** "Der Kunde gibt die Adresse ein" statt "Die Adresse wird eingegeben".
<!--SR:!2025-12-21,1,230-->

---

8:
Was ist eine User Story?
?
Eine kurze, einfache Beschreibung einer Anforderung aus der Perspektive des Endbenutzers/Kunden. Sie dient als "Versprechen für ein Gespräch" (Card, Conversation, Confirmation) und folgt meist dem Format: **"Als *Rolle* möchte ich *Ziel/Funktion*, um *Nutzen* zu erreichen."**
<!--SR:!2025-12-21,1,230-->

---

9:
Welche Beziehungsarten gibt es bei Use Cases und wofür werden sie eingesetzt?
?
1. **include (Einschluss):** Um wiederkehrende Abläufe, die an mehreren Stellen benötigt werden, in einen eigenen Use Case auszulagern (Vermeidung von Redundanz).
2. **extend (Erweiterung):** Um optionales Verhalten, Sonderfälle oder Fehlerbehandlung vom Hauptablauf zu trennen. Die Erweiterung wird nur ausgeführt, wenn eine bestimmte Bedingung (Extension Point) erfüllt ist.
3. **Generalisierung:** Vererbung zwischen Akteuren (z. B. "Admin" ist ein spezieller "User") oder seltener zwischen Use Cases.
<!--SR:!2025-12-21,1,230-->

Was modelliert ein Use-Case-Diagramm?
?
Es modelliert das **Systemverhalten aus Anwendersicht** (funktionale Anforderungen).
Es zeigt:
* Die **Systemgrenze** (Was gehört zum System, was nicht?).
* Die **Akteure** (Wer interagiert mit dem System?).
* Die **Anwendungsfälle** (Was leistet das System?).
* Die **Beziehungen** zwischen diesen Elementen.
* *Wichtig:* Es zeigt **keine** Abläufe oder Reihenfolgen!
<!--SR:!2025-12-21,1,230-->

Erläutern Sie die Teile einer Entscheidungstabelle
?
Eine Entscheidungstabelle ist meist in 4 Quadranten aufgeteilt:
1.  **Bedingungsanzeiger (oben links):** Auflistung aller relevanten Bedingungen (Inputs).
2.  **Aktionsanzeiger (unten links):** Auflistung aller möglichen Aktionen/Ergebnisse.
3.  **Bedingungseinträge (oben rechts):** Die verschiedenen Kombinationen der Bedingungen (Regeln), oft mit "J" (Ja), "N" (Nein) oder "-" (Egal) markiert.
4.  **Aktionseinträge (unten rechts):** Markierung (z. B. "X"), welche Aktion bei welcher Regel ausgeführt wird.
<!--SR:!2025-12-21,1,230-->

Was bedeutet "Konsolidierung" bei einer Entscheidungstabelle?
?
Das **Zusammenfassen von Regeln** (Spalten), die zur gleichen Aktion führen.
Dies ist möglich, wenn sich zwei Regeln nur in einer Bedingung unterscheiden, diese Bedingung aber keinen Einfluss auf das Ergebnis hat ("Don't Care" / "-"). Dies reduziert die Komplexität der Tabelle.
<!--SR:!2025-12-21,1,230-->

Wie sieht das Muster für eine Erweiterung bei einem Use Case aus?
?
Eine Erweiterung (Extension) beschreibt einen alternativen Pfad, der vom Hauptpfad abzweigt. Das Muster beinhaltet:
1.  **Auslöser/Bedingung:** Wann passiert es? (z. B. "User drückt 'Abbrechen'").
2.  **Extension Point:** Wo im Hauptablauf passiert es? (Referenz auf die Schrittnummer).
3.  **Ablauf:** Was passiert in der Erweiterung?
4.  **Abschluss:** Was passiert danach? (Rücksprung in den Hauptablauf oder Abbruch/Ende).
<!--SR:!2025-12-21,1,230-->

Nennen und erläutern Sie die Strukturelemente des Spotify-Modells
?
Das Modell organisiert skalierte Agilität durch eine Matrix-Struktur aus Autonomie und Alignment:
1.  **Squads:** Die kleinste Einheit (wie ein Scrum-Team). Cross-funktional, autonom, sitzen zusammen.
2.  **Tribes:** Eine Sammlung mehrerer Squads, die an einem verwandten Geschäftsbereich arbeiten (max. ca. 100 Personen).
3.  **Chapters:** Fachliche Gruppierungen *innerhalb* eines Tribes (z. B. alle Tester des Tribes). Dient dem fachlichen Austausch und der Personalentwicklung (Chapter Lead ist oft Disziplinarvorgesetzter).
4.  **Guilds:** Freiwillige Interessensgemeinschaften über das *gesamte* Unternehmen hinweg (z. B. "Java Guild", "Agile Coach Guild") zum breiten Wissensaustausch.
<!--SR:!2025-12-21,1,230-->

Nennen Sie 3 charakteristische Merkmale von LeSS (Large-Scale Scrum)
?
LeSS wendet Scrum auf mehrere Teams an, die gemeinsam an *einem* Produkt arbeiten:
1.  **Ein Product Owner & Ein Product Backlog:** Es gibt nur *einen* PO und *ein* Backlog für alle Teams (keine Team-Backlogs), um den Gesamtüberblick zu behalten.
2.  **Gemeinsamer Sprint:** Alle Teams arbeiten im gleichen Takt (synchronisierter Sprint-Start und -Ende).
3.  **Feature-Teams:** Teams sind nicht nach Komponenten (z. B. "Datenbank-Team"), sondern nach Features organisiert, um Kundenwert Ende-zu-Ende liefern zu können.
<!--SR:!2025-12-21,1,230-->


Nennen und unterscheiden Sie die zwei Hauptarten der Qualitätssicherung (QS)
?
1. **Konstruktive QS (Fehlervermeidung):**
   Maßnahmen, die *während* der Entwicklung wirken, damit Fehler gar nicht erst entstehen ("Quality by Design").
   *Beispiele:* Richtlinien, Coding Standards, Checklisten, Pair Programming, Wahl geeigneter Methoden/Werkzeuge.
2. **Analytische QS (Fehlerfindung):**
   Maßnahmen, die *nach* der Erstellung eines Artefakts (Code oder Dokument) wirken, um vorhandene Fehler zu entdecken.
   *Beispiele:* Softwaretests (Unit, Integration, System), Reviews, Walkthroughs, Statische Codeanalyse.
<!--SR:!2025-12-21,1,230-->