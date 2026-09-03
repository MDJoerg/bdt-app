# MCP-Konfigurator

Deckt den **tunnellosen** Fall ab: direkte Verbindungen zu MCP-Servern mit Benutzer/Passwort oder
Token, ohne Bridge, in allen Zielumgebungen. Fünf Bereiche über eine Startseite erreichbar:

- **Katalog** – bekannte MCP-Server (ARC-1, AIPC, SAP-ADT-MCP für Eclipse/VS Code, Fiori-/UI5-/
  UI5-Web-Components-MCP, öffentliche SAP Docs) plus eigene und über ein Partner-Branding verteilte
  Einträge. Eingecheckte Einträge lassen sich je Projekt ausblenden, nie löschen; eigene Einträge
  können angelegt/bearbeitet/gelöscht werden. Import/Export über eine Austauschdatei.
- **Server-Konfigurationen** – vorkonfigurierte Bündel mehrerer Katalog-Server mit vorbelegten
  Feldwerten, gedacht für Partner/Kundenverantwortliche, die eine Standard-Ausstattung an andere
  Projekte weitergeben. Eigene Konfigurationen sind editierbar/löschbar, über ein Partner-Branding
  verteilte lassen sich nur ansehen oder als eigene Kopie übernehmen. Import/Export über eine
  eigene Austauschdatei.
- **Generator** – bündelt beliebig viele Server aus dem Katalog (oder auf einmal aus einer
  Server-Konfiguration übernommen) zu einer Projektkonfiguration mit einem gemeinsamen „Kopf"
  (Präfix, System-ID, Mandant, Sprache, URL, Vault-Secrets – einmal ausfüllen oder aus einem
  bestehenden Endpunkt übernehmen) und erzeugt daraus fertige Konfigurationsdateien für zehn
  Ziele: Claude Code, VS Code/GitHub Copilot, Claude Desktop, Cline/Roo Code, Continue, OpenCode,
  Codex CLI, goose, GitHub Copilot für Eclipse und ein generisches „mcpServers"-Austauschformat.
  Jeder Server bekommt automatisch einen eindeutigen Alias; Secret-Strategie wählbar (Platzhalter +
  separate `.env`, Standard, oder Klartext direkt in der Datei mit Warnung).
- **Modell-Zugänge** *(in Vorbereitung)* – Konfigurations-Schnipsel je Coding-Harness aus einem
  bestehenden Endpunkt ableiten.
- **Werkzeuge** *(in Vorbereitung)* – Base64 hin/zurück, Konfigurations-Import/-Konverter.

## Voraussetzungen

- Ein Projekt (Katalogeinträge, Server-Konfigurationen und Projektkonfigurationen werden dort
  gespeichert).
- Für „Aus Endpunkt übernehmen" und die im Vault hinterlegten Secrets: ein entsperrter Vault beim
  Erzeugen der Dateien.

## Typischer Ablauf

1. Im Katalog nach einem passenden MCP-Server suchen oder einen eigenen anlegen.
2. Im Generator eine Projektkonfiguration anlegen: Kopf ausfüllen (oder aus einem bestehenden
   Endpunkt übernehmen), Server aus dem Katalog hinzufügen (oder auf einmal aus einer
   Server-Konfiguration übernehmen).
3. Optional bei jedem Server „Verbindung testen" klicken (zeigt die gemeldete Werkzeugzahl oder
   eine Fehlermeldung; bei einem STDIO-Server nur nach Freischalten des Häkchens
   „STDIO-Verbindungstest im MCP-Konfigurator erlauben" in den Einstellungen unter „Erweiterte
   Verwendung" – jeder Klick zeigt vorher einen Bestätigungsdialog mit dem exakten Befehl, da dabei
   kurzzeitig ein echter lokaler Prozess gestartet wird).
4. Zielumgebung + Secret-Strategie wählen, „Dateien erzeugen" klicken.
5. `mcp.json`/`.env` (bzw. das Ziel-Äquivalent) in deinen Coding Agent übernehmen – auch als ZIP
   in einem Schritt herunterladbar, inkl. eines Kickstart-Prompts für eine neue KI-Sitzung.

## Funktionen im Detail

- Katalogeinträge tragen nie echte Zugangsdaten, nur Platzhalter-Vorlagen.
- Der Kopf der Projektkonfiguration übernimmt Adresse/System-ID/Mandant/Sprache aus einem
  gewählten Endpunkt, ohne dass du sie doppelt pflegen musst – die Secrets bleiben dabei
  Verweise auf den Vault (Regel 7), nie im Klartext gespeichert.
- Jeder Server bekommt automatisch einen Alias (`<Präfix>-<Server>[-<System-ID>][-<Mandant>]`) –
  bei einer Kollision blockiert die Kachel das Speichern/Erzeugen, statt ihn stillschweigend zu
  verändern.
- Ein neu hinzugefügter Server übernimmt Mandant/Sprache, sofern der Katalog-Server das kennt
  (z. B. ARC-1), automatisch aus dem bereits ausgefüllten Kopf statt aus dem starren
  Katalog-Standardwert.
- Zusätzliche, im Katalogeintrag nicht vorgesehene Umgebungsvariablen/Header lassen sich je Server
  frei ergänzen (überschreiben bei Namensgleichheit die Vorlage).

## Tipps & Grenzen

- Enthaltene Zugangsdaten in erzeugten Konfigurationsdateien sind sensibel – behandle sie
  entsprechend vertraulich, besonders bei der Secret-Strategie „Werte einsetzen" (Klartext).
- goose und GitHub Copilot für Eclipse kennen keinen/nur eingeschränkten Platzhaltermechanismus –
  bei goose landen Geheimnis-Namen standardmäßig unter `env_keys` (Schlüsselbund/`goose configure`),
  bei Eclipse stehen Zugangsdaten immer im Klartext in der Datei.
- Für tunnelgebundene Verbindungen (widerrufbarer Token statt SAP-Credential) gibt es die eigene
  Kachel „MCP-Router".
