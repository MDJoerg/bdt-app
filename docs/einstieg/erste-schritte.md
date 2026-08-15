# Erste Schritte

## Installieren

Wie du BDT installierst, hängt davon ab, welche Variante du nutzen willst – alle vier sind
funktional gleichwertig (Details: [Deployment-Varianten](../experten/deployment.md)):

- **Chrome-Erweiterung:** Datei aus den Releases herunterladen, unter `chrome://extensions` den
  Entwicklermodus einschalten und die entpackte Erweiterung laden (bis ein Store-Eintrag
  existiert), oder die CRX-Datei direkt installieren.
- **VS-Code-Erweiterung:** die VSIX-Datei herunterladen, in VS Code über „Aus VSIX installieren…"
  einspielen.
- **Desktop-App (Windows):** das ZIP-Archiv entpacken und `BDT.exe` starten – kein Installer
  nötig (portable App).
- **Web-App:** die von dir/deiner Organisation gehostete URL im Browser öffnen. Für den
  Offline-Zugriff und ein eigenes App-Icon kannst du sie über das Browser-Menü „Installieren"
  als PWA einrichten.

## Das erste Projekt anlegen

1. Öffne das Launchpad – das ist die Startseite von BDT.
2. Klicke auf das Zahnrad-Symbol (Einstellungen) in der Kopfzeile.
3. Gehe zu „Projekte" → „Neues Projekt" → gib einen Namen ein → speichern.
4. Wähle das neue Projekt unten in der Fußzeile aus (falls es nicht schon automatisch aktiv ist.)

Jetzt kannst du direkt loslegen – vieles funktioniert ganz ohne weitere Einrichtung, z. B. die
Wissensablage oder die Kreativ-Editoren (Whiteboard, Markdown-Editor, Mermaid-Editor, …).

## Einen Endpunkt einrichten (optional)

Nur nötig, wenn du eine Kachel nutzen willst, die mit einem SAP-System, einem KI-Anbieter oder
einem anderen externen Dienst spricht (z. B. Repository-Suche, CDS Explorer, KI-Chat mit einem
eigenen KI-Provider).

1. Einstellungen → „Endpunkte" → „Neuer Endpunkt".
2. Typ wählen (z. B. „SAP ABAP System"), URL eintragen.
3. Anmeldeart wählen und ggf. Zugangsdaten hinterlegen – die landen automatisch verschlüsselt im
   Vault; du wirst beim ersten Mal gebeten, ein Master-Passwort für den Vault zu vergeben.
4. Speichern, dann mit „Verbindung testen" prüfen, ob es klappt.
5. In der jeweiligen Kachel unten in der Fußzeile den Endpunkt auswählen.

## Weiter geht's

- Schau dir die [Tipps](tipps.md) an – Favoriten, Profile, Dark Mode und mehr.
- Wenn dir das Launchpad zu voll vorkommt: Einstellungen → „Launchpad-Gruppen" → Regler
  „Kacheln – Sichtbarkeit" auf „Fokus" stellen. Dann siehst du zunächst nur eine kleine,
  kuratierte Auswahl und kannst dich Schritt für Schritt zu „Standard" oder „Experte" vorarbeiten.
- Bei Fragen: [FAQ](../faq.md).
