# CDS Explorer

Liest die Element-Info einer CDS View direkt aus deinem SAP-System (über die ADT-API) und zeigt
sie als übersichtliche Object Page: Attribute, Assoziationen (inklusive eines klickbaren
Assoziations-Graphen zur Navigation zu verknüpften Views), eine Markdown-Zusammenfassung und den
Roh-XML-Quelltext.

## Voraussetzungen

- Ein eingerichteter SAP-Endpunkt (ADT).
- Funktioniert nur für CDS Views, nicht für klassische Tabellen.

## Typischer Ablauf

1. Namen der CDS View eingeben (Suchhilfe verfügbar), Sprache wählen.
2. „Laden" – die Object Page baut sich mit den geladenen Daten auf.
3. Zwischen den Tabs Attribute/Assoziationen/Assoziations-Graph/Markdown/Roh-XML wechseln.
4. Im Assoziations-Graph auf eine verknüpfte View klicken, um direkt dorthin zu navigieren
   („Zurück"-Verlauf bleibt erhalten).
5. Bei Bedarf den Quelltext-Tab öffnen, um den vollständigen CDS-Quelltext zu sehen.

## Funktionen im Detail

- Bereits besuchte Objekte werden zwischengespeichert – erneutes Anklicken im Graphen lädt nicht
  jedes Mal neu nach.
- Eine Suchhilfe für den Objektnamen sucht gezielt nach CDS Views (nicht nach anderen
  Objekttypen).

## Tipps & Grenzen

- Rein lesend – der CDS Explorer schreibt nichts in dein SAP-System zurück.
- Diese Kachel hat die frühere Kachel „Element Info" vollständig ersetzt.
