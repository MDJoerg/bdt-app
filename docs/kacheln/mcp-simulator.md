# MCP Simulator

Hier definierst du einen **eigenen MCP-Server**, bevor es eine Implementierung gibt – und probierst
ihn gleich mit Daten aus deinem Projekt aus. Am Ende lädst du die Definition als Spezifikation
herunter und gibst sie an die Entwicklung (oder eine KI) weiter.

## Voraussetzungen

- Ein Projekt (die Simulatoren liegen in der Wissensablage).
- Für Daten: ein Asset-Universum, ein Dataset im Daten-Studio oder Inhalte in der Wissensablage.
  Ohne Daten kannst du Tools trotzdem als reinen Vertrag anlegen („Echo" oder „Fester Text").
- Kein SAP-Endpunkt, kein Netzwerk.

## Ablauf

1. **Neu**, **Beispiel anlegen** oder **Importieren …** in der Liste.
2. Reiter **Server**: technischer Name, Titel, Version, Hinweise für Clients.
3. Reiter **Tools**: je Tool Name, Beschreibung, Parameter (Zeile für Zeile oder als JSON) und die
   **Datenbindung** – Assets auflisten/lesen/Beziehungen, Dataset abfragen/Zeile lesen, Wissensablage
   durchsuchen/Objekt lesen, fester Text oder Echo. Filter können einen festen Wert oder einen Parameter
   verwenden; bleibt der Parameter leer, entfällt der Filter.
4. Reiter **Ressourcen** und **Prompts**: feste Ressourcen, Ressourcen-Vorlagen mit `{Variable}` und
   Prompt-Vorlagen mit `{{Argument}}`.
5. Reiter **Probe**: Tool, Ressource oder Prompt aufrufen – oder eine rohe JSON-RPC-Anfrage schicken.
   Gelungene Aufrufe lassen sich als Beispiel aufzeichnen.
6. Reiter **Spec**: Dateien herunterladen oder den KI-Prompt kopieren.

## Funktionen im Detail

- **spec.json** – der Vertrag: genau die Antworten von `tools/list`, `resources/list`,
  `resources/templates/list` und `prompts/list`, ohne die Datenbindung.
- **server.json** – Eintrag im Format der offiziellen MCP-Registry; die URL bleibt Platzhalter.
- **SPEC.md** – lesbare Beschreibung mit Parametertabellen und aufgezeichneten Beispielen; lässt sich
  direkt als Kontext an den KI-Chat geben.
- **bdt-mcp-sim.json** – die vollständige Definition samt Bindungen zum Wiedereinlesen.
- **Import** – KI-Antwort, eine eingefügte `tools/list`-Antwort (z. B. aus dem MCP-Inspector) oder eine
  `bdt-mcp-sim.json`. Importierte Tools antworten zunächst mit „Echo".
- **Prüfung** im Reiter „Server": doppelte oder ungültige Namen, Pflichtparameter ohne Definition,
  Tools ohne Datenquelle.

## Tipps & Grenzen

- Parameter werden nur in einer Teilmenge von JSON Schema geprüft (Typ, Pflicht, Werteliste, Bereich).
- Antworten sind auf höchstens 200 Zeilen begrenzt (einstellbar je Tool); Kappungen werden angezeigt.
- Die Wissensablage wird in dieser Fassung per Textsuche durchsucht, nicht per Vektorsuche.
- **Nutzen außerhalb der Kachel:** Im KI-Chat steht dein Simulator in der MCP-Auswahl („Simulator: …“) und
  bei den Agenten; im MCP-Inspector verbindest du ihn über „Simulator verbinden …“ und siehst die
  JSON-RPC-Nachrichten im Protokoll; im KI-Testcenter wählst du ihn bei einem MCP-Testfall als Profil.
  Im MCP-Konfigurator erscheint er im Katalog (Herkunft „MCP Simulator“), aber noch nicht im Generator.
