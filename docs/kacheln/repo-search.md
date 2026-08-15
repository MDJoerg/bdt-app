# Repository-Suche

Durchsucht das Repository deines SAP-Systems nach Entwicklungsobjekten – CDS Views, Klassen,
Programmen, Nachrichtenklassen und vielem mehr. Deckt zusätzlich die frühere „Katalogsuche" mit
ab: über „Auswahl anreichern" bekommen Treffer zusätzliche Spalten wie Zeilenzahl oder
verwendete CDS Views.

## Voraussetzungen

- Ein eingerichteter SAP-Endpunkt (ADT).

## Typischer Ablauf

1. Suchbegriff eingeben.
2. Über den Objekttyp-Auswahldialog eingrenzen (kuratierte Typenliste, Presets, RAP-Schichten).
3. Suchen – bis zu 1.000 Treffer, darüber hinaus erscheint eine sichtbare Warnung statt einer
   stillen Kürzung.
4. Ergebnis-Spalten über den Spalten-Konfigurator anpassen, ggf. Auswahl markieren und
   „Auswahl anreichern" für Zusatzinformationen (Zeilenzahl, verwendete CDS Views,
   Anwendungskomponente, RAP-Aktionen).
5. Treffer öffnen, exportieren oder in den Sammelkorb legen.

## Funktionen im Detail

- Bei einem Treffer vom Typ Knowledge Transfer Document (SKTD/TYP) öffnet ein Kontextmenü-
  Eintrag eine Markdown-Vorschau des Dokuments samt Export/Übernahme in den
  [Markdown-Editor](markdown-editor.md).
- Suchprofile speichern eine Suche (Begriff, Objekttypen, Spalten) für die Wiederverwendung.

## Tipps & Grenzen

- Rein lesend – die Repository-Suche ändert nichts in deinem SAP-System.
- Für eine gezielte Katalogsuche nach OData-Services nutze stattdessen den
  [SAP OData Katalog Browser](odata-catalog-browser.md).
