#Note

2026-06-12

Tags: [[Docker]], [[Cloud Computing]], [[Deployment]]
#cloud_computing

---
Image-from-the-shelf

Um die massiven Vorteile der Prozessvirtualisierung weltweit skalieren zu können, benötigt die Architektur einen zentralen Verteilungsmechanismus. Die **Docker Registry** erfüllt genau diesen Zweck: Sie ist der zentrale Ort zum Speichern und Verteilen von Docker Images.

Sie etabliert das sogenannte **"Image-from-the-shelf"-Paradigma**. Wie Produkte in einem Supermarktregal liegen fertige Laufzeitumgebungen bereit. Sucht ein Unternehmen nach einer bestimmten Funktionalität (z.B. einem Datenbank-Server), muss es diesen nicht mehr mühsam konfigurieren, sondern kann das fertige Abbild einfach aus der Registry beziehen und in Millisekunden starten. Hierbei wird architektonisch zwischen zwei Zugriffsmodellen unterschieden: **öffentliche Registries (Public)**, die weltweit für jeden erreichbar sind, und **geschlossene Registries (Private)**, die den Zugriff strikt auf ein Unternehmensnetzwerk begrenzen.

Netzwerk-Effizienz durch Schichten

Ein gigantischer architektonischer Vorteil der Docker Registry liegt in ihrer Symbiose mit der Schichtenarchitektur (Layers) von Docker Images. Wenn der Docker-Daemon ein Image aus der Registry lädt (Pull) oder in diese hochlädt (Push), wird niemals ein monolithischer Block übertragen.

Das System gleicht lediglich die kryptografischen Prüfsummen ab und **überträgt ausschließlich jene Schichten, die auf dem Zielsystem oder in der Registry noch fehlen**. Nutzen zehn verschiedene Applikationen im Unternehmen dasselbe 200 MB große Basis-Betriebssystem, wird diese Basisschicht nur ein einziges Mal über das Netzwerk transferiert und in der Registry gespeichert.

Docker Hub und die Vertrauensfrage

Die weltweite Standard-Registry (und der automatische Fallback nach einer Docker-Installation) ist der **Docker Hub** (https://hub.docker.com). Als größte öffentliche Bibliothek für Container-Images birgt dieser offene Ansatz jedoch ein massives Sicherheitsrisiko durch Fremdcode.

Um die Authentizität und Sicherheit für kritische Architekturen zu gewährleisten, pflegt Docker mit einem eigenen Team sogenannte **"offizielle Images"**. Diese werden streng kontrolliert und regelmäßig aktualisiert. Architektonisch lassen sich diese vertrauenswürdigen offiziellen Images (wie z.B. für MySQL oder Ubuntu) daran erkennen, dass sie **keinen Usernamen bzw. Organisationsnamen in ihrem Tag tragen**.

---

### Flashcards

Welches fundamentale Paradigma der Softwareauslieferung wird durch die Docker Registry ermöglicht und was bedeutet es?
?
Das **"Image-from-the-shelf"-Paradigma**. Es bedeutet, dass Unternehmen oder Entwickler fertige, vorkonfigurierte Laufzeitumgebungen (Docker Images) wie aus einem Regal zentral abrufen und sofort direkt einsetzen können, ohne sie selbst bauen zu müssen.

Warum ist der Datentransfer zwischen einem lokalen Docker-Daemon und einer Docker Registry architektonisch derart ressourcen- und netzwerkeffizient?::Da der Transfer strikt auf der Schichtenarchitektur von Docker basiert. Es werden immer nur jene spezifischen Image-Schichten (Layers) über das Netzwerk übertragen, die auf der Zielmaschine bzw. in der Registry noch nicht existieren.

Wie lassen sich in der öffentlichen Registry "Docker Hub" die besonders vertrauenswürdigen, offiziellen Images identifizieren und wer pflegt sie?::Offizielle Images zeichnen sich dadurch aus, dass sie **keinen Usernamen** im Tag tragen. Sie werden von einem speziellen Docker-Team in Zusammenarbeit mit den jeweiligen Projekten gepflegt und regelmäßig mit Aktualisierungen versorgt.

---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Docker Registry]]
SORT file.mtime DESC
```