# Architekturmuster

Beschreiben als Konzept den Grundaufbau eines ganzen Systems (Vergleich Enturfsmuster). Es gibt
versch. Muster welche auf ihre besonderen Anforderungeen angepasst sind (gross/komplex, stark
verteilt, inter(re)aktiv, hochverfügbar). Diese sind aber nicht standardisiert wie GoF-Patterns.
Siehe
auch [Catalog of Patterns of Enterprise Application Architecture](https://martinfowler.com/eaaCatalog/)

## Schichtenbildung

Gliederung eines Systems in aufeinander aufbauende, funktional getrennte Schichten. Die
Kommunikation findet über wohldefinierte Schnittstellen statt. Abhängigkeiten nur in Richtung der
tieferliegenden Schicht. Kein Überspringen und keine Zyklen. Die Strukturierung sowohl innerhalb
eines System als auch Systemübergreifend. Bei physischer Verteilung spricht man von *Tiers*.

![Layers in UML](layer-uml.png){width=10%}

Die Bildung einer Schicht kann nach versch. Kriterien erfolgen:

* Logische/Funktional
* Technik
* Abstraktionsebene
* Hierarchisch
    * Funktionale
    * Abstraktionslevel
    * Technologie/Sprache/Framework

In Java manifestieeren sich die versch. Schichten häufig in der Packagestruktur (
ch.domain.sysmte.client.\*). Allerdings schlechter Ansatz, da sie Modularisierung verunmöglicht.
Seit JAVA9 kann Package nicht mehr in mehrere JAR-Dateien zerteilt werden..

## Schichten vs. Features

Alternativen Ansatz der Schichtung als Packages, *package by feature*. Fachliche Sicht
zusammenführen. Sehr vereinfacht; statt horizontal wird vertikal gruppiert. Problematik die
Modularisierung von JAVA9, verunmöglicht *package by feature*, Konsequenz feingranulare
Packages/JARs $\longrightarrow$ wieder positiv!

Ziel ist es *bounded-Contexts* zu identifizieren.

## Verteilte Schichten auf Tiers

Die Schichtenbildung ist eine fundamentale Grundlage um verteilte Anwedungen bzw. ARchitekturen
realisieren. Schichtengrenzen eignen sich sehr gut zur Auftrannung, um Teile auf versch. Systeme zu
deployen. Zur Abstraktion der Aufteilung bzw. der Kommunikation verwendet man idealerweise
austauschbare Schichten.

## Logische 3-Schicht-Architektur

Enthält drei fundamentale Schichten

* Präsentation; GUI-Layer, Maske, WebUI
* Geschäftslogik; Geschäftsprozesse, -Modelle
* Datenhaltung; Datenspeicherung, Datenlogik

Diese Aufteilung lohnt sich praktisch immer, unabhängig der physischen Verteilung: *SoC*
$\rightarrow$ *SRP* $\rightarrow$ *Modularisierung*

### Verfeinerung der Präsentationssicht

Die reine Präsentation und Präsentationlogik weiter trennen.

* durch MVC
* bei Thin-Clients ist es sogar notwendig - HTML/CSS und Javascript

### Verfeinerung der Geschäftslogikschicht

Sinnvoll auch hier weiter zu trennen.

* Business Objects/Domain Objects sind reine objektorientiertes Modell, enthält Daten und Methoden
* Business Funktionen als Services/Businessmethoden

### Verfeinerung der Datenhaltungsschicht

Trennung und Abstraktion der reinen Datenlogik.

* Unabhängig von physischen Datenmodell
* O/R Mapping -> Persistenz-Framework (EF)
* Transparentes Einbinden von Legacy-Systeme
* Abstraktion mehrerr Backend (DBMS-)Systeme
* Transaktionshandling (nicht Steuerung!)

### Resultat der Verfeinerung

Aus der Verfeinerungen der 3-Schicht-Architektur kann bald eine $n$-Schicht-Architektur. SRP und SLA
wird somit noch stärker realisiert, der Aufwand steigt auch der Aufwand.

### $n$-Schichten - Allgemeine Punkte

Je mehr Schichten umso

* Bessere Strukturierung, einzelne Schichten kleiner und einfacher
* Grössere Chance auf Wiederverwendung (einzelner Layers)
* Höhere Flexibilität, z.B. Austausch einzelner Schichten
* Bessere Skalierbarkeit (primär vertikal)
* Einfachere und präzisere Planung/Schätzbarkeit
* Parallele und getrennte Entwicklung möglich

aber

* Komplexität des ganzen Systems wird grösser
* Mehr Schnittstellen, mehr Aufwand, mehr Planung
* Schichten sind technisch – wo bleibt die Fachlichkeit

### Probleme 2-Schicht Architektur

Klassische Client/Server. Typisch mit GUI-Clients mit zentraler Datenhaltung in DBMS

Die Anwedungsschicht (Rich-Client) enthält GUI-, Anwendungs- *und* Business-Logik. Datenschicht
erreicht Integrität mit Datenmodell bzw. Contstraints. Logik über Triggers oder StoredProcedures.

Hauptproblem ist, dass das Datenmodel *meist* kanonisch ist und laufend grösser wird. Es entsteht
starke Kopplung.

### Dikussion 3-Schichten

Man erreicht «natürliche» Aufteilung gemäss logischen Schichten

* Präsenstation
* Domänen- / Businessschicht
* Datenschicht mit Logik und Haltung

Dadurch Vorteil von (manchmal) weniger Redundanzen in der Logik (UI, Backend, DB!?). Hat aber auch
potential indem mehrere und verschiedene Datenquellen abstrahiert werden können und mehrere versch.
Clients realisierbar sind. Echte Zentralisierung von Businesslogik möglich.

### Bilanz

Für eine Schichten-Architektur kommt es auf die Grösse an. Im kleinen Funktinioniert es sehr gut
zentrales Problem ist aber die Breite der Schicht, irgendwann unübersichtlich.

Die *Domäne* eine Applikation wird schlicht zu gross. Als Konsequenz werden die Schichten zu breit,
worin sich Dinge zusammengelegt sind, die nichts miteinander zu tun haben.

## Service Oriented Architektur

Services sind fachlich orientiert und technologieneutral. Services kapseln abgegrenzte Sub-Domänen
ind eigenständige, verteilte Dienste, die dann von übergeordneten Applikationen zur Realisierung
eines Businessprozesses genutzt werden. Ein Service verfügt über

* eine wohldefinierte Schnittstelle
* Services sind in einem Verzeichnisdienst eingebunden und werden dynamisch gesucht und gebunden (
  binding)
* Kommunikation kann über fast beliebgie Protokolle erfolgen (RPC, RMI, CORBA, HTTP, SOAP, REST,
  usw.)

Führt zur fachlichen Entkoppelung und die Services werden kleiner führt aber auch zu verteilten
Applikationen.
