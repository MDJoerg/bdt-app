# Clean Core Radar

Prüft, ob ein SAP-Objekt „Clean Core"-fähig ist – also ohne bekannte, aus SAP-Sicht kritische
Modifikationen/veraltete Techniken auskommt. Dafür importierst du eine SAP-
Cloudification-Repository-Datenbasis; einen einzelnen Objekt-Lookup darin brauchst du dafür
keinen SAP-Endpunkt. Eine echte Paket-Analyse gegen ein reales System (dritter Reiter) braucht
zusätzlich einen Endpunkt.

## Voraussetzungen

- Eine importierte SAP-Cloudification-Repository-Datenbasis (Reiter „Datenbasis").
- Für die Paket-Analyse zusätzlich ein eingerichteter SAP-Endpunkt.

## Typischer Ablauf

1. Im Reiter „Datenbasis" eine oder mehrere Cloudification-Dateien importieren.
2. Im Reiter „Suche" ein einzelnes Objekt nachschlagen – ganz ohne Endpunkt.
3. Im Reiter „Paket-Analyse" (mit Endpunkt) einen Paketbaum wählen und gegen die Datenbasis
   abgleichen – Ergebnis als Hub-Tabelle.
4. Optional „Als RAP-Schichten-Graph anzeigen" für eine visuelle Übersicht.

## Funktionen im Detail

- Die Hub-Tabelle zeigt Objekte, die von vielen anderen genutzt werden – ein guter Ausgangspunkt
  für Migrationsentscheidungen.
- Der RAP-Schichten-Graph zeigt Abhängigkeiten zwischen den Objekten eines Pakets.

## Tipps & Grenzen

- Die Paket-Analyse nutzt eine Text-Heuristik für Klassen/Programme/Interfaces (nicht 100 %
  präzise), CDS-View-Abhängigkeiten werden deterministisch erkannt.
- Für einen echten ATC-Prüflauf (Findings statt reinem Lookup) nutze das
  [Clean Core Cockpit](clean-core-cockpit.md).
