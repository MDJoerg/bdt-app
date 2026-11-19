# Customizing-Studio

Zeigt die eigenen Customizing-Tabellen des gewählten SAP-Systems, die klassisch über **SM30**
(Pflegedialoge) und **SM34** (View-Cluster) gepflegt werden, und wie weit sie schon auf
**Custom Business Configuration** (CBC, Fiori-App „Custom Business Configurations") umgestellt sind.
Der Bereich „Bestand" beantwortet die Frage „Worüber reden wir eigentlich?" und liefert die
Grundlage für eine Aufwandsschätzung. Das Erzeugen von CBC-Objekten folgt in späteren Ausbaustufen.

## Voraussetzungen

- Ein eingerichteter SAP-Endpunkt (ADT), on-premise. Auf ABAP Cloud sind die SM30-Tabellen per SQL
  gesperrt.
- Die Kachel liest nur. Sie stellt SQL-SELECTs über dieselbe Schnittstelle wie die Data Preview.

## Typischer Ablauf

1. Endpunkt in der Fußzeile wählen.
2. **Namensraum** angeben, z. B. `Z*, Y*` oder `/ABC/*` (mehrere Muster mit Komma).
3. Häkchen **View-Cluster (SM34)** und **Migrationsstand prüfen (CBC)** nach Bedarf setzen und
   **Bestand laden** klicken.
4. **Übersicht:** Kennzahlen, Komplexität, Umstellungsstand, Pflegedialoge je Paket und der Verlauf
   aufgehobener Läufe.
5. **Pflegeobjekte:** alle Pflegedialoge und View-Cluster als Tabelle (filter-, sortier- und
   exportierbar, Bericht als Markdown). Ein Klick öffnet rechts die Objektseite.
6. **Objektseite:** Eckdaten, Events, Hinweise zur Umstellung, auf Klick Felder, Fremdschlüssel und
   Zeilenzahl; für Cluster die Struktur als Baum. Absprünge in Data Preview, ADT und
   Verwendungsnachweis.
7. **Lauf aufheben** speichert den Bestand in der Wissensablage. Aus der Wissensablage öffnet
   „Dashboard anzeigen" ihn wieder (nur lesen).

## Komplexitäts-Ampel

- **einfach:** eine Tabelle ohne Events.
- **mittel:** Pflege-View, Texttabelle, 1–3 Events oder mindestens 3 Fremdschlüssel.
- **komplex:** Teil eines View-Clusters, mindestens 4 Events oder Pflege-View über mindestens
  3 Tabellen.

Jede Zeile nennt die Gründe für ihre Einstufung.

## Migrationsstand

Ein CBC-Objekt hat eine Wurzel-View, die `I_CstmBizConfignLastChgd` liest. Die Kachel sucht diese
Wurzeln im CDS-Quelltext aller Views und folgt ihren Kind-Views bis zur gelesenen Tabelle. Eine
Tabelle mit solchem Gegenstück gilt als „umgestellt". Ein View-Cluster gilt erst als umgestellt,
wenn alle seine Objekte es sind.

## Grenzen

- Verwaiste Pflegedialoge (Tabelle oder View existiert nicht mehr) erscheinen mit Hinweis.
- Die Quelltexte der Event-Routinen werden noch nicht angezeigt, nur Event und Routinenname.
