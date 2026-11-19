# BPMN-Editor

Modelliert Geschäftsprozesse als BPMN-2.0-Diagramm – Standard-Notation mit Aufgaben, Gateways,
Ereignissen und Pools, per Maus gezeichnet.

## Voraussetzungen

- Ein Projekt.
- Kein SAP-Endpunkt nötig.

## Typischer Ablauf

1. „Neues Objekt" öffnet ein leeres BPMN-Diagramm.
2. Elemente aus der Werkzeugpalette ziehen und verbinden.
3. Speichern.

## Funktionen im Detail

- Volle BPMN-2.0-Palette (Aufgaben, Gateways, Start-/End-Ereignisse, Pools/Lanes).
- Wie jedes Diagramm-Infoobjekt über die [Wissensablage](info-explorer.md) wiederauffindbar,
  verknüpfbar und in Bündeln gruppierbar.

## KI-Kanal (BDT-MCP-Gateway)

Eine externe KI (z. B. Claude Code) kann Prozesse über den Kanal `/mcp/bpmn` lesen und bauen:
Diagramme anlegen und öffnen, Aufgaben, Ereignisse, Gateways und Flüsse hinzufügen, Pools mit
Lanes für Rollen anlegen, umbenennen, verschieben und entfernen.

1. Knopf „Kanal für externe KI" in der Werkzeugleiste einschalten.
2. Zum Ändern in **Einstellungen → MCP → Freigaben** das Häkchen „KI darf BPMN-Diagramme ändern" setzen.
   Die erste Änderung einer externen KI fragt zusätzlich im Tab nach.
3. Jede Änderung siehst du sofort; **Strg+Z** nimmt sie zurück. Gespeichert wird nur über
   „Speichern" (ein von der KI neu angelegtes Diagramm wird gleich gespeichert).

Siehe auch [BDT mit Claude fernsteuern](../quickstart/mcp-claude-code.md).

## Im Architektur-Studio

Ein BPMN-Diagramm aus der Wissensablage erscheint im Architektur-Studio als Karte mit Vorschaubild.
„◧" öffnet es im Reiter „Inhalt" mit dem vollen BPMN-Editor, ohne Tab-Wechsel; „Speichern" schreibt
in die Wissensablage und erneuert das Vorschaubild. Ältere Diagramme bekommen ihr Vorschaubild beim
nächsten Speichern.

## Tipps & Grenzen

- Für freie, nicht BPMN-normierte Flowcharts eignet sich der [Mermaid-Editor](mermaid-editor.md)
  oder der [Diagramm-Editor (Draw.io)](drawio-editor.md) oft schneller.
