# CDS-Modell und Hierarchie aus alten Tabellen erzeugen

Ein Selbstlernkurs in neun Schritten: Du baust aus sechs Tabellen eines Kundendienstes (die Welt von Sascha) mit dem **Datenkatalog** und dem **ABAP Generator** einen CDS-View, eine CDS-Hierarchie und einen OData-Dienst. Dauer: etwa 90 Minuten.

## Was du brauchst

- Das **Musterprojekt „CDS – Kundendienst"**: Datei `docs/musterprojekt/cds/musterprojekt-cds.json` aus dem BDT-Repository. Import über **Einstellungen → Projekte → Import** (auch als Kopie unter neuem Namen möglich).
- Für die Schritte mit System: einen SAP-Endpunkt (Typ „SAP ABAP") auf ein System ab 7.58 / S/4HANA 2023 mit den Demo-Tabellen `ZZBDTDEMO_*`.
  - Auf dem Brandeis-Demosystem A4H liegen sie im Paket `$TMP`.
  - Auf einem eigenen System: `docs/musterprojekt/cds/demo-kundendienst-abapgit.zip` mit abapGit einspielen, dann die Klasse `ZZ_BDT_DEMO_CL_FILL` in ADT mit F9 ausführen. Sie schreibt die Testdaten (9 Org-Einheiten, 8 Techniker, 12 Kunden, 20 Anlagen, 40 Aufträge, gut 80 Positionen) und lässt sich jederzeit erneut ausführen.
- Zum Anlegen im System: am Endpunkt „Schreibzugriffe erlaubt", Generator-Stufe 2 und `$TMP` als erlaubtes Paket; unter **Einstellungen → Erweiterte Verwendung** die Häkchen „ADT-Schreibzugriffe" und „ABAP-Objekte generieren".

Ohne System kannst du die ersten Schritte mit dem Katalog „Kundendienst – Start" üben: er enthält alle Felder und die Testdaten.

## So ist das Projekt aufgebaut

| Ordner | Inhalt |
|---|---|
| 00 Start | Lies mich: Ziele, Voraussetzungen, Namen; Architektur-Studio-Workspace „CDS-Kurs – Landkarte" |
| 01 Ausgangslage | Datenmodell mit ER-Diagramm, Katalog „Kundendienst – Start" |
| 02 Lernschritte | Schritt 1–9, je mit Ziel, Ablauf, erwartetem Ergebnis, Prüffragen und Tipp |
| 03 Lösung | Katalog „Kundendienst – Lösung", erzeugte Quelltexte |

Der Workspace **„CDS-Kurs – Landkarte"** (Kachel **Architektur-Studio**) ist die Landkarte zum Kurs: Sheet „Überblick" mit Sprung-Karten, „Lernweg" als Anleitung zum Abhaken, „Vorgehen" erklärt die neun Stationen vom Tabellenbestand zum OData-Dienst, dazu „Datenmodell" und „Begriffe". Im Navigator startet der Rundgang „Der Kurs in drei Minuten".

Die Taxonomie **„Lernstand"** (Offen, In Arbeit, Erledigt) macht die Lernschritte in der Kachel **Kanban** zu einem Board: Verschiebe die Karten, wenn du weiterkommst.

## Die neun Schritte

1. Tabellen in den Datenkatalog laden
2. Beziehungen vorschlagen lassen (Fremdschlüssel, Feldname, Eltern-Feld)
3. Das Modell grafisch prüfen
4. Felder auswählen und Filterfelder setzen
5. CDS-Entwurf erzeugen und prüfen
6. Im System anlegen – mit dem ABAP Generator (Prüfen, Ausführen, Laufprotokoll)
7. Eine Hierarchie erzeugen und über OData testen
8. Der abapGit-Weg
9. Aufräumen (Rückabwicklung über das Laufprotokoll)

## Gut zu wissen

- Das abapGit-ZIP enthält auch die Fremdschlüssel der Tabellen. Nach dem Einspielen schlägt der Datenkatalog in Schritt 2 dieselben Beziehungen vor wie auf A4H.
- Bei mehreren Teilnehmern auf einem System: jeder hängt ein Kürzel an den View-Namen bzw. das Hierarchie-Präfix (z. B. `ZZ_BDT_DEMO_JM`).
- Der ABAP Generator löscht bei der Rückabwicklung nur Objekte, die er selbst angelegt hat. Die Demo-Tabellen bleiben stehen.
