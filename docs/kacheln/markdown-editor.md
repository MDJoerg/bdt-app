# Markdown-Editor

Schreibt Notizen, Dokumentationen und Berichte als Markdown, mit Live-Vorschau daneben. Der
Standard-Editor für reinen Text in der Wissensablage – viele andere Kacheln (z. B. der
[Markdown-Konverter](markdown-converter.md) oder „Lauf aufheben"-Berichte) übergeben ihr
Ergebnis genau hierher zur Weiterbearbeitung.

## Voraussetzungen

- Ein Projekt.
- Kein SAP-Endpunkt nötig.

## Typischer Ablauf

1. „Neues Objekt" öffnet einen leeren Markdown-Text.
2. Links schreiben, rechts die gerenderte Vorschau live mitverfolgen.
3. Speichern.

## Funktionen im Detail

- Rendert auch eingebettete ```mermaid-Codeblöcke live als echtes Diagramm in der Vorschau.
- Nimmt Übergaben aus anderen Kacheln entgegen (z. B. einen frisch erzeugten Markdown-Report),
  die du danach ganz normal weiterbearbeitest und speicherst.

## Tipps & Grenzen

- Für interaktive Diagramme direkt als Text-DSL eignen sich die spezialisierten Editoren besser
  (z. B. [Mermaid-Editor](mermaid-editor.md), [BPMN-Editor](bpmn-editor.md)) – der
  Markdown-Editor rendert Mermaid nur in der Vorschau, bearbeitet es aber nicht komfortabel.
