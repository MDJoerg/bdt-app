# News-Quellen

Verwaltet die Quellen, aus denen die dynamischen News-Kacheln in der Launchpad-Gruppe
„Neuigkeiten" gespeist werden: YouTube-Kanäle/-Playlists, RSS-/Atom-Feeds oder beobachtete
Webseiten/Blogs.

## Voraussetzungen

- Ein Projekt.
- Kein SAP-Endpunkt nötig – Quellen werden direkt abgerufen.

## Typischer Ablauf

1. „Neue Quelle" wählen und die Art festlegen: YouTube, RSS-/Atom-Feed oder Webseite.
2. Adresse eintragen (bei YouTube: URL, `@Handle` oder rohe Kanal-/Playlist-Id).
3. Optional Hashtags zur Einordnung vergeben.
4. „Neue Kachel" verknüpft eine oder mehrere Quellen mit einer eigenen Launchpad-News-Kachel.

## Funktionen im Detail

- Mehrere Quellen können sich eine gemeinsame News-Kachel teilen (z. B. mehrere Blogs zu einem
  Thema).
- Neu angelegte News-Kacheln erscheinen automatisch in der Gruppe „Neuigkeiten" im Launchpad.

## Tipps & Grenzen

- Diese Kachel ist reine Konfiguration – das eigentliche Abrufen und Anzeigen der News passiert
  im Launchpad selbst (Karussell je Kachel).
- Manche YouTube-Endpunkte antworten wechselnd – ein einzelner erfolgloser Abruf ist meist kein
  dauerhaftes Problem, ein späterer Versuch klappt oft.
