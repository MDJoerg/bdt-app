# OData Browser

Lädt die Metadaten eines konkreten OData-Service und zeigt dessen Entitäten mit ihren Daten – zum
gezielten Nachschauen, Filtern und Exportieren, wenn du bereits weißt, welcher Dienst der
richtige ist.

## Voraussetzungen

- Ein eingerichteter SAP-Endpunkt.
- Den Servicenamen/-pfad kennst du entweder schon, oder du findest ihn über die eingebaute
  Suchhilfe bzw. den [SAP OData Katalog Browser](odata-catalog-browser.md).

## Typischer Ablauf

1. Servicepfad eintragen (oder über die Suchhilfe suchen).
2. „Metadaten laden" – danach erst wählst du bewusst eine Entität aus (kein automatisches
   Vorab-Laden).
3. Daten filtern (über ein Filter-Popup statt einer rohen `$filter`-Texteingabe) und ansehen.
4. In Ablage speichern, in den Sammelkorb legen oder ins Daten-Studio übernehmen.

## Funktionen im Detail

- Das Filter-Popup passt sich dem Feldtyp an (Text, Zahl mit von/bis, Datum, Ja/Nein) und bietet
  bei OData V4 zusätzlich eine Mehrfachauswahl bekannter Werte.
- Ergebnisse lassen sich direkt als Datensatz im [Daten-Studio](data-studio.md) weiterverarbeiten.

## Tipps & Grenzen

- Die Seitengröße ist auf 1.000 Zeilen gedeckelt.
- Rein lesend.
