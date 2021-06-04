# Software Architektur
Eine Architektur ist eine **Abstraktion**, es wird etwas zusammenfassend und vereinfachend dargestellt. Vergleich mit Modellierung und Design, es ist ein fliessender Übergang. Sie beschreibt ein **System** durch dessen Strutur und Aufbau (Sub-/ Teilsysteme, Schichtung, Zwiebel, Verteilung) und der darin enthaltenen Softwareteile (Komponenten) und deren Beziehungen. Abhängigkeiten, Schnittstellen, Daten- und Kontrollflüsse, usw.

## Definition von Architektur
> Softwarearchitektur definiert sich durch die Kernelemente eines Systems, welche als Basis für alle weiteren Teile nur schwer und aufwändig verändert werden können.
Martin Fowler

> Die Architektur repräsentiert die signifikanten Designentscheidungen die ein System festhalten, wobei die Signifikanz an den Kosten von Änderungen bemessen wird.
Grady Booch

## Welche Architektur besprechen wir
Wir konzentrieren uns hauptsächlich auf die **Softwarearchitektur** und streifen die Betriebsarchitektur.

### Softwarearchitektur
Besteht unteranderem aus:

* Applikationsarchitektur
* Systemarchitektur
* Lösungsarchitektur

## Aspekte und Herausforderungen der Softwarearchitektur
Grobe Übersicht unter Einhaltung angemessener Qualitätsaspekte

* Grundlende Struktur
    * Schichten, Client/Server, n-tiers, Services usw.
    * Art der Applikation und Deployment
    * Architekturmuster und Prinzipien
* Kommunikation und Verarbeitung
    * Verteilbarkeit, Parallelität, Performance, Robustheit, Resilienz (Robustheit bei Störungen oder Teilausfällen von verteilten Systeme)
    * Kommunikationsmuster (synchron/async)
    * Transaktionalität
* Eingesetzte Technologie
    * Userinterface (Fat-, Richt, Thin)
    * Persistenz der Daten
    * Referenzarchitekturen

## Arten von Applikationen
Es gibt eine grosse Bandbreite von Applikationen mit sehr unterschiedlichen Anforderungen
* Einzelbenutzerapplikatione
    * eher klein, sogar nur eine Mobile-App
    * lokale Persistenz
* Mehrbenutzer
    * Enterprise Software (Unternehmen)
    * Zentrale Services und Daten, beliebige Komplexität
    * Typisch in mehre (Teil-)Systeme aufgebrochen
* Internetanwendung (Public)
    * Typisch mit Web-GUI
    * beliebig viele Benutzer
    * verteilte Datenspeicherung, beliebige Komplexität

## Architekturstile in der Zeit
Mit der Zeit entwickelten sich sehr viele Architekturstile. Je nach Applikationsart erwiesen sich diese als schlecht, aber auch als brauchbar. Erkenntnisse daraus, die Kunst ist die richtige Architektur am richtigen Ort.

## Fliessender Wechsel zw. Design und Architektur
Ist die grosse Herausforderung Muster, Prinzipien und Techniken auf den unterschiedlichen Abstraktionsebenen angemessen zu befolgen und zu beurteilen. Schlussendlich haben wir viele Klassen und Schnittstellen - jede weitere Strukturierung ergbit sich weitgehend von der Organisation und Konvention.

# Systeme und Komponenten
Softwaresysteme werden in einzelne Subsysteme zerlegt. Die Zerlegung führt zu mehrstufigen hierarchischen Subsysteme. Diese haben gewisse Unabhängigkeit und interagieren über **wohldefinierte Schnittstellen**. Das Ziel ist einfachere, verständlichere und schnellere Architektur.

* lose Kopplung - via möglichst lose Schnittstellen
* hohe Kohäsion - mit Datenkapselung und Information Hidding

Vorteile dieser hierarchischen Strukturierung sind:

* Präzise Schätz- und Planbarkeit
* Unabhängige Entwicklung möglich
* Einfachere Testbarkeit
* Unabhängiges Deployment
* Potential für Wiederverwendung höher

## Komponenten und (Sub-)Systeme
Komponenten sind softwaretechnische Einheiten welche durch den Einsatz ein System realisiert werden kann. Ein System muss aber nicht zwingend eine Komponente enthalten. Sie sind damit orthogonal

```plantuml
System --> Komponente
```

# Monolithische Architektur
Zu unrecht in Verruf gekommen, es wird zu wenig differenziert.
