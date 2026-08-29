# XR-Universum

Stellt ein Asset-Universum, deine Wissensablage oder ein SAP-Repository als begehbares
3D-Universum dar: Regionen und Cluster fliegst du per Autopilot an, einzelne Objekte öffnest du
in einem Detail-Panel. Gedacht zum Erkunden großer Datenbestände, nicht zum freien Herumfliegen.

## Voraussetzungen

- Je nach Datenquelle: ein Asset-Universum ODER ein Projekt mit einer Wissensablage-Hierarchie
  (beides ohne SAP-Endpunkt) ODER ein SAP-Endpunkt mit eingetragenen
  Anwendungskomponenten-/Paketmustern (es gibt keine SAP-Schnittstelle, die „alle Komponenten
  eines Systems" auflistet – du grenzt bewusst ein). Eine vierte Datenquelle – eine „Code-Stadt"
  – öffnet sich ausschließlich über den Knopf „Als XR-Stadt begehen" in der Kachel
  **EW Code Visualizer**, nicht über die Datenquellenauswahl hier.
- Sinnvoll nutzbar nur in der Web-App/PWA.

## Typischer Ablauf

1. Datenquelle wählen: Asset-Universum, Wissensablage oder SAP-Repository – oder direkt aus dem
   EW Code Visualizer heraus mit „Als XR-Stadt begehen" starten (überspringt diesen Schritt).
2. Bei SAP-Repository: Endpunkt sowie Komponenten-/Paketmuster eintragen.
3. „Flug starten".
4. Region → Cluster → Objekt anklicken, um näher heranzufliegen; ein Klick auf ein Objekt öffnet
   das Detail-Panel.
5. Optional: Beziehungen eines Objekts „folgen" oder eine Mission mit Zielregion/-anzahl
   verfolgen.
6. Optional: „Sitzung freigeben" erzeugt ein statisches Abbild zum Teilen per Link/QR-Code.

## Funktionen im Detail

- **Filter** (kürzlich geändert/Klassifizierung) grenzen die sichtbaren Objekte ein, sofern die
  gewählte Datenquelle die nötigen Informationen liefert.
- **Beziehungen im Raum anzeigen** verbindet Objekte im aktuell sichtbaren Cluster sichtbar
  miteinander.
- **Planet/Mond-Darstellung:** bei SAP-Repository-Daten erscheint der technische Objekttyp als
  Planet, die einzelnen Objekte umkreisen ihn als Monde.
- **Missionen:** ein einfaches Ziel („besuche N Objekte, optional in einer bestimmten Region")
  mit sichtbarem Fortschritt.
- **Code-Stadt (aus dem EW Code Visualizer):** Objekte erscheinen als Gebäude statt als Kugeln –
  Höhe und Farbe entsprechen den dort gewählten Metriken, Gebäude mit ATC-Findings glühen und
  tragen ein Findings-„Monster" (n Arme = n Findings, ab 8 gekappt mit sichtbarer „+N"-Anzeige),
  kürzlich geänderte pulsieren leicht. Wurden Findings seit dem letzten vergleichbaren Lauf
  reduziert, glänzt das Gebäude zusätzlich golden. Statt der generischen Mission zeigt eine
  Code-Stadt die Karte „Monster-Jagd": besiege eine Zielanzahl Findings-Monster, optional
  beschränkt auf ein Paket – ein Monster gilt als besiegt, sobald sein Objekt-Detail geöffnet
  wird. Die Datenquellenauswahl bleibt dabei ausgeblendet; „Flug beenden"/„Flug starten" fliegen
  dieselbe Stadt erneut an, ohne die Seite neu zu laden.

## Tipps & Grenzen

- Ein SAP-Repository-Universum ist immer auf die von dir eingetragenen Komponenten-/
  Paketmuster beschränkt – kein automatischer Komplettflug durch ein ganzes System.
- Eine per „Sitzung freigeben" geteilte Ansicht ist ein statisches Abbild zum Zeitpunkt des
  Teilens, keine Live-Kopplung.
