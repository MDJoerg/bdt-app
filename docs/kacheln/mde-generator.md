# MDE Generator

Erzeugt aus einer eingefügten CDS View oder einer einfachen Feldliste eine vollständige
Metadata Extension (MDE) für List Report & Object Page – der schnelle Einstieg, wenn du noch
keine MDE hast und nicht bei null anfangen willst.

Technisch dieselbe Kachel wie [MDE Designer](mde-designer.md) („MDE Studio"), nur mit direktem
Einstieg in den Erzeugen-Schritt statt in die Bearbeitung.

## Voraussetzungen

- Kein Projekt und kein SAP-Endpunkt nötig – MDE Studio arbeitet vollständig lokal mit dem
  Text, den du einfügst.

## Typischer Ablauf

1. CDS-View-Quelltext oder eine einfache Feldliste einfügen.
2. Eine vollständige Metadata Extension generieren lassen.
3. Das Ergebnis im [MDE Designer](mde-designer.md) grafisch weiterbearbeiten oder direkt als
   Text übernehmen.

## Funktionen im Detail

- Erkennt Feldnamen automatisch und schlägt eine sinnvolle Grundstruktur vor (Kopf-
  Facette, Line-Item-Feldliste, Selektionsfelder).
- Läuft komplett lokal – kein Quelltext verlässt dein Gerät.

## Tipps & Grenzen

- Das generierte Ergebnis ist ein Startpunkt, keine fertige Lösung – Feinschliff (Wichtigkeiten,
  Facetten-Gruppierung) machst du danach im [MDE Designer](mde-designer.md).
- Bekannte Grenzen: Kopfannotationen außer `@Metadata.layer` gehen beim Einlesen verloren,
  Assoziationen werden übersprungen, und je Feldgruppe/Line-Item wird nur der erste Eintrag
  berücksichtigt.

