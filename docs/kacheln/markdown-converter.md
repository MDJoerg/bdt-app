# Markdown-Konverter

Wandelt verschiedene Quellen in Markdown um: eingefügte Tabellen, Webseiten (auch als
Site-Crawl über mehrere verlinkte Seiten), YouTube-Videos inklusive Playlists (mit Transkript),
Word-Dokumente (.docx) sowie Audio-/Video-Dateien über lokale Transkription.

## Voraussetzungen

- Funktioniert teilweise auch **ohne Projekt** – nur „In Ablage speichern" braucht eines.
- Für Webseiten/YouTube gibst du das Ziel direkt ein; BDT ruft es unmittelbar für dich ab, ohne
  dass dafür ein eingerichteter Endpunkt nötig ist.
- Lokale Audio-/Video-Transkription lädt beim ersten Einsatz ein Spracherkennungsmodell in
  deinen Browser – ein bewusster, einmaliger Download nach deinem Klick.

## Typischer Ablauf

1. Quellenart wählen: Tabelle, Webseite, YouTube, Word-Datei oder Audio/Video.
2. Quelle einfügen, eintippen oder Datei auswählen.
3. Das erzeugte Markdown prüfen und bei Bedarf nachbearbeiten.
4. „In Ablage speichern" (braucht ein Projekt) oder das Ergebnis anderweitig weiterverwenden
   (z. B. kopieren).

## Funktionen im Detail

- **Tabelle:** aus Excel oder einer Webseite kopiert einfügen, oder direkt eine
  Markdown-Tabelle eintippen und weiterbearbeiten.
- **Webseite:** einzelne Seite oder Site-Crawl (folgt Links innerhalb derselben Domain).
- **YouTube:** einzelnes Video oder komplette Playlist, inklusive Transkript, falls verfügbar.
- **Word:** `.docx`-Datei hochladen und in Markdown umwandeln.
- **Audio/Video:** lokale Transkription (Whisper), läuft vollständig in deinem Browser – die
  Datei verlässt dein Gerät dabei nicht.

## Tipps & Grenzen

- YouTube-Transkripte bleiben wegen serverseitiger Bot-Erkennung gelegentlich leer – das ist ein
  ehrlicher Fehlschlag, keine Umgehung wird versucht.
- Ein Site-Crawl kann bei großen Seiten dauern – die Kachel zeigt den Fortschritt und
  gegebenenfalls eine Kappung an, statt eine unvollständige Erfassung zu verschweigen.
