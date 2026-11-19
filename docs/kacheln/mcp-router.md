# MCP-Router

Bündelt für ein Kundenprojekt ein Profil aus den verwendeten Tunneln und den MCP-Servern, die
darüber erreichbar sind (z. B. ARC-1 als lokaler Prozess deiner KI-Umgebung). Aus dem Profil
erzeugst du fertige Konfigurationsdateien für Claude Code oder VS Code. Die Kachel richtet sich
an Entwickler, die mehrere MCP-Server gegen SAP-Systeme betreiben.

## Voraussetzungen

- Nur im Expertenmodus sichtbar.
- Ein Projekt; ein Profil gehört immer zum gewählten Projekt.
- Eine laufende Local Bridge (VS Code oder die mitgelieferte Webapp). Ohne Bridge zeigt die Kachel
  einen Hinweis; die Desktop-App hat noch keinen eigenen Tunnel-Listener.
- Ein entsperrter Vault, sobald ein Knoten mit SAP-Anbindung angelegt oder ein Token erneuert wird.
- Für SAP-gebundene Knoten ein SAP-Endpunkt oder ein MCP-Inspector-Profil, das als Tunnel
  freigegeben ist.

## Typischer Ablauf

1. Links **Neues Profil** klicken, Name und optional eine Beschreibung eintragen und
   **Speichern**. Erst danach sind die Abschnitte „Tunnel“ und „Knoten“ nutzbar.
2. Unter „Tunnel“ einen vorhandenen Tunnel auswählen und hinzufügen oder **Tunnel schnell
   anlegen …** (Art „SAP-Endpunkt“ mit Pfad-Präfix oder „MCP ABAP (MCP-Inspector-Profil)“).
3. Unter „Knoten“ **Neuer Knoten …** klicken: Typ wählen, technischen Namen vergeben, Tunnel
   zuordnen, die Felder unter „Katalog-Konfiguration“ prüfen und speichern.
4. Je Knoten über „Konfiguration erzeugen …“ oder für alle Knoten über **Sammelkonfiguration
   erzeugen …** die Datei bauen. Ziel-Client wählen: „Claude Code (.mcp.json)“ oder „VS Code /
   GitHub Copilot (.vscode/mcp.json)“.
5. Datei, „.env“ und Kickstart-Prompt kopieren oder herunterladen und im Projektordner deiner
   KI-Umgebung ablegen.

## Funktionen im Detail

- **Knotentypen aus dem Katalog:** Die wählbaren Typen kommen aus demselben Katalog wie der
  [MCP-Konfigurator](mcp-configurator.md) – eingecheckte Einträge, eigene Projekt- und
  Branding-Einträge sowie freigegebene MCP-Inspector-Profile.
- **Zugänge automatisch:** Jeder SAP-gebundene Knoten bekommt einen eigenen, widerrufbaren
  Tunnel-Zugang. Der Token liegt in einem Sammel-Secret im Vault. Knoten ohne SAP-Anbindung
  brauchen weder Tunnel noch Token.
- **Konfiguration erzeugen:** In der Datei und der „.env“ steht nur der widerrufbare Tunnel-Token,
  nie das SAP-Passwort. Ein Hinweis nennt die Zeilen für die „.gitignore“. Für VS Code zeigt die
  Kachel die Tokens zum Einfügen beim ersten Start, weil VS Code sie abfragt.
- **Kickstart-Prompt:** ein fertiger Text für den Start einer neuen KI-Sitzung.
- **Status & Betrieb:** zeigt je Profil, ob Tunnel gefunden und gestartet sind und ob Zugänge und
  Tokens vorhanden sind. Dazu „Alle Tunnel starten“, „Alle Tunnel stoppen“, „Abgleichen (neu
  erzeugen) …“ und „Alle Tokens neu generieren …“.
- **URL eines Knotens:** Bei Servern mit Adresse ruft BDT die URL nie selbst auf. Sie landet nur in
  der erzeugten Datei.

## Tipps & Grenzen

- Der technische Name muss innerhalb des Profils eindeutig sein; Groß-/Kleinschreibung und
  Sonderzeichen zählen dabei nicht.
- „Alle Tunnel stoppen“ beendet nur Tunnel, die ausschließlich dieses Profil nutzt.
- „Abgleichen“ legt fehlende Zugänge und Tokens neu an, etwa nach dem Wiederherstellen auf einem
  anderen Gerät. Ein fehlender Tunnel selbst muss oben neu zugeordnet werden.
- Tunnel gehören zum Rechner, nicht zum Projekt. Einzelne Tunnel bedienst du weiter in den
  Einstellungen.
- Beim Löschen eines Profils oder Knotens nennt eine Rückfrage, welche Zugänge mit entfernt werden.
- Die „.env“ enthält Zugangsdaten – versioniere sie nicht.
