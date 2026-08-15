# MCP-Konfigurator

Erzeugt eine fertige `mcp.json`- und `.env`-Konfiguration für Coding Agents (z. B. Claude Code),
damit diese sich mit einem MCP-Server aus deiner BDT-Umgebung verbinden können – ohne die
Zugangsdaten von Hand zusammenzustellen.

## Voraussetzungen

- Ein eingerichteter MCP-fähiger Endpunkt.

## Typischer Ablauf

1. Endpunkt wählen.
2. Konfiguration erzeugen lassen.
3. `mcp.json`/`.env` in deinen Coding Agent übernehmen.

## Funktionen im Detail

- Übernimmt Adresse und Zugangsart aus dem gewählten Endpunkt, ohne dass du sie doppelt
  pflegen musst.

## Tipps & Grenzen

- Enthaltene Zugangsdaten sind sensibel – behandle die erzeugte Datei entsprechend vertraulich.
