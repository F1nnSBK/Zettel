Klausur
2/3 Wissensfragen, 1/3 Transferfragen, Taschenrechner

Warum IT-Sicherheit
Unterschied IT-Sicherheit vs Cyber
Cyber -> Anbindung ans Netz
IT Sicherheit -> Lokale Sicherheit in IT Systemen
290mrd Schaden
Beste Verteidiger isnd die leute, die Angreifen können
Was ist Cybersicherheit eigentlich?
Jeep Cherokee Hack
Cyberraum -> Kein Gewaltmonopol (Vor- & Nachteil), Hacker sind in Ländern, die keine Gesetze dafür haben oft sicher

Grundziele
Haupt- & Nebenziele:
CIA-Triad - Vertraulichkeit, Integrität, Verfügbarkeit
Authentizität & Authentifikation -> Identifikation des Gegenübers
Autorisierung -> Wenn man dann Authentifiziert ist, wird autorisiert, also auf welchen Bereich hat jemand Zugriff? Was darf sie?
Verbindlichkeit -> Nichtabstreitbarkeit (Nachvollziehbarkeit) -> Asymmetrische Verschlüsselung
Maßnahmen zur Prävention
Anonymisierung & Pseudoanonymisierung -> Gewährleistung, dass eine Person nicht oder nicht unmittelbar identifiziert werden kann

Informationssichertheit -> Sicherheit der Information selbst, digital & analog
Venn Diagramm der Informations-, IT- und Cybersicherheit

Safety vs Security
S. 70

Sicherheitslücke
-> Stelle in Soft- und/oder Hardware, die es einem Angreifer ermöglicht Angriffe auf ein IT-System umzusetzen
Angriffsfläche
-> Alle IT-Systeme & Dienste, die angegriffen werden können
Angriffsvektor
-> Das Mittel mti dem der Angriff ausgeführt wird (Exploit)
Haus Analogie

Clear Web / Surface Web
Deep Web
Dark Net

Weiterentwicklung von Cybersecurity
Gute Software vs Schlechte Software
(Gutartig - Bösartig)

Hacker Typen - Black Hat, White Hat, Gray Hat, Green Hat, Blue Hat, Red Hat

Passive Angriffe
-> zB 
Aktive Angriffe

Zielgerichtet vs nicht zielgerichtet

DAU = Dümmster Anzunehmender User

Typische Sicherheitslücken
Anforderungsfehler
Designfehler
Implementierungsfehler
Installations- und Administrationsfehler

Funktionale Sicherheit 
GRC -> Governance, Risk Management, Compliance
Ziele davon S.13
Steuerbarkeit, Anpassungsfähigkeit, ...
-> Ist kein reines IT-Thema, es betrifft alle (z.B. auch HR)

Compliance -> Einhaltung von Vorgaben (z.B. DSGVO -> Extern, Verhaltensregeln -> Intern)
Drei Säulen der IT-Security
Regulatorische Vorgeben
Technische Maßnahmen
Organisatorische Prozesse

Compliance wird oft nur als Kostenfatkor gesehen
Regelkreis
Plan -> Do -> Check -> Act (PDCA)
IT-Compliance am besten by Design und NICHT nachträglich
Compliance $\neq$ Sicherheit
Security Governance
Gibt Orientierung/Richtlinien vor (Führung)
-> Keine Einzelentscheidungen
Gov definiert: ... S.52

Incident Response
SWOT-Analyse

Risikomanagementmethoden
ALARP - Vorteile/Nachteile -> Argumentation

PDCA-Zyklus (Die 4 Phasen - Do ist nicht die Umsetzung)
Risikoidentifikation, -bewertung, ...

SDCA (Standardize Do Check Act)

Zusammenhang: SWOT -> PDCA & SDCA <-> Incident Response Cycle
Grafik S.123

Incident Response vs IT Forensik
IT Forensik meint bei Incident Response kein vollständige IT-forensische Analyse, häufig reicht eine gezielte Voruntersuchung/-Analyse.
Vorbereitung -> Identifikation & Analyse <-> Eindämmung -> Bereinigung -> Wiederherstellung -> Lessons Learned

Playbooks S.60
Pyramid of Pain (Mit Blick auf den Angreifer)
Hashwerte -> IP-Adressen -> Domainnamen -> Netzwerk-/Hostartefakte -> Tools -> TTPs (Tactic Technique Procedures)

MITRE-ATT&CK-Framework & MITRE Defend


---

Symmetrische & Asymmetrische
Beispiel Magic.py, Restklassenringe, Modulo Operator topologisch dargestellt, Primkörper, elliptische Kurven (gleiches Prinzip)


