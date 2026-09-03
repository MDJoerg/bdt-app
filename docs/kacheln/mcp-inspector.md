# MCP-Inspector

Verbindet sich mit einem MCP-Server und lässt dich dessen Werkzeuge, Ressourcen und Prompts
erkunden – und einzelne Werkzeuge manuell mit Testwerten aufrufen, bevor du sie über den
[KI-Chat](ai-chat.md) einer KI zur Verfügung stellst. Unterstützte Server-Typen: ABAP-AI/MCP und
ABAP-AI/MCP2 im SAP-System (über einen SICF-Knoten), ein beliebiger lokaler HTTP-MCP-Server sowie der
in Eclipse bzw. VS Code eingebaute **SAP ADT MCP Server**.

## Voraussetzungen

- Für die SAP-Typen: ein eingerichteter SAP-Endpunkt (Fußzeile).
- Für lokale Typen: kein Endpunkt nötig – Protokoll/Host/Port/Pfad stehen direkt im Formular.
- SAP ADT MCP Server: in Eclipse (ADT ≥ 3.60) unter *Window → Preferences → ABAP Development → MCP
  Server* aktivieren und einen Token generieren (Port 2234); in ADT for VS Code über die Settings
  „Adt > Mcp Server" (Port 2236). Den Token trägst du unter „Authentifizierung" als Bearer ein.

## Typischer Ablauf

1. Server-Typ wählen. Bei SICF-Typen den SICF-Knoten prüfen und über „MCP Server auswählen" Area +
   Server-ID aus der Konfigurationstabelle übernehmen.
2. Bei lokalen Typen Host/Port/Pfad prüfen (beim ADT-Preset bereits vorbelegt, Variante Eclipse/VS
   Code umschaltbar) und unter „Authentifizierung" den Modus wählen.
3. „Verbinden" – der Katalog (Tools/Prompts/Ressourcen) erscheint als Baum, Details rechts.
4. Ein Werkzeug mit Testwerten manuell aufrufen und das Ergebnis prüfen.

## Funktionen im Detail

- **Authentifizierung (lokale Typen):** Modus „Keine", „Basic (Benutzer/Passwort)" oder
  „Bearer-Token". Der Wert kommt entweder aus einem Vault-Secret (Typ Benutzer/Passwort bzw.
  Token – ein Profil speichert dann nur den Verweis) oder du gibst ihn „nur für diese Sitzung"
  ein (wird nie gespeichert).
- **Weitere Konfiguration:** Zusatzparameter als Query-String, bei SICF-Typen das CSRF-Token.
- **Profile** merken die Verbindungs-Konfiguration am Projekt – ohne Secrets.
- Zeigt Werkzeug-Beschreibungen und deren erwartete Parameter, bevor du sie ausführst.
- Oben rechts: „Mit KI analysieren", Katalog als JSON/Markdown, „Als Notiz ablegen", im
  Experten-Modus das Verbindungsprotokoll.
- Nutzt reines JSON-RPC (kein Server-Sent-Events-Streaming).

## Tipps & Grenzen

- Gut geeignet, um vor dem produktiven Einsatz im KI-Chat zu prüfen, ob ein Werkzeug überhaupt
  wie erwartet funktioniert.
- Der Filter-Header lässt sich einklappen und anpinnen; der Titel zeigt auch eingeklappt Servername
  und Zähler.
- Lokale Typen lassen sich nicht als Tunnel freigeben (das braucht einen Endpunkt aus den
  Einstellungen).
