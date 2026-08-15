# MCP-Inspector

Verbindet sich mit einem MCP-Server (z. B. im ABAP-System) und lässt dich dessen Werkzeuge,
Ressourcen und Prompts erkunden – und einzelne Werkzeuge manuell mit Testwerten aufrufen, bevor
du sie über den [KI-Chat](ai-chat.md) einer KI zur Verfügung stellst.

## Voraussetzungen

- Ein eingerichteter MCP-fähiger Endpunkt.

## Typischer Ablauf

1. Endpunkt wählen, verbinden.
2. Verfügbare Werkzeuge/Ressourcen/Prompts durchsehen.
3. Ein Werkzeug mit Testwerten manuell aufrufen und das Ergebnis prüfen.

## Funktionen im Detail

- Zeigt Werkzeug-Beschreibungen und deren erwartete Parameter, bevor du sie ausführst.
- Nutzt reines JSON-RPC (kein Server-Sent-Events-Streaming).

## Tipps & Grenzen

- Gut geeignet, um vor dem produktiven Einsatz im KI-Chat zu prüfen, ob ein Werkzeug überhaupt
  wie erwartet funktioniert.
