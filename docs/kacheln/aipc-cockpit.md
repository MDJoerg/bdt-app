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
- **Pakete:** schnürt Projekte, Dokumente und Referenzen zu einem Paket und spielt es in ein
  anderes System ein – z. B. vom SAP-System in den gehosteten AIPC-Dienst für Schulungen.
  Zwei Umfänge: „Struktur 1:1" (gewählte Projekte inkl. automatisch aufgelöster Referenzen)
  oder „Bootstrap-Klon" (alles, was die KI für ein Projekt sehen würde, als Projekt-Paar aus
  Kontext-Projekt + eigenem Projekt oder als ein flaches Projekt). Das Paket enthält keine
  Zugangsdaten; du kannst es als ZIP herunterladen oder in der Wissensablage aufheben.
  Beim Einspielen zeigt ein Dry-Run vorab, was neu angelegt, aktualisiert, unverändert
  bleibt oder in Konflikt steht (z. B. belegte ScopeId, vorhandenes Dokument mit anderem
  Inhalt). Jedes Dokument bekommt einen Herkunfts-Vermerk, je Zielprojekt entsteht ein
  Steckbrief-Dokument `_PAKET/<id>`. Einspielen braucht „Schreibzugriffe erlaubt" am
  Ziel-Endpunkt.
- **Zeitreise:** im Projekt-Detail der vierte Tab. Zeigt alle Revisionen der Dokumente und
  die Sessions auf einer Zeitachse (Punkte = Revisionen, Bänder = Sessions je Entwickler).
  Wähle einen Zeitpunkt **T** (Schieber, Datumsfeld oder Klick ins Diagramm) – daraus entsteht
  ein Klon des Projekts, wie es zu diesem Zeitpunkt aussah, z. B. als Schulungs-Vorlage.
  „Klon vorbereiten" übergibt ihn an „Pakete" (Ziel wählen, Vorschau berechnen, einspielen).
  Beachte: Welche Session zu welcher Änderung gehört, ist nur eine **Schätzung** (Zeitfenster
  + Entwickler); Status, Titel und Dokumenttyp zu T lassen sich nicht rekonstruieren (es gelten
  die heutigen Werte bzw. „alle veröffentlichen"), und bereits gelöschte Referenzen fehlen.
  Ein Session-Protokoll-Dokument im Klon zeigt, wie der Trainer vorgegangen ist.
- **Pakete für Partner (Neu strukturieren, Versionen):** Im Bereich „Pakete" kannst du zusätzlich
  den Modus **„Neu strukturieren"** wählen: Die Dokumente der gewählten Projekte verteilst du auf
  neue Ziel-Projekte (Vorschlag „wie in der Quelle", „je Dokumenttyp" oder „alles in ein Projekt",
  jede Zeile änderbar; leeres Ziel = Dokument bleibt draußen). Die Referenzen zwischen den neuen
  Projekten leitet BDT aus deiner Zuordnung ab. Ein Paket trägt Name, Version, optional Lizenz/
  Herausgeber; **„Neue Version aus abgelegtem Paket …"** übernimmt Auswahl und Zuordnung des
  Vorgängers und schlägt die nächste Versionsnummer vor.
- **Paket-Vergleich & Roll-out:** Der Bereich beantwortet „was hat sich geändert?" auf drei Wegen –
  Paket ↔ **Live-Quelle**, Paket ↔ **Paket** (z. B. v1.0 gegen v1.1) und Paket ↔ **Zielsystem**
  (**Drift**: dort wurde ein Paketdokument lokal geändert). Geänderte Dokumente zeigen einen
  Zeilenvergleich. Die **Roll-out-Matrix** spielt ein Paket auf mehrere Systeme aus – je System
  mit eigenem Dry-Run und eigener Bestätigung, Präfix/Suffix werden je System gemerkt. Das
  **Drift-Radar** zeigt je System, auf welchem Paketstand es steht (aktuell / Update fällig).
  Vergleiche und Radar sind rein lesend; Ausspielen braucht „Schreibzugriffe erlaubt" am Ziel.
- **Schulungs-Kit:** Für Schulungen legst du aus einem Paket (z. B. dem Template aus der Zeitreise)
  je Teilnehmer einen **eigenen Klon** an (`<Projekt>-<KÜRZEL>`), auf Wunsch auf dem gehosteten
  Dienst ganz ohne SAP-System. Gemeinsamer Kontext (Wissens-Projekte) wird nur einmal angelegt und
  von allen Klonen referenziert; die Klone bekommen keine ScopeId. Ein Dry-Run zeigt vorab, was
  entsteht; das Anlegen ist wiederholbar (spätere Nachzügler bekommen nur ihren Klon). Der
  **Teilnehmer-Vergleich** hält jeden Klon gegen einen Zielstand (z. B. das Trainer-Ergebnis) und
  zeigt Fortschritt, geänderte/fehlende Dokumente (mit Zeilenvergleich) sowie die Session-Aktivität
  je Klon (Anzahl, Dauer, zuletzt aktiv). Die Tabelle kannst du kopieren oder herunterladen.
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
