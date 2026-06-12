#Note

2026-06-12

Tags: [[Cloud Computing]], [[Systemarchitektur]], [[Bereitstellungsmodelle]], [[IT-Sicherheit]]
#cloud_computing

---
In der Systemarchitektur definiert das Bereitstellungsmodell (Deployment Model), _wo_ und _wie_ Cloud-Dienstleistungen technisch realisiert werden. Die **Private Cloud** markiert hierbei das Modell mit der geringsten Abstraktion der Infrastruktur und dem zeitgleich höchsten Wartungsaufwand.

Der fundamentale Unterschied zum klassischen, manuellen On-Premise-Betrieb ist die technologische Schnittstelle: In einer Private Cloud kommt eine Cloud-Verwaltungssoftware zum Einsatz, um die lokale Hardware zu abstrahieren und virtuelle Ressourcen **automatisiert und standardisiert** bereitzustellen. Das Unternehmen behält jedoch die absolute physische Kontrolle: Es verantwortet weiterhin die Beschaffung, den Betrieb und die Wartung sämtlicher Hard- und Software.

Maximale Kontrolle und das "Airgap"-Prinzip

Der primäre architektonische Treiber für die Wahl einer Private Cloud ist das Bedürfnis nach unbedingter Datensouveränität und physischer Sicherheit. Da die Systeme in einem lokalen Rechenzentrum betrieben werden, ist der physische Zugriff streng gesichert.

Für hochsensible Datenverarbeitungen ermöglicht die Private Cloud sogenannte **"Airgap"-Umgebungen**. Hierbei handelt es sich um Infrastrukturkonfigurationen, die physisch oder logisch komplett vom restlichen Internet isoliert (abgeschnitten) sind. Angreifer von außen haben somit keinen Netzwerkvektor, um auf die Systeme zuzugreifen. Das Unternehmen hat zudem die maximale Kontrolle über die Hardwareauswahl und kann eigene, streng maßgeschneiderte Sicherheitskonzepte durchsetzen.

Der architektonische Trade-off

Der Preis für diese absolute Kontrolle ist der Verzicht auf die größten Hebel der modernen Cloud-Ökonomie. Private Clouds eignen sich gut für Organisationen mit stark begrenzter Bandbreite oder solche, die bestehende Hardware und Personal zwingend weiterverwenden müssen.

Die massiven Nachteile sind jedoch:

1. **Fehlende globale Skalierung:** Es existiert keine weltweit verteilte Infrastruktur, Lastspitzen können nur bedient werden, wenn vorab teure (und oft ungenutzte) Hardware-Ressourcen angeschafft wurden.
2. **Eingeschränkte Innovation:** Unternehmen können nicht einfach auf fertige, hochinnovative Cloud-Dienste (wie Machine Learning oder Spracherkennungs-APIs) zurückgreifen, da deren Eigenentwicklung On-Premise astronomische Kosten verursachen würde.

---

### Flashcards

Was ist das definierende Merkmal einer Private Cloud hinsichtlich der Verantwortlichkeit für die Infrastruktur?
?
Trotz der Nutzung von moderner Cloud-Software zur automatisierten Bereitstellung virtueller Ressourcen verantwortet das Unternehmen weiterhin vollständig die Beschaffung, den Betrieb und die Wartung der gesamten physischen Hard- und Software im eigenen Rechenzentrum.

Was versteht man im Architektur-Kontext der Private Cloud unter einer "Airgap"-Umgebung?::Das sind Infrastrukturkonfigurationen, die keinen Internetzugang besitzen. Sie sind netzwerktechnisch komplett isoliert und werden primär eingesetzt, um ein maximales Sicherheitsniveau für hochsensible Daten zu garantieren.

Welcher fundamentale Trade-off (Nachteil) entsteht durch die Beibehaltung der maximalen Kontrolle in einer Private Cloud?::Durch den lokalen Betrieb geht die globale Infrastruktur und die grenzenlose Skalierbarkeit verloren. Zudem führt die Architektur zu eingeschränkter Innovation, da komplexe Fremd-Dienste (wie KI oder Spracherkennung der großen Provider) nicht einfach konsumiert werden können.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Private Cloud]]
SORT file.mtime DESC
```