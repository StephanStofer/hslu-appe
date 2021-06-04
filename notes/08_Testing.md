# Testen von Applikationen

Testaspekte für verschiedene Architekturen.

## Ziele für gute Tests

* Testausführung weit möglichst automatisieren
* Qualität von Testcode wie produktiven Code behandeln
* Tests lohnen sich
* UseCases und Funktionen möglichst einzeln testen, sonst instabiler auf Veränderungen
* Kurze einfache Testfälle, (Selektivität der Testfälle)
* Teste der normalen, erwarteten Ablaufs
* Ausnahmen und provozierte Fehler testen

Nur so komplex wie nötig und so einfach wie möglich.

## Testaspekte

Unterschiedliche Testarten wie *Funktionale*, *Performance-/Stress* und *Sicherheits*-Tests. Je nach
Architektur und Applikationsart konzetrieren sich die Tests stärker auf die Server.

### Funktionale Applikationstests

* Testen vollständige App
* kombiniertes Testen von Business- und Applikationslogik
* können sehr aufwendig werden
* Erfordern wohldefinierte Startbedingungen (Daten)
* Zeitaufwendig
* Aufwändige Umgebung (Systemanforderung)

### Performance- und Stress-Tests

* Belastungstests durch viele parallele Clients
* Verhalten testen wie Queueing, zurückweisen, abweisen der Anfragen
* Wiederanlaufverhalten zur Robustheit und Stabilität und Resilienz

### Sicherheits-Test

* vorallem Web-Anwendungen
* siehe OWASP

## Tests in Schichtenarchitektur

Gefahr besteht, dass man immer alle unteren Schichten *mittestet*. Daraus negative Konsequenzen für
die Integrationstests, weil Ausfühurngszeit steigt, Selektivität sinkt. Werden immer mehr zu
Integrationstests statt Unit-Tests. Einsatz von Test Doubles um die Sichten einzeln und entkoppelt
voneinander testen.

## Testen von Rich-GUI-Applikationen

GUI ist Schnittstelle selber. Interaktivität muss für automatisierten Tests «simuliert» und
aufgezeichnet werden. Verifikation muss «optisch» erfolgen. Stolpersteine wie Bildschirmauflösung,
Fensterpositionen, Zeitverhalten etc. Relativ hoher Aufwand für Testprogrammierung. Starke Kopplung
an die interne GUI-Struktur.

## Testen von Applikationen mit DB

Herausforderung ist die Datenmanipulation durch Testfälle (Reproduzierbarkeit). Anforderungen sind

* Zustanz der DB muss vor und nach Ausführung definiert sein
* Effiziente Verifikation des DB-Inhaltes
* Parallele Testausführung

Grundlage dazu ist Testdatenmanagement. Das Bereitstellen und aktive Wartung von Testdaten.

### Lösungsansätze

* Frameworks für Daten, Fälle und Verifikation, z.B. DBUnit
* Verwendung mehrere Schemas auf zentralem DBMS
* Lokale DB pro Entwickler - Aufwand/Kosten für Pflege
* In-Memory-DB für jeden Test. Ist der Repräsentativ?
* Prod DB als Docker-Container

## Testen von Web-Apps und -Services

Sind einfacher zu Testen weil auf Http/s Request-Response Modell basieren. Ausnahme AJAX-calls sind
schwieriger. Stress- und Security Tests ebenfalls gut machbar. Je besser HTML-Code desto effizienter
und einfacher wird Testen (positive Mitkoppelung). Alle Elemente zur Identifikation und Selektion
mit eindeutiger ID kennzeichnen. Schwierigkeiten durch grössere Dynamik (reactive programming,
Clientscripts, Asynchronität). Grundlage dazu ist Browser-Automation (Versionsproblematik, IE,
Chrome, Safari, Mobile etc.)
Bekannte Frameworks sind SeleniumHQ und Arquillian

## Testen von REST-(Micro)-Services

Weil REST-Services sprachunabhängig gibt es grosse Zahl von Frameworks. Für simple Fälle reichen
Bordmittel oder auch curl. Jüngere Libraries für REST-Clients sind so abstrakt und kompakt (OkHttp,
Unirest) dass man quasi mittesten kann. MS-Frameworks (SpringBoot, Micronaut) bieten integrierte
Ergänzungen für Testing an. Es gibt auch *[Testcontainer](www.testcontainers.org)*

## Bilanz

Pragmatisch, selektiv und effizient testen.
