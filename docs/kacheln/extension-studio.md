# Extension-Studio

Sucht Editor-Erweiterungen in öffentlichen Katalogen und lädt die Paketdatei (VSIX) auf deinen
Rechner – für Umgebungen mit eigenem Extension-Store (z. B. code-server) oder gesperrten URLs.

## Voraussetzungen

- Kein Projekt, kein SAP-Endpunkt, kein Secret nötig.
- Browser-Erweiterung: beim ersten Zugriff auf einen Katalog fragt Chrome nach der Berechtigung.
  Reine Webapp: der Microsoft Marketplace erlaubt per CORS keine Suche aus dem Browser – dort
  Local Bridge/Electron/VS-Code-Target nutzen; Open VSX funktioniert immer.

## Typischer Ablauf

1. Typ „VS Code" und Quelle wählen (Microsoft Marketplace oder Open VSX).
2. Suchbegriff oder exakten Bezeichner (`herausgeber.name`) eingeben, **Suchen**.
3. Treffer filtern (Installationen, Plattform, nur verifizierte Herausgeber) und sortieren.
4. Zeile anklicken: Versionen und Plattform-Varianten, **VSIX laden** je Variante.
5. In code-server: `code-server --install-extension <datei>.vsix` (Befehl lässt sich kopieren).

## Funktionen im Detail

- **Trefferliste** mit Name, Bezeichner, neuester Version, Installationen, Bewertung, Verifiziert,
  Aktualisiert, Plattformen und Beschreibung; **Weitere Treffer laden** holt die nächste Seite.
- **Filter:** Mindestzahl an Installationen (ab 1 Tsd., 10 Tsd., 100 Tsd.), Plattform und „Nur
  verifizierte Herausgeber“; Sortierung wählbar (Vorgabe: Installationen).
- **Versionen-Dialog:** je Version die Plattform-Varianten, Pre-Release-Versionen sind markiert.
  „Installationsbefehl kopieren“ liefert den Befehl für code-server.
- **Download-Prüfung:** Der Download wird auf ein echtes VSIX-Paket (ZIP) geprüft; gzip-komprimierte
  Antworten werden entpackt.

## Tipps & Grenzen

- Eine Anfrage geht nur auf Klick an den gewählten Katalog, nie automatisch.
- Wähle für Windows/Linux/macOS die passende Plattform-Variante.
- Lizenz und Nutzungsbedingungen der Erweiterung gelten weiter – prüfe, ob Weitergabe/Offline-Nutzung erlaubt ist.
