#Note

2026-06-12

Tags: [[Datenbanken]], [[Java]], [[JPA]], [[ORM]], [[EntityManager]]
#datenbanken 

---
Die **Jakarta Persistence API (JPA)** ist das Regelwerk. Sie definiert, wie Objekte auf Tabellen gemappt werden. Ein Provider wie Hibernate führt diese Regeln dann aus. Um JPA zu nutzen, greifen drei zentrale Zahnräder ineinander:

1. Das Mapping (Die Klasse)

Damit JPA weiß, dass eine normale Java-Klasse in eine Tabelle übersetzt werden soll, nutzen wir Metadaten-Annotationen:

- `@Entity`: Markiert die Klasse als persistentes Objekt (Tabelle).
- `@Id`: Zwingend erforderlich! Markiert die Instanzvariable, die den Primärschlüssel repräsentiert.
- `@GeneratedValue`: Weist die Datenbank an, die ID automatisch hochzuzählen (z.B. Auto-Increment).

2. Die Konfiguration (`persistence.xml`)

Die zentrale Steuerungsdatei. Sie definiert die "Persistence Unit" und enthält:

1. Datenbank-Zugangsdaten (URL, User, Passwort).
2. Den verwendeten JPA-Provider (z.B. Hibernate).
3. Strategien zur automatischen Schema-Generierung (z.B. Tabellen automatisch beim Start anlegen).

4. Der Arbeiter (`EntityManager`)

Der `EntityManager` ist die zentrale Schnittstelle zur Datenbank. Er verwaltet den **Persistence Context** (den Arbeitsspeicher der Datenbank-Sitzung). Alles, was im Persistence Context liegt, wird vom EntityManager überwacht.

Daraus ergibt sich der strikte **Objektlebenszyklus (4 Zustände)**:

1. **Transient (Neu):** Das Objekt wurde mit `new` in Java erstellt. Es existiert nur im RAM, die Datenbank kennt es noch nicht.
2. **Managed (Verwaltet):** Das Objekt wurde mit `em.persist()` oder `em.find()` in den Persistence Context aufgenommen. Alle Änderungen am Objekt (z.B. `person.setVorname()`) werden automatisch verfolgt und beim `commit` als `UPDATE` in die Datenbank geschrieben.
3. **Detached (Abgelöst):** Der Persistence Context wurde geschlossen. Das Objekt existiert noch im RAM, aber Änderungen werden nicht mehr als SQL in die Datenbank synchronisiert.
4. **Removed (Gelöscht):** Das Objekt wurde mit `em.remove()` zum Löschen markiert. Beim nächsten `commit` feuert JPA ein `DELETE` auf die Datenbank.

Abfragestrategien (Wie lese ich Daten?)

JPA bietet 3 Wege, um Objekte zu lesen:

1. **em.find(Class, ID)****:** Der direkte Weg für Einzelobjekte über den Primärschlüssel. Sehr effizient, aber keine Filterung möglich.
2. **JPQL (Java Persistence Query Language):** Sehr ähnlich zu SQL, aber man fragt nicht Tabellen, sondern Java-Objekte (Entities) ab. Fehler werden leider erst zur Laufzeit (Runtime) erkannt.
3. **Criteria API:** Komplexe, rein programmatische Erstellung von Abfragen via Java-Code. Vorteil: Absolute Typsicherheit – Fehler fallen schon beim Kompilieren auf.

---

### Flashcards

Annotationen: Welche Funktion haben die Annotationen `@Entity` und `@Id` in einer Java-Klasse?
?
`@Entity` markiert eine reguläre Java-Klasse als persistentes Domänenobjekt, welches auf eine Datenbanktabelle abgebildet werden soll. `@Id` kennzeichnet dabei zwingend die Instanzvariable, die von JPA als Primärschlüssel verwendet werden soll.

Konfiguration: Welche zentralen Informationen werden in der Datei `persistence.xml` definiert?::Sie definiert die „Persistence Units“, welche unter anderem Datenbank-Zugangsdaten (URL, User, Passwort), den JPA-Provider (wie Hibernate), die zu verwaltenden Klassen und Strategien zur automatischen Schema-Generierung enthalten.

Lebenszyklus: Beschreiben Sie den Zustand „Managed“ (Verwaltet) einer Entity. Wie verhält sich das System bei Änderungen an einem verwalteten Objekt?
?
Im Zustand _Managed_ ist die Entity in den Persistence Context aufgenommen worden (z.B. durch `persist()` oder `find()`). Das System überwacht das Objekt: Alle Änderungen an den Instanzvariablen werden automatisch verfolgt und beim Transaktions-Commit mit der Datenbank synchronisiert (als SQL-Update ausgeführt).

Abfragesprachen: Was ist der Hauptunterschied in der Typsicherheit zwischen JPQL und der Criteria API?
?
Fehler in JPQL (da es als String formuliert wird) werden erst zur Laufzeit (Runtime) beim Ausführen erkannt. Die Criteria API bietet hingegen echte Typsicherheit im Java-Code, wodurch Syntaxfehler bereits frühzeitig zur Kompilierzeit abgefangen werden können.

Welche Auswirkung hat die Methode `em.persist(obj)` auf ein transientes Java-Objekt im Kontext des Lebenszyklus?::Sie überführt das Objekt vom Zustand _Transient_ in den Zustand _Managed_. Es wird dem Persistence Context hinzugefügt, wodurch beim nächsten Transaktions-Commit automatisch ein `INSERT`-Befehl in der Datenbank ausgelöst wird.

Was ist der Unterschied zwischen dem Zustand _Managed_ und _Detached_ bei JPA-Entities?::_Managed_-Objekte befinden sich im aktiven Persistence Context und jede Änderung an ihnen wird automatisch in die Datenbank synchronisiert. _Detached_-Objekte wurden von diesem Kontext gelöst; sie existieren weiterhin im RAM, aber Änderungen an ihnen haben keinerlei Auswirkungen mehr auf die Datenbank.


---
### Verwendung
```dataview
TABLE file.mtime AS "Bearbeitet"
FROM [[JPA]]
SORT file.mtime DESC
```