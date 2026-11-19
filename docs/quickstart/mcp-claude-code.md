# BDT mit Claude fernsteuern (MCP)

BDT kann als MCP-Server arbeiten. Eine KI wie Claude liest und ändert dann deine Assets,
Dokumente, Stories, Whiteboards und UI-Mockups, und du siehst die Änderungen live im Browser.
Alle Bereiche laufen über **ein** Gateway mit **einem** Port und **einem** Zugang.

**Voraussetzungen**

- BDT als VS-Code-Erweiterung oder als Web-App mit Local Bridge. In der reinen
  Chrome-Erweiterung gibt es keinen lokalen Port.
- [Claude Code](https://claude.com/claude-code), also die Kommandozeile oder der Code-Tab der
  Claude-App. Claude Desktop (Chat) geht auch, braucht aber zusätzlich die Brücke `mcp-remote`.
- Das [Musterprojekt „Sascha"](musterprojekt-sascha.md), importiert und in der Fußzeile gewählt.

## 1. Gateway in BDT starten

1. Öffne **Einstellungen → Verbindungen › MCP**, Karte „BDT als MCP-Server (Gateway)".
2. Lass den Port auf **47800** und klicke **Aktivieren**.
3. Klicke **Zugang anlegen**. Ist der Vault entsperrt, wird das Token dort gespeichert und
   bleibt sichtbar.
4. Unter „Bereiche" hat jede Zeile den Knopf **Header-Wert**. Kopier den Wert (`Basic …`). Er
   ist für alle Bereiche gleich.
5. Gib der KI Schreibrechte unter **Einstellungen → MCP → Freigaben**: die Häkchen „KI darf
   … Assets / die Wissensablage / Stories / das Whiteboard / UI-Mockups / Launchpad-Profile …".

## 2. Claude Code einrichten

Am einfachsten über die Kommandozeile mit Scope `user`. Dann landet das Token in keiner
Projektdatei. Ersetze `<HEADER>` durch den kopierten Wert:

```bash
claude mcp add --scope user --transport http bdt-asset http://127.0.0.1:47800/mcp/asset --header "Authorization: <HEADER>"
claude mcp add --scope user --transport http bdt-kb http://127.0.0.1:47800/mcp/kb --header "Authorization: <HEADER>"
claude mcp add --scope user --transport http bdt-story http://127.0.0.1:47800/mcp/story --header "Authorization: <HEADER>"
claude mcp add --scope user --transport http bdt-wb http://127.0.0.1:47800/mcp/wb --header "Authorization: <HEADER>"
claude mcp add --scope user --transport http bdt-uim http://127.0.0.1:47800/mcp/uim --header "Authorization: <HEADER>"
claude mcp add --scope user --transport http bdt-rc http://127.0.0.1:47800/mcp/rc --header "Authorization: <HEADER>"
claude mcp add --scope user --transport http bdt-spec http://127.0.0.1:47800/mcp/spec --header "Authorization: <HEADER>"
```

Alternativ erzeugt die Gateway-Karte unter „Client-Konfiguration" eine fertige Datei, z. B. für
Claude Code, goose oder VS Code. Wähle dort **„Token direkt einsetzen"**. Ohne das Häkchen
enthält die Datei `${VAR}`-Platzhalter, die Claude Code nur aus echten Umgebungsvariablen füllt,
nicht aus einer `.env`-Datei.

Starte danach eine **neue** Claude-Sitzung. Der Befehl `/mcp` sollte die sieben Server `bdt-*` als
verbunden zeigen.

> **Kürzester Weg:** In der Gateway-Karte auf **„Mit KI verbinden (nur Remote Control)"** klicken, die Konfiguration eintragen und der KI den **Startsatz** geben (Knopf daneben). Sie liest dann `rc_briefing` und schaltet weitere Werkzeuge über Profile frei – du bestätigst das in BDT.

## 3. Kanäle öffnen

Ein Bereich antwortet nur, solange seine Kachel offen ist und dort der Knopf
**„Kanal für externe KI"** (Stecker-Symbol) an ist. Am schnellsten geht es direkt in der
Gateway-Karte: **„Kachel öffnen"** in der Zeile des Bereichs öffnet die Kachel in einem neuen Tab,
schaltet dort den Kanal ein und meldet zurück, sobald er offen ist. Die Karte zeigt unter
„Bereiche", welche Kanäle gerade offen sind.

| Server | Kachel |
|---|---|
| `bdt-asset` | Asset-Verwaltung (Universum „Sascha – Headless-Werkzeugkoffer") |
| `bdt-kb` | Wissensablage |
| `bdt-story` | Story-Studio, Sicht „Meine Stories" |
| `bdt-wb` | Whiteboard (mehrere Boards gleichzeitig möglich) |
| `bdt-uim` | UI-Mockup-Studio |
| `bdt-rc` | Launchpad / Remote Control (Stecker-Symbol neben „Profile verwalten") – der feste Einstieg, s. u. |
| `bdt-spec` | Spezifikation-Studio (Liste oder geöffnete Spezifikation) |

> **goose:** Den Zugang unter `headers:` eintragen (`Authorization: Basic …`), nicht als
> Umgebungsvariable (`env_keys`) – sonst schickt goose keinen Header, das Gateway antwortet 401 und
> goose versucht eine OAuth-Anmeldung („Dynamic registration failed").

Mit `bdt-rc` kann Claude die anderen Kacheln selbst öffnen, z. B. „öffne ein neues Whiteboard". Im
Launchpad erscheint dann eine Meldung. Erst dein Klick auf **Öffnen** öffnet den Tab, weil Browser
Fenster ohne Klick blockieren. Der Kanal der geöffneten Kachel schaltet sich dort selbst ein.

## 4. Ausprobieren

Schreibende Änderungen bestätigst du im Browser. Bei Assets, Wissensablage, Stories und Spezifikationen prüft die
KI erst einen Plan und schreibt dann. Whiteboard und UI-Mockups ändern sich sofort und lassen
sich im Browser rückgängig machen.

**Assets: wer führt welche Daten?**

> Welche von Saschas Use Cases laufen über mehrere Systeme, und welches System führt jeweils die
> Datenobjekte?

Claude verfolgt Use Case → Funktion → Modul → System und die Beziehung „führt (Datenhoheit)".
Im Musterprojekt findet es dabei eine echte Modell-Lücke: „Auftrag rückmelden" schreibt einen
Bestand, den EWM führt, ohne Datenübertragung von S/4HANA zu EWM. Lass Claude die Lücke
schließen.

> Lege den Use Case „Ersatzteil per Foto identifizieren" an (Situation ARBEIT, Kanal SPRACHE)
> und verknüpfe ihn so wie Saschas andere Use Cases.

**Wissensablage**

> Fasse die Discover-Ergebnisse zu Sascha zusammen und lege im Ordner „01 Verstehen" ein Dokument
> „Interview-Leitfaden Sascha" mit 8 Fragen an.

**Story-Studio**

> Lies die Sascha-Story und füge eine Szene hinzu, in der er im Transporter per Sprache den
> Fahrzeugbestand prüft. Prüfe sie und zeig mir das Szenenbild.

Fehlt ein passender Hintergrund, kann Claude selbst einen zeichnen, z. B. eine Fahrerkabine.

**Whiteboard** (neues Board öffnen)

> Zeichne Saschas Arbeitstag als Post-its in drei Spalten Arbeit / Pause / Zentrale, verbinde die
> Schritte mit Pfeilen, rahme jede Spalte und zeig mir das Ergebnis als Bild.

Claude legt alle Post-its und Pfeile mit einem einzigen Aufruf (`wb_add_many`) an und kann dem
Board einen Namen geben (`wb_set_name`). Gespeichert ist das Board erst, wenn du im Browser auf
„Speichern" klickst.

**UI-Mockup-Studio**

> Entwirf für Saschas Büro-Laptop eine Worklist „Meine Serviceaufträge heute" mit Object Page,
> fülle Beispieldaten aus den Assets und prüfe das Mockup gegen die Fiori-Richtlinien.

**Über mehrere Bereiche**

> Lies die systemübergreifenden Use Cases aus den Assets und zeichne daraus eine Systemlandkarte
> aufs Whiteboard: Systeme als Rahmen, Use Cases als Post-its.

## Ein Server für mehrere Bereiche (Gateway-Profil)

Statt je Bereich einen Server einzutragen, kannst du unter **Einstellungen → MCP → Profile** ein
Gateway-Profil anlegen, z. B. „Sascha" mit Launchpad, Wissensablage und Story-Studio. Je Bereich
wählst du „alle Werkzeuge" oder einzelne Werkzeuge („Nur lesende ankreuzen" hilft beim Ausprobieren).
In Claude Code steht dann nur noch ein Eintrag mit der URL `…/mcp/p/<kurzname>`; die fertige
Konfiguration kopierst du direkt aus dem Reiter. Werkzeuge außerhalb des Profils sieht die KI nicht.
Die Kacheln der Bereiche müssen wie gewohnt mit eingeschaltetem Kanal offen sein – der Reiter zeigt je
Bereich „offen" oder „nicht offen" und hat einen Knopf zum Öffnen.

## Jede Aktion bestätigen

Wer genau sehen will, was die KI tut, schaltet unter **Einstellungen → MCP → Freigaben** das Häkchen
„Jede Aktion der KI bestätigen" ein. Dann fragt der Kachel-Tab vor jedem Werkzeug-Aufruf nach und zeigt
Bereich, Werkzeug und Argumente. Du kannst einmal erlauben, eine Regel anlegen (z. B. „alles Lesende für
diese Sitzung") oder ablehnen. Eine Regel gilt für die Sitzung (dieser Tab), für alle Tabs bis du den
Browser schließt („Kachel"), für ein Gateway-Profil oder immer. Gespeicherte Regeln widerrufst du im
selben Reiter. Liegt der Tab im Hintergrund, steht in seinem Titel „⚠ Freigabe nötig".

Im selben Reiter kannst du je Bereich „Änderungen ohne Vorschau schreiben" ankreuzen. Dann entfällt
der Änderungsdialog beim Schreiben; das Freigabe-Popup davor bleibt. Das geht nur im Experten-Modus.

Fertige Eingaben zum Ausprobieren liegen im Musterprojekt im Architektur-Studio auf dem Sheet
„MCP Beispiele".

## Was hat die KI gemacht?

Unter **Einstellungen → MCP → Verlauf** steht jeder Werkzeug-Aufruf der KI: welches Werkzeug, mit
welchem Ergebnis, ob du ihn erlaubt oder abgelehnt hast (und durch welche Regel), über welchen Zugang
und welches Profil. Fährst du mit der Maus über eine Zeile, siehst du die Argumente. In einer Kachel
mit eingeschaltetem Kanal öffnet der Kanal-Knopf ein Menü mit dem Verlauf dieses Tabs. Der Verlauf
gilt, bis die Bridge neu startet.

## Wenn etwas nicht klappt

| Symptom | Ursache und Abhilfe |
|---|---|
| `/mcp` zeigt einen Server als getrennt | Gateway gestoppt oder falscher Header-Wert. Gateway-Karte prüfen, Header neu kopieren. |
| Antwort „Kein … geöffnet" | Die Kachel ist zu oder ihr Kanal ist aus. Kachel öffnen, Stecker-Knopf einschalten. |
| Schreiben wird abgelehnt | Häkchen unter „Erweiterte Verwendung" fehlt, oder die Bestätigung im Browser wurde nicht geklickt. |
| Daten aus dem falschen Projekt | In der Kachel unten das richtige Projekt wählen und den Kanal neu einschalten. |

## Den MCP Simulator testen

Der Simulator „Werkzeugkoffer" läuft nicht über das Gateway. Er bildet die geplanten Werkzeuge
für Sascha nach (Auftrag lesen, Bestand prüfen, Material reservieren …) und antwortet mit den
Daten aus den Assets. Öffne im MCP Simulator den Reiter **„Veröffentlichen"**. Dort bekommst du
eine eigene Adresse und eine eigene Client-Konfiguration.
