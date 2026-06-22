#Note

2026-06-22

Tags: [[Cyber-Security]], [[IT-Sicherheit]], [[IoT]], [[Hardware-Sicherheit]]
#it_security

---

### Jeep Cherokee Hack (Praxis-Beispiel)

Der **Jeep Cherokee Hack (2015)** von Charlie Miller und Chris Valasek ist eines der bekanntesten Praxis-Beispiele für Cyber-Angriffe auf IoT-Geräte und kritische Hardware-Infrastrukturen. Die Hacker demonstrierten, wie sie aus der Ferne über das Mobilfunknetz die volle Kontrolle über ein fahrendes Auto übernehmen konnten.

#### Funktionsweise des Hacks
1. **Einstiegspunkt (Infotainment-System)**: Über das *Uconnect*-System des Fahrzeugs (welches über Mobilfunk mit dem Internet verbunden war) fanden die Hacker einen offenen Port.
2. **Brücke zum CAN-Bus**: Über eine Schwachstelle im Infotainment-System konnten sie auf den internen Kommunikationsbus des Fahrzeugs (den **CAN-Bus**) zugreifen.
3. **Befehlsinjektion**: Da der CAN-Bus unverschlüsselt war und keine Authentifizierung erforderte, konnten die Hacker gefälschte Steuerungsbefehle an kritische Steuergeräte (ECUs) senden. Dadurch steuerten sie das Lenkrad, die Bremsen, die Scheibenwischer und den Motor.

#### Sicherheitsmaßnahmen zur Verhinderung
- **Strikte Systemtrennung (Segregation)**: Physische oder logische Isolation des ungesicherten Infotainment-Systems vom sicherheitskritischen CAN-Bus (z. B. durch Gateways/Firewalls).
- **Kryptographische Code-Signierung**: Firmware-Updates für Steuergeräte dürfen nur installiert werden, wenn sie eine gültige digitale Signatur des Herstellers aufweisen (Verhinderung von Schadcode-Injektion).
- **Intrusion Detection/Prevention Systems (IDS/IPS)**: Überwachung des CAN-Bus-Verkehrs auf anomale Nachrichten oder ungewöhnliche Befehlsraten.
- **Port-Filterung**: Deaktivieren aller unnötigen, nach außen offenen Ports auf dem Mobilfunk-Modem.

**Verknüpfte Zettel:**
- [[Safety vs. Security]] (Abhängigkeit der physischen Sicherheit von Cybersicherheit)
- [[Virtualisierung]] (Konzepte der Kapselung und Systemtrennung)
- [[namespaces]] / [[cgroups]] (Linux-basierte Ansätze zur Isolation von Systemressourcen)

---
#### Flashcards

Was war der Einstiegspunkt und das Endziel beim Jeep Cherokee Hack?::Einstiegspunkt war das Uconnect-Infotainment-System über Mobilfunk; Endziel war der CAN-Bus zur Steuerung sicherheitskritischer Fahrzeugfunktionen.

Welche drei Hauptmaßnahmen hätten den Jeep Cherokee Hack verhindern können?
?
1. **Systemsegregation**: Strikte Trennung von Infotainment und Fahrsteuerung.
2. **Code-Signierung**: Schutz von Firmware-Updates vor Manipulation.
3. **Anomalieerkennung (IDS)**: Überwachung des CAN-Bus-Verkehrs.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Jeep Cherokee Hack]]
SORT file.mtime DESC
```