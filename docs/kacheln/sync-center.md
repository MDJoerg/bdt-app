# Sync-Center

Gleicht die Wissensablage eines Projekts mit einem Ordner auf deinem Rechner ab – zum Beispiel
einem Obsidian-Vault, einem lokalen Git-Repository oder einem OneDrive-Ordner. Jedes Objekt wird
eine Datei: Markdown, Stories, Spezifikationen, Posts, Folien und Mindmaps als lesbarer Text,
alles andere als JSON. Eine solche Einstellung heißt hier „Sync-Verbindung“.

## Voraussetzungen

- Ein Projekt. Kein SAP-Endpunkt nötig.
- Für den Ordner-Abgleich im Browser: Chrome oder Edge (File System Access). Andere Browser können
  nur „Als ZIP herunterladen“ und „Aus ZIP einlesen …“.
- „Lokaler Ordner …“ gibt es nur in VS Code, in der Desktop-App und in der Webapp, die du auf dem
  eigenen Rechner gestartet hast (Aufruf über localhost).

## Typischer Ablauf

1. Im Sync-Center auf **Neue Sync-Verbindung** klicken und Name und Projekt eintragen.
2. Die **Rolle** wählen: „Partner (beide Richtungen)“, „BDT führt (nur in den Ordner schreiben)“
   oder „Ziel führt (nur aus dem Ordner lesen)“.
3. Den Ordner festlegen: **Ordner wählen …** (Browser-Freigabe) oder **Lokaler Ordner …** (lokaler
   BDT-Server). Bei Bedarf **Ordner freigeben**, wenn der Browser die Freigabe vergessen hat.
4. Bereiche und Auslöser ankreuzen, dann **Speichern**.
5. Unter „Abgleich“ **Probelauf** klicken. Die Liste zeigt jeden geplanten Schritt; bei einem
   Konflikt wählst du je Zeile „BDT-Fassung behalten“, „Ordner-Fassung übernehmen“ oder „Beide
   behalten (Kopie)“.
6. **Ausführen** – erst dieser Klick ändert etwas. Das Ergebnis steht danach im **Protokoll**.

## Funktionen im Detail

- **Rollen:** „BDT führt“ schreibt nur in den Ordner (Backup, Export). „Ziel führt“ liest nur aus
  dem Ordner. „Partner“ gleicht in beide Richtungen ab und fragt nur nach, wenn ein Objekt auf
  beiden Seiten geändert wurde.
- **Löschen:** Eine im Ordner gelöschte Datei verschiebt das Objekt nur in den Papierkorb, wenn
  „Papierkorb-Schritte ausführen“ angekreuzt ist. Ein in BDT gelöschtes Objekt entfernt die Datei
  nur mit „Löschungen spiegeln (in BDT gelöscht → Datei löschen)“.
- **Anhänge:** Bilder eines Markdown-Dokuments liegen daneben im Ordner `<dokument>.files/`.
- **Bild-Bibliothek abgleichen (bilder/):** Bilder in beide Richtungen, je Bild eine
  Beschreibungsdatei `.bild.json`. Eine neue Bilddatei im Ordner wird ein neues Bild.
- **Assets und Beziehungen abgleichen (assets/):** Asset-Dateien (`.json` unter `typen/` und
  `instanzen/`, mit Teilmodell-Werten) und `beziehungen.json` in beide Richtungen, auch neue
  Asset-Dateien. Universen, Datenmodelle, Beziehungstypen und Begriffe pflegt BDT. Je Asset
  entsteht ein Steckbrief als `.md`, damit Links in Obsidian ein Ziel haben.
- **Formate ohne Kopfzeilen:** Mermaid (`.mmd`), ZenUML (`.zenuml`), BPMN (`.bpmn`), Stylesheets
  (`.css`) und Metadata Extensions (`.ddlx`) enthalten nur den reinen Inhalt. Name, Schlagworte
  und Ablage stehen in einer Begleitdatei `<datei>.bdt.json` daneben.
- **AGENTS.md für KI-Agenten schreiben:** eine Datei mit Inhaltsverzeichnis und Formaten, damit
  Claude Code, Copilot & Co. die Dateien verstehen. Entfernst du darin die Zeile
  `<!-- bdt:generated -->`, gehört die Datei dir und BDT lässt sie in Ruhe.
- **Auslöser:** „Beim Speichern in den Ordner schreiben“, „Beim Öffnen von BDT abgleichen“ (einmal
  je Browser-Sitzung) und „Intervall“ (5, 15, 30 Minuten oder jede Stunde, solange ein BDT-Tab
  offen ist). Automatisch läuft nur, was die Rolle eindeutig festlegt.
- **ZIP:** „Als ZIP herunterladen“ liefert dieselbe Ordnerstruktur als Datei, ohne den Ordner
  anzufassen. „Aus ZIP einlesen …“ zeigt einen Probelauf und übernimmt danach die Inhalte.
- **Unveränderte zeigen:** blendet im Probelauf auch die Objekte ohne Änderung ein.

## Tipps & Grenzen

- Ordner, Zustand und Protokoll gelten nur für diesen Browser. Ein zweiter Rechner legt eine
  eigene Verbindung zum selben Ordner an.
- Konflikte und Löschungen warten bei automatischen Läufen im Sync-Center auf deine Entscheidung.
- Alle Auslöser brauchen eine erteilte Ordner-Freigabe; ohne Freigabe fragt BDT nicht nach.
- Vertrauliche Objekte verlassen das Gerät nie.
- In Bild-Bibliothek und Assets gibt es keinen Papierkorb: „In BDT löschen“ ist dort endgültig.
- Eigene Schlagworte (`tags`) im Text gelten als Schlagworte. Die Felder `bdt_*` gehören BDT –
  ändere sie nicht von Hand.
- Obsidian legt eingefügte Bilder standardmäßig im Stammordner ab. Solche Bilder erkennt BDT nicht
  als Anhang, nur Dateien in `<datei>.files/`.
- Git selbst (Commit, Push) macht BDT nicht – das erledigst du wie gewohnt im Repository.
