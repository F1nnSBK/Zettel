#Note

2026-06-12

Tags: [[Datenbanken]], [[Java]], [[JPA]], [[ORM]], [[Hibernate]], [[Architektur]]
#datenbanken 

---
Um dem mühsamen, manuellen Verketten von SQL-Strings und Auslesen von ResultSets (über JDBC) zu entkommen, nutzt man in modernen Anwendungen das **Object-Relational Mapping (ORM)**.

Diese Automatisierung übernimmt die komplette Übersetzung zwischen Objektwelt und relationalem Schema (Klassen ↔ Tabellen, Objekte ↔ Zeilen). Der Codeaufwand für den Datenbankzugriff wird dadurch drastisch reduziert, und die Wartbarkeit steigt enorm.

Die 3 Ebenen der Abstraktion

Einer der wichtigsten Punkte für das Verständnis (und die Klausur) ist die strikte Trennung der Begriffe ORM, JPA und Hibernate. Die Architektur baut in drei Schichten aufeinander auf:

**1. Das Konzept: ORM (Object-Relational Mapping)**

- Beschreibt rein die generische Technik, Objekte einer Programmiersprache auf relationale Tabellen abzubilden.
- Es ist völlig unabhängig von spezifischen Sprachen (gibt es auch in Python, C#, etc.) oder Datenbankprodukten.

**2. Die Spezifikation: JPA (Jakarta Persistence API / ehem. Java Persistence API)**

- Der offizielle Java-Standard (eingeführt 2006), um den damaligen Wildwuchs an proprietären Lösungen zu vereinheitlichen.
- JPA ist rein _deklarativ_. Es definiert nur die Schnittstellen (Interfaces), Annotationen (wie `@Entity`) und die Abfragesprache JPQL.
- **Wichtig:** JPA besitzt selbst **keinen** ausführbaren Code für das Mapping! Es ist nur das Regelwerk.

**3. Die Implementierung: z. B. Hibernate**

- Hibernate (bereits 2001 als Pionier gestartet) ist das eigentliche Framework (der "Provider"), das die JPA-Spezifikation mit Leben füllt und die Arbeit erledigt.
- Es bietet oft noch Zusatzfunktionen, die über den JPA-Standard hinausgehen (wie die Hibernate Query Language - HQL).

Die Interaktion: JPA vs. JDBC

JPA und JDBC sind keine Feinde, sie arbeiten auf unterschiedlichen Flughöhen:

- **JPA** ist für den Entwickler die höchste Abstraktionsschicht. Wir arbeiten nur mit Java-Objekten (Entities) und dem `EntityManager`.
- **JDBC** ist die unterste Schicht. Ein JPA-Provider wie Hibernate generiert aus unseren Objekt-Befehlen im Hintergrund echtes SQL und **nutzt intern immer JDBC**, um diese Statements über den Treiber an die Datenbank zu senden.

---

### Flashcards

ORM-Konzept: Was ist das Ziel von Object-Relational Mapping (ORM) und welchen Vorteil bietet es gegenüber der manuellen Arbeit mit JDBC ? (Wiederholungsfrage 3)
?
Das Ziel von ORM ist es, als automatisierte Abstraktionsschicht zwischen Objekten (z.B. Java-Klassen) und Relationen (RDBMS-Tabellen) zu fungieren. Der Vorteil ist, dass Entwickler Daten als native Objekte behandeln können, ohne manuelle SQL-Statements in Strings schreiben oder ResultSets händisch mappen zu müssen.

JPA vs. Hibernate: Erläutern Sie das Verhältnis zwischen JPA und Hibernate. Welcher Teil ist die Spezifikation und welcher die Implementierung ?
?
JPA ist die **Spezifikation** (der offizielle Java-API-Standard, der nur die Schnittstellen definiert, aber keinen ausführenden Code enthält). Hibernate ist die **Implementierung** (der Provider), die diesen Standard mit ausführbarem Code umsetzt und mit Leben füllt.

Schichtenmodell: Wie interagieren JPA, JDBC und die Datenbank technisch miteinander? Wer ruft wen auf ?
?
JPA ist die höchste Schicht für den Entwickler. Ein JPA-Provider (wie Hibernate) generiert aus den Objekt-Anweisungen automatisch SQL und ruft dann intern **immer JDBC** auf, um diese SQL-Befehle physisch an die Datenbank zu senden.

Wann wurde Hibernate als Open-Source-Framework ins Leben gerufen und wann folgte JPA als offizieller Java-Standard zur Vereinheitlichung?::Hibernate startete 2001 als Pionier. Die JPA (Jakarta Persistence API) folgte 2006 als offizieller Standard.

Warum benötigt JPA zwingend eine Implementierung wie Hibernate, EclipseLink oder OpenJPA, um zu funktionieren?::Weil JPA (die Spezifikation) als reine Sammlung von Schnittstellen und Annotationen keinen eigenen ausführbaren Code für das physische Datenbank-Mapping besitzt.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[ORM]]
SORT file.mtime DESC
```