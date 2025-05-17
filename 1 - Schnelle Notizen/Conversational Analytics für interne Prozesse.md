### Projektidee: Conversational Analytics für interne Prozesse

**Titel der Arbeit:** Conversational Analytics für interne Prozesse - Ein natürlicher Sprachzugang zu Business-Daten

**Beschreibung:** Entwicklung eines KI-gestützten Systems, das es Mitarbeitenden ermöglicht, über natürliche Sprache mit internen Business-Daten zu interagieren, anstatt SQL-Abfragen oder Dashboards zu nutzen. Nutzer können einfache Fragen stellen und erhalten strukturierte oder visualisierte Antworten.

**Technologien & Tools:**

- OpenAI GPT-4/LangChain für Sprachverarbeitung
- SQLite oder BigQuery als Datenquelle
- FastAPI/Streamlit für UI
- SQL Parser, ggf. Dataframe-Auswertung mit Pandas

**Zielsetzung:**

- Entwicklung eines Chatbot-Prototyps mit natürlicher Sprachverarbeitung
- Anbindung an eine strukturierte Datenquelle
- Übersetzung natürlicher Sprache in strukturierte Abfragen
- Ausgabe strukturierter oder visualisierter Antworten
- Fokus auf Self-Service für Fachabteilungen ohne SQL-Wissen

**Business-Nutzen:** Kann langfristig als internes Analyse-Tool eingesetzt werden und die Hürde für datengetriebene Entscheidungen senken. Bietet hohes Automatisierungspotenzial in Kombination mit Reporting- oder CRM-Systemen.

**Bewertung:** Diese Projektidee wird als die potenziell aufwendigste der vier vorgestellten Projekte eingeschätzt. Die Hauptkomplexität liegt in der Entwicklung eines robusten Systems zur Verarbeitung natürlicher Sprache (NLP) und der genauen Übersetzung von Benutzerfragen in strukturierte Datenbankabfragen. Die Arbeit mit großen Sprachmodellen (wie GPT-4) und Frameworks wie LangChain erfordert ein tiefes Verständnis sowie die Bewältigung potenzieller Probleme wie "Halluzinationen" (falsche oder erfundene Antworten). Darüber hinaus erfordert die Anbindung an und Interaktion mit internen Datenquellen sowie die Entwicklung einer benutzerfreundlichen Oberfläche erheblichen Aufwand. Dies macht das Projekt technisch anspruchsvoll und zeitintensiv.