- **Für externe Clients veröffentlichen** (Reiter „Veröffentlichen", nur in der Web-App und in VS Code):
  Port wählen, „Veröffentlichen", dann je Client einen Zugang anlegen. Das Token siehst du nur direkt
  danach – kopiere gleich die Client-Konfiguration (LM Studio/Claude Code, VS Code, Claude Desktop …).
  Der Client erreicht den Simulator unter `http://127.0.0.1:<Port>/mcp`. Geantwortet wird mit den
  aktuellen Projektdaten aus deinem offenen Tab; schließt du ihn, meldet der Client „Simulator nicht
  erreichbar". Beim Wiederöffnen auf „Mit dieser Seite verbinden" klicken.
- **Echten Server prüfen** (Reiter „Prüfen"): Server wählen – ein MCP-Inspector-Profil, eine URL
  (optional mit Bearer-Token oder Benutzer/Passwort, wird nicht gespeichert) oder einen anderen
  Simulator. „Prüfen" vergleicht die Tools, Ressourcen und Prompts des Servers mit deiner Spezifikation
  und zeigt Fehler, Warnungen und Hinweise. Danach kannst du die aufgezeichneten Beispiele am Server
  aufrufen: lesend gekennzeichnete Tools direkt, alle anderen nur nach Rückfrage.
- **Skript-Bindung:** reichen Filter nicht, wählst du als Art „Skript (JavaScript, Sandbox)". Du schreibst
  den Rumpf einer Funktion mit `args` (Argumente) und `data` (Zeilen der gewählten Datenquelle) und gibst
  Text, eine Liste oder ein Objekt zurück, z. B. `return data.filter((r) => r.country === args.country);`.
  Das Skript läuft abgeschottet (kein Netz, kein Zugriff auf gespeicherte Daten, Zeitlimit) und erst, wenn du
  in den Einstellungen unter „Erweiterte Verwendung" das Häkchen „MCP Simulator: Skripte ausführen" setzt.
  `console.log` erscheint in der Probe unter `_meta.scriptLogs`.
- **ABAP-Gerüst erzeugen** (Reiter „Spec"): für das ABAP-MCP-SDK abap-ai/mcp2. Du gibst ein Präfix an
  (Vorschlag `ZBDT_MCP2_`), prüfst die vorgeschlagenen Namen für Klasse, Interface und Paket und erzeugst
  ein Interface mit allen Tool- und Parameternamen und Texten, eine Serverklasse mit dem Schema und je Tool
  einer Methode, die ein Entwickler (oder eine KI) nur noch ausprägt, und auf Wunsch Tests aus den
  aufgezeichneten Beispielen. Jede Datei lässt sich kopieren, alles zusammen als abapGit-ZIP laden. Das
  README im ZIP nennt den Eintrag für `ZMCP2_SERVERS` und wie du den fertigen Server in BDT prüfst.
  Mit **„mit API-Schicht“** entstehen zusätzlich ein API-Interface, eine Backend-Klasse und eine
  Factory: die Serverklasse liest dann nur die Argumente und formt die Antwort, die Daten kommen aus der
  API-Schicht. Die Tests laufen gegen einen Stub, die API-Schicht lässt sich auch für OData/Fiori nutzen.
- **Für KI: ABAP-Implementierung bauen** (Reiter „Spec"): statt selbst auszuprägen, gibst du den Bau an eine
  KI. Der Dialog zeigt den fertigen Auftrag: Namen, Regeln für mcp2, alle Tools mit Parametern und Beispielen,
  den Vertrag `spec.json` und auf Wunsch das Gerüst. Du kopierst ihn, gibst ihn an den KI-Chat oder lädst
  ein Kontext-Paket (ZIP) für KI-Werkzeuge mit Dateizugriff. Zeichne vorher im Reiter „Probe" Beispiele
  auf, sonst fehlen der KI Muster-Antworten.
- **Spezifikation anlegen** (Reiter „Spec"): legt im Spezifikation-Studio eine an diesen Simulator
  gebundene Spezifikation an – jedes aufgezeichnete Beispiel wird ein Szenario, das du dort gegen den
  Simulator und später gegen den echten Server abspielst.
- **LM Studio:** Ziel „Claude Code (.mcp.json)" wählen und den Eintrag unter `mcpServers` in
  LM Studios `mcp.json` übernehmen (`url` und `headers`, `type` darf mit). Im Chat den Server
  aktivieren und ein Modell mit Tool-Unterstützung wählen.
