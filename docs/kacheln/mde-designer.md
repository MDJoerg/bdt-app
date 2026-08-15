# MDE Designer

Bearbeitet eine Metadata Extension (MDE) grafisch – Felder ein-/ausblenden, Line-Item-
Wichtigkeiten setzen, Facetten und deren Feldzuordnung anpassen – statt den MDE/DDLX-Text von
Hand zu editieren.

Technisch dieselbe Kachel wie [MDE Generator](mde-generator.md) („MDE Studio"), nur mit direktem
Einstieg in die Bearbeitung statt in die Neuerzeugung.

## Voraussetzungen

- Kein Projekt und kein SAP-Endpunkt nötig – MDE Studio arbeitet vollständig lokal mit dem
  Text, den du einfügst.

## Typischer Ablauf

1. Bestehenden MDE/DDLX-Quelltext einfügen (oder aus dem [MDE Generator](mde-generator.md)
   übernehmen).
2. Felder, Line-Item-Wichtigkeiten, Selektionsfelder und Facetten grafisch anpassen.
3. Ergebnis als Text zurück exportieren und in dein SAP-System übernehmen.

## Funktionen im Detail

- Roundtrip-sicher für bereits bekannte Annotationen: die ursprüngliche Reihenfolge bleibt
  erhalten, unbekannte Feld-Annotationen gehen beim Bearbeiten nicht verloren.
- Positionen (die 10er-Nummerierung in der MDE) werden automatisch aus der Reihenfolge im
  Editor erzeugt – du musst sie nicht selbst zählen.

## Tipps & Grenzen

- Bekannte Grenzen: Kopfannotationen außer `@Metadata.layer` gehen beim Einlesen verloren,
  Assoziationen werden übersprungen, und je Feldgruppe/Line-Item wird nur der erste Eintrag
  berücksichtigt.
- MDE Studio schreibt nichts automatisch in dein SAP-System – das Übernehmen des Ergebnisses
  machst du selbst.
