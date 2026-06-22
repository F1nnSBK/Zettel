#Note

2026-06-22

Tags: [[Cyber-Security]], [[IT-Sicherheit]], [[Software-Engineering]], [[Grundlagen]]
#it_security

---

### Softwarequalitäten im Kontext der IT-Sicherheit

Aus Sicht der Cyber-Security lässt sich Software anhand zweier Dimensionen klassifizieren: **Qualität** (Gut vs. Schlecht) und **Absicht** (Gutartig vs. Bösartig).

```
                 Absicht: Gutartig (Benign)  │  Absicht: Bösartig (Malicious)
                                             │
Qualität: Gut    Zuverlässige, sichere       │  Hocheffiziente, getarnte
                 Standard-Software           │  Schadsoftware (z. B. APT-Trojaner)
─────────────────────────────────────────────┼──────────────────────────────────────
Qualität:        Fehlerhafte Software (Bugs, │  Schlecht programmierte Malware
Schlecht         Lücken), aber ohne böse     │  (leicht zu entdecken, abstürzend)
                 Absicht (z. B. Legacy)      │
```

#### 1. Die Begriffsabgrenzungen

##### Gutartige vs. Bösartige Software (Malware)
* **Gutartige Software (Benign)**: Software, die dem Anwender helfen soll und keine schädigenden Funktionen besitzt (auch wenn sie fehlerhaft sein kann).
* **Bösartige Software (Malicious / Malware)**: Software, die **explizit mit der Absicht entwickelt wurde**, Schaden an IT-Systemen anzurichten, Daten zu stehlen, Nutzer zu spionieren oder Systeme zu sabotieren.

##### Gute vs. Schlechte Software
* **Gute Software**: Befolgt Best Practices (Clean Code, Secure-by-Design), ist performant und fehlerarm.
* **Schlechte Software**: Ist schlecht entworfen, enthält viele Programmierfehler (Bugs) und Sicherheitslücken, wurde aber **nicht** mit Schadabsicht geschrieben.

---

#### 🛡️ Erkennung von Malware in Unternehmen
Unternehmen setzen verschiedene Techniken auf Endgeräten (Endpoints) und im Netzwerk ein, um Malware zu identifizieren:

1. **Signaturbasierte Erkennung (Statisch)**:
   * *Funktionsweise*: Vergleicht den Hashwert oder bestimmte Byte-Muster einer Datei mit einer Datenbank bekannter Schadsoftware.
   * *Grenze*: Erkennt keine neuartigen Angriffe (Zero-Day-Exploits) oder polymorphe Malware, die ihren Code verändert.
2. **Heuristische & Verhaltensbasierte Erkennung (Dynamisch)**:
   * *Funktionsweise*: Führt verdächtige Dateien in einer isolierten Testumgebung (**Sandbox**) aus und beobachtet deren Verhalten (z. B. ob sie versuchen, Systemdateien zu überschreiben, sich im Autostart einzutragen oder Prozesse zu injizieren).
3. **Netzwerk-Anomalieerkennung**:
   * *Funktionsweise*: Überwacht den Datenverkehr auf Verbindungen zu bekannten Command-and-Control-Servern (C2) von Botnetzen oder auf ungewöhnlich große Datenabflüsse (Data Exfiltration).
4. **EDR-Systeme (Endpoint Detection & Response)**:
   * *Funktionsweise*: Kombiniert obige Methoden auf Endgeräten, zeichnet Systemaktivitäten auf und ermöglicht die sofortige Isolierung betrofener Rechner.

**Verknüpfte Zettel:**
- [[Software Engineering]] (Software-Lebenszyklus und Code-Qualität)
- [[Qualitätsicherung]] (Testen und Verifizieren von Software)
- [[Qualitätswerkzeuge]] (Methoden zur Messung von Codequalität)

---
#### Flashcards

Was ist der Unterschied zwischen schlechter Software (Bad Software) und Malware?::Schlechte Software enthält Fehler/Lücken ohne Absicht (Bugs). Malware wird absichtlich programmiert, um Schaden anzurichten.

Wie funktioniert die heuristische Malware-Erkennung im Vergleich zur signaturbasierten?::Die signaturbasierte Erkennung vergleicht bekannte Dateimuster/Hashes. Die heuristische Erkennung beobachtet das Verhalten einer Datei in einer Sandbox auf schädliche Aktionen.

Warum scheitert die signaturbasierte Erkennung bei Zero-Day-Exploits?::Weil für neue, unbekannte Angriffe (Zero-Days) noch keine Signaturen in den Datenbanken der Antiviren-Hersteller existieren.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Softwarequalitäten]]
SORT file.mtime DESC
```