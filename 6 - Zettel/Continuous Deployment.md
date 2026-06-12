#Note

2026-06-12

Tags: [[Automatisierung]], [[DevOps]], [[Softwareentwicklung]]
#cloud_computing 

---
Die automatisierte Auslieferung von Softwareversionen ist ein Kernbestandteil moderner Cloud-Architekturen. Während die klassische _Continuous Integration_ den Code testet und _Continuous Delivery_ das baubare Artefakt vorbereitet, ist **Continuous Deployment** die absolute Endstufe dieses Prozesses,. Es baut architektonisch direkt auf der Continuous Delivery auf und treibt die Automatisierung auf die Spitze: Es umfasst die **vollautomatisierte Inbetriebnahme (Deployment)** der neu erstellten Softwareversion ohne jeglichen menschlichen Freigabeschritt,.

Das explizite architektonische Ziel dieses Paradigmas ist die **Risikominimierung im operativen Betrieb**. Bei manuellen Livegängen entstehen oft kritische Ausfälle, weil das korrekte Herunterfahren des alten Softwarestands und das saubere Starten der neuen Version händisch fehleranfällig sind. Continuous Deployment verhindert diese menschlichen Fehler durch exakt reproduzierbare, skriptbasierte Rollout-Routinen.

Der Zwang durch Skalierung

Dass Unternehmen diese radikale Automatisierung anstreben, ist in der Cloud oft keine freie Entscheidung, sondern ein technischer Imperativ. Die Cloud-Infrastruktur basiert stark auf Paradigmen wie der **[[Horizontale Skalierung]]**. Da Ressourcen dabei über viele Knoten verteilt sind und dynamisch hinzukommen oder wegschalten, bricht das klassische Administrationsmodell zusammen. Es ist auf verteilten Systemen schlichtweg nicht mehr möglich, Code auf jeder verwendeten Maschine manuell zu testen und händisch ein Deployment vorzunehmen.

Diese harte Grenze erzwingt es, dass die gesamte Release-Kette – von der Code-Änderung bis zum laufenden Prozess auf dem Endserver – kompromisslos durch Continuous Deployment automatisiert werden muss. Das Artefakt wird generiert, verteilt und der Container (oder die Instanz) wird vollautomatisiert neu gestartet.

---

### Flashcards

Was ist das primäre, operative Ziel von Continuous Deployment im Vergleich zum manuellen Livegang einer Software?
?
Das primäre Ziel ist es, all jene manuellen Fehler zu vermeiden, die typischerweise durch menschliche Eingriffe beim Herunterfahren des alten Softwarestands und dem anschließenden Starten der neuen Softwareversion entstehen.

Auf welcher spezifischen Prozess-Stufe baut Continuous Deployment zwingend auf und was ist der Unterschied zwischen den beiden Konzepten?::Continuous Deployment baut direkt auf **Continuous Delivery** auf. Während Delivery nur den Bau des auslieferbaren Artefakts und der Deploymentskripte automatisiert, übernimmt Deployment auch die tatsächliche automatisierte Inbetriebnahme (den Livegang) der Version,,.

Warum ist Continuous Deployment in modernen Cloud-Architekturen, die intensiv horizontale Skalierung nutzen, zwingend erforderlich?::Weil bei horizontaler Skalierung eine Anwendung über eine Vielzahl von Maschinen verteilt wird; es ist schlichtweg nicht mehr möglich, auf jeder einzeln verwendeten Maschine den Code zu testen und manuell ein Deployment vorzunehmen.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[Continuous Deployment]]
SORT file.mtime DESC
```