Kryptographie - Kommt gefühlt überall vor (Bsp. Herzschrittmacher, WLAN, Autoschlüssel, ...)
-> Vergleich Motor, das Auto und der Sprit muss aber auch da sein

Kryptographie und Kryptoanalyse als Gegenspieler
Statt Schlüsseltext spricht man von e- und d-Funktionen (Encryption-Decryption Funktionen)
und k für Key.
Beispiel: $e_k: x \to y$ & $e_k^{-1}: y \to x$ oder $d_k: y \to x$ 
Kerckhoff'sches Prinzip -> Das muss jeder Informatiker kennen.
Überblick Kryptographie S.77
Zusammenhang:
Gruppe (Additiv, Multiplikativ), Ring (S.8, Modul 9), Restklassenringe
-> Ring als math. Objekt, auf dem man Modulo Rechnung anwendet (Schneller als Division)
Teilerfremd zum Modulo Wert
$(\mathbb{Z}_9, +, x)=\set{0,1,2,3,4,5,6,7,8,9}$
Körper mit Division gibt Probleme -> Lösung sind Primkörper, weil man darin Teilen und Multiplizieren kann und er trotzdem abgeschlossen ist (Erweiterungskörper)
Modulo sollte also Primzahl sein, muss aber nicht (Typische Aufgabe in der Klausur), mit k = 2 geht es nicht aber mit k = 3 schon, weil 3 und 26 nur die 1 als größten gemeinsamen Teiler haben
Wie viele Schlüssel gibt es also?
Ausprobieren oder Eulersche Phi Funktion
Vigenere-Chiffre -> Schwäche sind Muster bei zu kurzne Keys
Muster sind in der Kryptograhpie das Schlimmste was es gibt

Stromchiffren -> Jeden einzelne Bit wird verschlüsselt S. 7, 12
Wird zb bei der Verbindung von Smartphone zum Sendemast verwendet
Warum geht das, obwohl es so simpel ist?
XOR gibt uns eine 50% Chance was verschlüsselt wurde, wenn wir ein gewissen Bit sehen, das scheint erstmal unsicher *ABER* wir haben tausende oder zehntausende Bits, dadurch wird es fast unknackbar. Wenn dann alles gleich wahrscheinlich ist, dann ist alle gleich falsch und gleich richtig -> man kann es nicht interpretieren
Was genau sind die Bit $s_i, x_i \text{ und } y_i$?
Wie erzeugt man zufällige Zahlen?
PRNG, TRNG, CSPRNG Fail bei rand() in C
LFSR Konstruktion
Trivium, GSM Standard A5/1 (verbessert A5/3)
Wenn nicht zufällig -> Knackbar


Blockchiffren -> Blockweise Verschlüsselung
DES - Data Encryption Standard
(64 Bit Blocks - Key ist aber 56 Bit lange)
Gibt es ein sicheres Verfahren um Blockchiffren zu bauen? -> Nein
Claude Shannon - Diffusion & Konfusion / P-Box (Bitpermutation) & S-Boxen (Substitution)
Bei AES sind es MixColumn-Operation
Ein Bit soll die Hälfte aller anderen Bits verändern
Man soll immer mit Konfusion und Diffusion zusammen arbeiten, nie einzeln.
Konfusion (ENIGMA) -> fail <- Diffusion (Vegenere)
Strategie für den Chiffrenbau -> Sinvolle Verschachtelung über mehrere Runden
Jede Runde nutzt einen eigenen Schlüssel, der einzlene Schlüssel (Rundenschlüssel) wird in Teile zerlegt
FPGA - Copacobana Uni Bochum - DES


TOR 
.onion Seiten - theoretisch kann jeder beim Netzwerk mitmachen, es gibt aber strenge Anforderungen und die Hoster müssen ein Vertrauensniveau haben.
Freiweillige - Organisationen - NGOs - Universitäten
Wieso dauert die Asymm. Verschlüsselung so viel länger?
Aufbau des Circuits
Verschlüsselung der Daten
Entschlüsselung der Schichten
Datenrückfluss

Jeep Cherokee Hack
32Sek Passwort Generierung




Einweg & Hashfunktionen
Digitale Signaturen und Zertifikate
Schlüsselmanagement und Austausch
Authentifiktation

---

Brute Force
Wörterbücher
Seitenkanäle
Lineare und differentielle Kryptanalyse

---

Malware
Angriffsstrategien
Einfluss von Machine Learning

---

Grundlagen
Forensische Artefakte