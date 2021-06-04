# Anforderungsdiagramme und Modelle

Diagramme sind klarer Verständlich als Worte, weshalb sie häufig eingesetzt werden. Es gibt
zahlreiche unterschiedliche Arten von Diagramme. Die Methoden/Techniken unterscheiden sich, um
Anforderungen zu erheben, festzuhalten und zu analysieren.

## Domain Modell

Soll die Fachdomäne/Anwendungsdomäne. Enthält Daten und Entitäten und deren Beziehungen. Das Naming
sollte aussagekräftig und eindeutig sein. Ein Domain-Model ist ein konzeptionelles Modell der
Anwendungsdomäne und beinhaltet sowohl Verhalten als auch Daten. Es wird typischerweise als
UML-Diagramm erstellt.

### Ist-/Hat Beziehung

Komposition ist eine Ist-Beziehung -> Ein Raum ist in einem Gebäude. Ein Gebäude besteht aus 1 bis
$n$ Räumen.

Eine Aggregation ist eine Hat-Beziehung -> Ein Student hat Vorlesungen. Eine Vorlesung enthält 3 bis
$n$ Studenten. Die Komposistion wird mit einem ausgefüllten schwarzen Diamond gekennzeichnet. Die
Aggregation mit einem weissen. Ein weisser Pfeil heisst, eine Entität *hat* die Entität worauf
gezeigt wird.

## Kontext Diagramm

In einem Kontext Diagramm sehen wir das System mit seinen Grenzen mit allen Akteuren und
Nachrichten (Datenfluss) zwischen Akteur und System. Das Diagramm dient der Systemabgrenzungen.

## Use Case / Anwendungsfall Diagramm

Beschreibt einen Anwendungsfall, welcher durch unterschiedliche Szenarien eintreten können. Darin
werden alle Use Cases und die Verbindungen zu den Akteuren aufgezeigt. Die Pfeile sollten gerichtet
werden um zu erkennen, wer den Use Case anstösst.

## Geschäftsprozess Modell

Die Struktur bzw. der Prozess wird modelliert, was passiert wann genau. In welcher Struktur und
Reihenfolge. Entspricht BPNM.

## Feature Liste

Zeigt auf welche Features es überhaupt gibt und welche Kundengruppen diese verwenden können. Kann
auch über einen Status Auskunft geben (Fertig, in Arbeit, geplant).

