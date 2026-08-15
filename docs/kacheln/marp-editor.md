# Marp-Editor

Schreibt Präsentationsfolien als Markdown (Marp-Syntax) mit Live-Vorschau – inklusive Import aus
bestehenden PowerPoint-Dateien und Export als PDF.

## Voraussetzungen

- Ein Projekt.
- Kein SAP-Endpunkt nötig.

## Typischer Ablauf

1. „Neues Objekt" öffnet eine leere Präsentation, oder eine bestehende `.pptx`-Datei importieren.
2. Folien als Markdown schreiben (`---` trennt Folien), Vorschau live mitverfolgen.
3. Theme/Layout über den [CSS-Editor](css-editor.md) anpassen, falls gewünscht.
4. Als PDF exportieren oder als Infoobjekt speichern.

## Funktionen im Detail

- PowerPoint-Import wandelt vorhandene `.pptx`-Folien in Marp-Markdown um.
- PDF-Export läuft über einen Druck-Dialog, ohne dass die Folien dafür das Gerät verlassen.

## Tipps & Grenzen

- Eigene Themes gestaltest du über den [CSS-Editor](css-editor.md) – der Marp-Editor selbst
  bietet nur die Auswahl, nicht das Design von Grund auf.
