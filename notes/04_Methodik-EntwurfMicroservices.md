# Methodik / Entwurf und Bau eines Microservice

Wie identifiziere oder entwerfe ich Microservices in einem komplexen System.

## Strukturierung nach technischen Aspekten

Eine Möglichekiten nach Layer/Schichten zu gliedern. Vorteile keine Zyklen bei der Anpassungen eines
Layers.

## Strukturierung nach fachlichen Aspekten

Ziel der strukturierung von Microservices. Wird oft von Business (Fach) definiert und grenzt sich
technisch ab. Die Features werden anhand Silos gegliedert. Zum Beispiel ein Feature Warenkorb.

### Merkmale einer Microservice-Architektur

Es ist **kein** konsistentes Datenmodell über die ganze Applikation notwendig (Eventual Consistency
- braucht Zeit bis Persistenz überall sichergestellt ist). Jeder MS hat eigene fachlichen
Begrifflichkeiten, Datenattribute udn Datentypen. Konzepte wie *Bounded-Context*, welches aus DDD
statmmt. Allfällige Kommunikation zwischen MS müssen Daten-Anpassungen gemacht werden. Die einzelnen
MS kümmern sich selber über ihre Persistierung. Beim richtigen Vorgehen sind MS weitgehend
undabhängig voneinander, fachliche Erweiterung und Wartung werden einfacher. Fachlicher Aufwand kann
minimiert werden um Detail einzelner Teil-Domäne abzugleichen.

### Nachteile einer Mircoservice-Architektur

Grosse technischer Overhead bezüglich technischer Komplexität. Kommunikation generel aufwändig, muss
stabil sein. Sind die MS zu *klein* steigt Kommunikationsbedarf zwischen MS. Dies führt zu mehr
Kopplung, Mehraufwand und kann Performance mindern. Führt zu *Accidental Complexity*.

![Ein pragmatisches Microservice Modell](pragmatischesMS-Modell.png){width=60%}

## Wie indetifiziere ich ein Microservice

Ideal sind Kontextdiagramme. Man erkennt die Abgrenzung zum System (Grenzen). Es enthält auch alle
Akteure und alle Nachrichten zwischen Akteuren und System. Möchlich ist auch ein *Domain-Modell*
und *Bounded-Context*. Sie beinhaltet alle Geschäftsobjekte (Business Entities) und ihre
Beziehungen (Daten und Aktivitäten) unserer Applikation (es fokussiert also auf Daten-Objekte).

![Domain-Modell und Bounded-Context zur Identifikation von Microservices](domain-bounded-context.png)
{width=60%}

## Bounded-Context

Angelehnt an die Methode DDD ist ein abgegrenzter Bereich des Domain-Models, welcher Gültigkeit für
ein bestimmtes **fachliches** Modell hat. Die Domänen bestehen aus mehreren Bounded-Contexts.

## Prozessanalyse

Erst werden alle wesentlichen Prozesse identifiziert und diese in ihre Teilschritte zerlegt. Neben
Prozessschritten werden auch Akteure aufgeführt. Es bewusst einfach gehalten. Es wird meist nur der
Hauptpfad und keine alternativen Pfade erfasst, sonst würde sich BPMN-Notation aufdrängen.

## Event Storming

Ist eine Workshop-basierte Methode um schnell herauszufinden, was in der Domäne eines SW-Programms
passiert. Grundidee ist, SW-Entwickler und Domänenexperten zusammenzubringen und voneinander zu
lernen. Event Storming soll Spass machen.

1. Es wird eruiert, welche Nachrichten oder welche Events auftreten
1. Welcher Befehl führt zum Event
1. Welche Akteure sind daran beteiligt
1. Aggregate aus den Events

Die Elemente werden auf farbige Sticky Notes aufgeschrieben und auf Whiteboard oder Wand geklebt.
Jede Farbe hat eigene Bedeutung.

![Farbenlegende zu Event Storming](event-stormin_stickyNotesFarben.png){width=60%}

Das Ergebnis aus dem Event Storming ist eine farbige Wand :)

![Ergebnis des Event Stormings](resultat-eventStorming.png){width=60%}

## Prozessanalyse

Dank der Prozessanalyse erkennt man zeitliche Zusammenhänge der einzenlen Aktivitäten und
Beziehungen. Ein Ablauf einer Abfolge wird dokumentiert. Bei der Analyse der Prozessschritte wird
klar, dass sich eine Aufteilung in *Bounded-Contexts* aufdrängt. Unterscheiden sich die Zugriffe?
oder die Akteure der einzelnen Aktivitäten.

![Kandidaten für eigene Microservices in der Prozessanalyse\label{candidates}](kandidaten_prozessanalyse.png)
{width=70%}

Man erkennt auf der Abbildung \ref{candidates} mögliche *Bounded-Contexts* wie Stammdaten,
Ausschreibung, Angebotserstellung und Auswahlverfahren.

## Diagramm der MS Architektur in APPE

Wir versuchen mit dem Kontext-Diagramm ein Syste mit Inputs und Outputs zu beschreiben, ohne uns um
die Innereien des Systems zu kümmern. Wir nennen dies **Black-Box-View**.

![Black-Box-View](bbv.png){width=50%}

Daraus kann man die **Komponenten** oder Teilssysteme abbilden.

![Komponenten in APPE](Komponenten-in-APPE.png){width=60%}

### Beispiel einer Microservice Architektur

Nachfolgend eine Beispiel eine Modells einer Microservice Architektur.

![Beispiel einer Microservice Architektur](msa.png){width=60%}

### Datenfluss

Wichtig ist das man den Datenfluss und die Beziehung untereinander korrekt modelliert.

![Basiselemente zur Interaktionsmodellierung](basiselemente.png){width=40%}

![Komplexe Interaktionsmuster](komplexeinteraktionsmuster.png){width=40%}

## Legende

Falls verwendete Symbole für Blöcke, Beziehung oder Interaktion nicht klar ist, muss eine
entsprechende Legende vorhanden sein.
