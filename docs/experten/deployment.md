# Deployment-Varianten

BDT liefert dieselbe Anwendung in vier Zielumgebungen aus (BDT nennt sie intern „Targets"). Die
sichtbaren Werkzeuge sind überall gleich – die Unterschiede liegen darin, **wie** BDT mit einem
SAP-System oder einem anderen externen Dienst spricht.

## Die vier Varianten im Überblick

| Variante | Wie du sie startest | Zugriff auf SAP-/HTTP-Endpunkte |
|---|---|---|
| **Chrome-Erweiterung** | Entpackte Erweiterung laden oder CRX installieren | Direkt aus dem Browser, per Chrome-Berechtigung je Host |
| **VS-Code-Erweiterung (VSIX)** | „Aus VSIX installieren…" in VS Code | Über die eingebaute „Local Bridge" |
| **Desktop-App (Windows)** | Portables ZIP entpacken, `BDT.exe` starten | Über die Local Bridge bzw. direkt (Electron) |
| **Web-App / PWA** | URL im Browser öffnen, optional als PWA installieren | Direkt aus dem Browser – **außer** eine Local Bridge läuft mitgeliefert |

## Warum das einen Unterschied macht

Browser blockieren aus Sicherheitsgründen Anfragen an fremde Server von einer Seite, die auf
einem anderen Origin läuft (CORS). Eine Chrome-Erweiterung bekommt dafür eine explizite
Host-Berechtigung – du erlaubst den Zugriff auf dein SAP-System einmalig mit einem Klick.

VS Code, die Desktop-App und (wenn passend konfiguriert) die Web-App nutzen stattdessen eine
**„Local Bridge"**: einen kleinen, lokal mitlaufenden Baustein, der Anfragen im Namen von BDT
weiterreicht – ohne CORS-Problem, und mit Unterstützung für Windows-Anmeldung (SPNEGO) oder eine
Anmeldung im Browser (SSO/SAML, z. B. Entra ID), falls dein SAP-System das verlangt.

Eine reine Web-App ohne Local Bridge kann trotzdem direkt auf Endpunkte zugreifen, die selbst
CORS erlauben (z. B. viele KI-Anbieter) – für ein SAP-System brauchst du dort in der Regel eine
Local Bridge oder einen entsprechend konfigurierten Reverse-Proxy.

## Was bei jeder Variante gleich bleibt

- Deine Daten (Projekte, Wissensablage, Einstellungen) liegen lokal in deinem Browser bzw. auf
  deinem Rechner – unabhängig von der Variante.
- Zugangsdaten liegen immer verschlüsselt im Vault, nie im Klartext.
- Ein Netzwerkzugriff passiert nur, wenn du ihn auslöst, und nur an selbst konfigurierte
  Endpunkte.

## Updates

Eine neue Version installierst du wie beim Erstinstallieren (neue Datei herunterladen, erneut
laden/installieren). BDT prüft nicht automatisch im Hintergrund auf neuere Versionen – ein
manueller „Nach Updates suchen"-Knopf ist in Vorbereitung.
