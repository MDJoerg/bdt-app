# BDT – Business Daily Tools

Kostenlose Werkzeugsammlung im Fiori-Launchpad-Stil für die tägliche Arbeit mit
SAP-Entwicklung (CDS, RAP, Fiori Elements, ADT, OData) – herausgegeben von
**Brandeis Consulting**.

Keine Telemetrie, keine Anfragen an Dritte: Netzwerkzugriffe erfolgen ausschließlich auf
selbst konfigurierte SAP-/KI-Endpunkte, jeweils durch eine eigene Aktion ausgelöst.

📖 **Anwenderdokumentation:** <https://mdjoerg.github.io/bdt-app/> – Einstieg, jede Kachel
im Detail, FAQ, Experten-Themen. Dieselbe Doku ist auch direkt in der App über die Kachel
„Hilfe" verfügbar.

## Download & Installation

Die aktuellen Pakete liegen auf der [Releases-Seite](https://github.com/MDJoerg/bdt-app/releases).
Jedes Release liefert Dateien für drei Varianten – wähl die passende:

| Datei | Variante | Für wen |
|---|---|---|
| `bdt-<kanal>-chrome-<version>.crx` | Chrome/Edge, installierbar | die meisten – eine Datei installieren |
| `bdt-<kanal>-chrome-<version>.zip` | Chrome/Edge, entpackt laden | wenn die Firmen-Policy `.crx`-Dateien blockiert |
| `bdt-<kanal>-electron-win-<version>.zip` | Windows-Desktop-App | volle SAP-Anbindung ohne Browser-CORS-Hürden |
| `bdt-<kanal>-vscode-<version>.vsix` | VS-Code-Extension | Entwickler:innen, die in VS Code bleiben wollen |

`<kanal>` steht für die Ausgabestufe (`preview` / `alpha` / `beta` / `final`) – bei jedem
Release steht auf GitHub, welcher Kanal es ist. Wer volle SAP-Funktion ohne
CORS-Einschränkungen möchte, greift zur Desktop-App (Variante c).

### a) CRX installieren (Chrome/Edge)

1. `chrome://extensions` (bzw. `edge://extensions`) öffnen, **Entwicklermodus** einschalten.
2. Die `.crx`-Datei per Drag & Drop auf diese Seite ziehen, Installation bestätigen.

Chrome markiert Erweiterungen außerhalb des Web Stores als „nicht verifiziert" – für die
hier veröffentlichten Pakete unbedenklich. In firmenverwalteten Chrome-Installationen ist
die Installation teils per Policy blockiert – dann Variante b) nutzen.

### b) ZIP entpackt laden (Chrome/Edge)

1. ZIP in einen **dauerhaften** Ordner entpacken (nicht in „Downloads" liegen lassen – wird
   der Ordner gelöscht/verschoben, ist die Erweiterung weg).
2. `chrome://extensions` → Entwicklermodus → **„Entpackte Erweiterung laden"** → den
   entpackten Ordner wählen.

### c) Windows-Desktop-App

1. ZIP entpacken, `business-daily-tools.exe` doppelklicken – keine Installation nötig.
2. SmartScreen-Warnung beim ersten Start (die App ist noch nicht code-signiert):
   „Weitere Informationen" → „Trotzdem ausführen".

### d) VS-Code-Extension

```bash
code --install-extension bdt-<kanal>-vscode-<version>.vsix
```

(Alternativ in VS Code: Extensions-Ansicht → `···`-Menü → „Install from VSIX…".) Danach über
die Befehlspalette (F1): **„Business Daily Tools: Im Editor öffnen"** oder **„… Im Browser
öffnen"**.

## Updates

Eine neue Version einfach über die alte installieren: Chrome-Extension per Drag & Drop der
neuen `.crx` (gleicher Signierschlüssel → Update statt Zweitinstallation), bei Desktop-App
und VS-Code-Extension die neue Datei über die alte entpacken/installieren. Ein
„Nach Updates suchen"-Button direkt in der App ist geplant.

## Web-App

Eine im Browser laufende Variante ganz ohne Installation ist als eigenständiges Deployment
in Vorbereitung – Details dazu in der Anwenderdokumentation, Kapitel „Web-App-Betrieb".

## Feedback

Einen Fehler gefunden oder eine Idee? → [Issues](https://github.com/MDJoerg/bdt-app/issues)

## Rechtliches

„SAP", „ABAP" und „Fiori" sind Marken der SAP SE; Erwähnungen in diesem Repo sind rein
beschreibend. BDT steht in keiner Verbindung zur SAP SE und wird nicht von ihr unterstützt.

Herausgeber: [Brandeis Consulting](https://www.brandeis.de)
