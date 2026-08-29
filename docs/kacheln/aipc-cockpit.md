# AIPC Cockpit

Die Governance-Sicht auf „AI Project Context" (AIPC) – ein SAP-Backend, das Projektkontext
(Spezifikationen, Architektur-Entscheidungen, Findings, Guides) als versionierte Dokumente
speichert, damit KI-Coding-Werkzeuge damit arbeiten können. Das Cockpit zeigt Projekte,
Dokumente und Referenzen, erlaubt gezielte Pflege und beantwortet die Frage „was sieht die KI?".

## Voraussetzungen

- Ein SAP-Endpunkt auf dem System, auf dem AIPC installiert ist.
- Schreibende Aktionen (Projekte anlegen, Dokumente pflegen, Status ändern) nur, wenn am
  Endpunkt „Schreibzugriffe erlaubt" aktiviert ist – sonst bleibt alles rein lesend.

## Typischer Ablauf

1. Auf der Startseite den Bereich nach Zielgruppe wählen (Allgemein/Systembetreuer/
   Entwickler/Partner) – z. B. „Projekte, Dokumente & Referenzen".
2. Im Filter-Kopfbereich (einklapp- und pinnbar, wie in Fiori-Anwendungen) filtern und
   „Projekte laden" drücken.
3. Links im Baum navigieren – der Baum und der Detailbereich rechts scrollen unabhängig
   voneinander; das Filterfeld über dem Baum grenzt auch bereits nachgeladene Dokumente
   und Referenzen ein.
4. Ein Projekt anklicken: rechts erscheinen die Kopfinformationen mit drei Reitern –
   **Session-Aktivität** (wer hat wann wie lange mit KI an diesem Projekt gearbeitet),
   **Projekt-Kontext** (Dokumente nach Typ/Status, Referenzen nach Art des Zielprojekts,
   Revisions-Aktivität im Zeitverlauf) und **Dokumente** (sortier-/filterbare Tabelle).
5. Die Baumknoten „Dokumente", ein Dokumenttyp (z. B. „ADR") und „Referenzen" zeigen
   dieselben Tabellen – komplett, nach Typ gefiltert bzw. als Referenz-Liste.

## Funktionen im Detail

- **Briefing-Vorschau:** zeigt, welchen Kontext eine KI-Session für ein Projekt bekäme –
  inklusive über Referenzen geerbter Dokumente; mit Update-Diff und Kontext-Export (ZIP).
- **Richtlinien-Import:** Word-Datei, Webseite oder Markdown-Dateien in Abschnitte zerlegen
  und als AIPC-Dokumente schreiben – immer mit Vorschau (Dry-Run) vor dem Schreiben.
- **Wissensablage-Sync:** spiegelt den Briefing-Bestand als Markdown-Infoobjekte in deine
  Wissensablage (durchsuchbar über die Kachel „Suche", rein lesend gegenüber AIPC).
- **Governance-Dashboard + ISSUE-Inbox:** projektübergreifende Kennzahlen und offene Issues
  mit Annehmen/Ablehnen.
- **Entwickler-Onboarding:** fertige MCP-Konfigurationen für gängige KI-Coding-Werkzeuge,
  plus ein Kickstart-Prompt für die erste KI-Sitzung.
- **Meldungen:** Ergebnis- und Fehlermeldungen erscheinen unten links über der Fußzeile und
  verschwinden nach ein paar Sekunden von selbst; ein Klick auf eine Meldung zeigt Details
  (auch für Support-Zwecke, mit Kopieren/Download), das Symbol ganz links in der Fußzeile
  öffnet die Historie der letzten Meldungen.

## Tipps & Grenzen

- Dokumente/Referenzen eines Projekts werden erst beim Aufklappen bzw. Anklicken geladen –
  das hält den ersten Ladevorgang schnell.
- Nur Dokumente, die „Verbindlich" markiert UND veröffentlicht (Status „Aktiv") sind,
  fließen tatsächlich in das KI-Briefing ein.
- Referenzierte Inhalte anderer Projekte sind im Baum sichtbar, aber nur zur Ansicht –
  bearbeitet wird immer im Quellprojekt.
- Anzeigedauer und Historien-Größe der Meldungen sind in den Einstellungen (Bereich
  „Launchpad-Gruppen" → „Meldungen") einstellbar.
