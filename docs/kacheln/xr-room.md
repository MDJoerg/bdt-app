# XR-Raum

Baut aus Objekten deiner Wissensablage einen begehbaren 3D-Raum – als Panels an den Wänden.
Am Desktop steuerst du mit Maus/Tastatur, mit einem VR-Headset (z. B. Quest) kannst du optional
immersiv beitreten. Zusätzlich kannst du eine laufende Sitzung mit anderen teilen, bis hin zu
einem echten Mehrpersonen-Meeting mit Sprachchat.

## Voraussetzungen

- Ein Projekt mit Inhalten in der Wissensablage für die Panels.
- Sinnvoll nutzbar nur in der Web-App/PWA (die Browser-Erweiterung selbst eignet sich nicht für
  eine immersive Sitzung).
- Zum Freigeben/für Mehrraum-Sitzungen/Termine brauchst du einen eingerichteten BDT-Hub-Endpunkt.
- Für den Import von 3D-Modellen (statt nur Icons) das Häkchen „3D-Modell-Import erlauben" unter
  Einstellungen → „Erweiterte Verwendung".

## Typischer Ablauf

1. Im Reiter „Szene bauen" Objekte aus der Wissensablage auswählen (oder Icons/3D-Modelle direkt
   einfügen).
2. „Szene starten" – funktioniert auch mit leerer Auswahl, für einen zunächst leeren Raum.
3. Am Desktop navigieren, oder mit einem Headset immersiv beitreten.
4. Optional im Reiter „Freigabe & Teilnehmer" die Sitzung per Link, QR-Code oder Meeting-Code
   teilen.
5. Optional die aktuelle Anordnung speichern, damit sie beim nächsten Mal wieder steht.

## Funktionen im Detail

Die „Raum"-Karte (Canvas + grundlegende Steuerung) ist immer sichtbar, darunter gliedern sich
fünf Reiter:

- **Szene bauen:** Objekte aus der Wissensablage, Icons, Fabric-Grafiken/Wordclouds/Mermaid-
  Diagramme als Bild-Panel, 3D-Modelle (aus einer geprüften Auswahl, einer eigenen geprüften
  Quelle, oder eine lokale `.glb`/`.gltf`-Datei ganz ohne Internetzugriff) sowie ein
  Raum-Baukasten mit einfachen Bausteinen (Quader/Zylinder/Kugel/Kegel, inkl. eines
  Vorlagen-Generators für z. B. „4 Wände + Tisch").
- **Mehrraum-Sitzung:** mehrere Räume mit einer Lobby und Portalen dazwischen, als
  wiederverwendbares Projekt-Objekt gespeichert.
- **Termine:** ein Termin bindet eine Sitzung an einen Raum, mit Warteraum (der Koordinator lässt
  Gäste einzeln zu oder weist sie ab), Kapazitätsgrenze und optional anonymen Teilnehmern mit
  gewürfeltem Avatar.
- **Meeting beitreten:** mit eigenem Projekt/eigenem Avatar über eine eingetippte Meeting-ID
  beitreten (derselbe Weg wie über die Kachel [XR Meeting](xr-meeting.md)).
- **Freigabe & Teilnehmer:** befristete (15 Minuten) oder dauerhafte Freigabe, Sprachchat mit
  räumlichem Klang, Teilnehmerliste mit der Möglichkeit, jemanden zu entfernen.

## Tipps & Grenzen

- Ohne Headset funktioniert alles auch am Desktop – Bewegen per Tastatur/Maus, Klick statt
  Controller-Trigger.
- Eingefügte Icons/3D-Modelle/Bausteine gehören zur Sitzung; ob sie beim „Anordnung speichern"
  mitgesichert werden, hängt vom jeweiligen Inhaltstyp ab.
- Für einen Beitritt ganz ohne eigenes Projekt oder Konto gibt es die Karte
  „Meeting per Code beitreten" – siehe [BDT Hub](../experten/bdt-hub.md).
