# Clean Core Cockpit

Führt einen echten ATC-Prüflauf (SAPs Standard-Codeprüfung) über einen Paketbaum aus und
bereitet das Ergebnis auf: Dashboard mit Diagrammen, eine sortier-/filterbare Findings-Tabelle,
eine Hub-Sicht mit Migrations-Empfehlungen und ein Explorer zum Durchklicken.

## Voraussetzungen

- Ein eingerichteter SAP-Endpunkt mit ATC-Zugriff.

## Typischer Ablauf

1. Paketbaum und Prüfprofil auswählen (Prüfprofile lassen sich als Vorlage speichern).
2. „Lauf starten" – der ATC-Lauf läuft im System, das Cockpit fragt den Fortschritt ab.
3. Ergebnis in den Reitern durchsehen: Übersicht, Findings, Hub, Verbotene Funktionen,
   Next Best Action, Explorer.
4. Optional „Lauf aufheben" – speichert einen vollständigen Snapshot als Infoobjekt in deiner
   Wissensablage, später jederzeit read-only wieder aufrufbar.
5. Optional einen Markdown-Report erzeugen, inklusive Diagrammen.

## Funktionen im Detail

- **Score:** eine gewichtete Kennzahl aus der Finding-Dichte, als schneller Fortschritts-
  Indikator über mehrere Läufe hinweg.
- **Hub-Tabelle:** zeigt, welche Objekte „Quick Win"-Kandidaten sind (ein einzelner klarer
  Nachfolger).
- **Next Best Action:** ein systemweiter Verwendungsnachweis je Hub-Objekt, um Aufwand
  abzuschätzen.
- **Objekt in ADT öffnen:** ein Link-Versuch in Eclipse/ADT – funktioniert nur, wenn du Eclipse/
  ADT lokal installiert und eine passende Projekt-Verbindung eingerichtet hast.
- **Explorer:** drei Baum-Perspektiven (nach Finding-Typ, nach Objekt, nach Hub-Objekten).

## Tipps & Grenzen

- Ein ATC-Lauf verändert keine Repository-Objekte, legt aber Worklists/Ergebnisse im System an –
  du brauchst also keine Schreibfreigabe für Entwicklungsobjekte.
- Für einen reinen Lookup ohne echten System-Lauf eignet sich der
  [Clean Core Radar](clean-core-radar.md).
