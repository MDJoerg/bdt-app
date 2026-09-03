# Transport Cockpit

Zeigt Transportaufträge des gewählten SAP-Systems ohne SAPGUI: „Meine offenen Transporte"
(Workbench UND Customizing) als Explorer-Baum, dazu Recherche über andere Benutzer und bereits
freigegebene Aufträge. Nutzt dasselbe offizielle Transport-Organizer-ADT-API wie Eclipse –
rein lesend, es werden keine Transporte angelegt, verändert oder freigegeben.

## Voraussetzungen

- Ein eingerichteter SAP-Endpunkt (ADT). Die normale Transport-Organizer-Berechtigung eines
  Entwicklers genügt.

## Typischer Ablauf

1. Endpunkt in der Fußzeile wählen und „Suchen" klicken – ohne weitere Eingaben findest du
   deine eigenen änderbaren Aufträge (Workbench + Customizing).
2. Für Recherche: Benutzer eintragen (`*` = alle), Status „Freigegeben" ankreuzen und den
   Zeitraum wählen.
3. Im Baum navigieren: Transportauftrag → Aufgabe → Objektkategorie → Objekt.
4. Klick auf einen Auftrag zeigt rechts die Detailseite (Kennzahlen, Aufgaben, filterbare
   Objekt-Tabelle mit Export/Sammelkorb).
5. Rechtsklick (oder Klick auf ein Objekt) öffnet das Kontextmenü: „In ADT öffnen",
   Repository-Suche, CDS Explorer, Data Preview, Verwendungsnachweis oder MDE Studio –
   je nach Objekttyp.

## Funktionen im Detail

- **Benutzer:** leer = der am Endpunkt angemeldete Benutzer, `*` = alle Benutzer, sonst ein
  konkreter Benutzername.
- **„Freigegeben" filtert übers Freigabedatum:** Standard ist „Letzte 2 Wochen" – ältere
  freigegebene Aufträge brauchen „Zeitraum (von/bis)" mit explizitem Datumsfenster.
- **Suchprofile** speichern die komplette Filter-Einstellung je Projekt.
- **ADT-Link:** funktioniert nur mit lokal installiertem Eclipse/ADT, aktiviertem „Open ADT
  Links from external documents" und einer Projekt-Verbindung mit derselben Systemkennung
  (am Endpunkt gepflegt).

## Tipps & Grenzen

- Die Kachel legt beim Suchen eine kurzlebige serverseitige Suchkonfiguration an (dasselbe
  Verfahren wie Eclipse) und räumt eigene Alt-Konfigurationen automatisch wieder auf.
- Die Rückwärtssuche „In welchen Transporten ist dieses Objekt enthalten?" sowie die
  Dashboard-Diagramme (Objekttyp-Donut, Entwickler-Heatmap, Pakete-Torte) folgen in einer
  späteren Ausbaustufe.
