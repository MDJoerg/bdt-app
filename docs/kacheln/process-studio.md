# Prozess-Studio

Hilft dir, einem Key User bei der Arbeit in einer klassischen SAP-Dynpro-
Transaktion „zuzuschauen": Du reicherst ein lokales Bildschirmvideo mit
Marken, Screenshots, Notizen und (optional) einem Transkript an – die
Grundlage für eine spätere Prozessdokumentation Richtung Fiori Elements/RAP.

Die Aufzeichnung selbst passiert **außerhalb** von BDT (z. B. mit deinem
Bildschirm-Recorder oder dem im SAP GUI eingebauten Recorder) – das
Prozess-Studio ist der Ort, an dem du das Ergebnis auswertest.

## Voraussetzungen

- Ein Projekt.
- Kein SAP-Endpunkt nötig – alles läuft lokal im Browser.
- Für das optionale Transkript: das Häkchen „Lokale Transkription (Whisper)"
  in Einstellungen → „KI Funktionen" (in der Chrome-/Edge-Erweiterung nicht
  verfügbar, dort bitte Webapp/Electron/VS Code nutzen).

## Typischer Ablauf

1. „Neuer Prozess" anlegen (Name, optional Prozess-ID/Status/
   Verantwortlicher/Zielarchitektur), speichern.
2. Optional eine oder mehrere **Varianten** hinzufügen (z. B. „Standard" vs.
   „Sonderfall").
3. „Neue Aufzeichnung" unter dem Prozess anlegen, im Tab „Video" die lokale
   Videodatei wählen (sie wird **nicht gespeichert** – nur Dateiname/Hash).
4. Beim Abspielen im Tab „Marken" an wichtigen Stellen eine Marke setzen
   (aktuelle Position), dazu Bezeichnung/Bemerkung eintragen und bei Bedarf
   einen Screenshot aufnehmen.
5. Alternativ „Auto-Marken-Vorschläge suchen" – das Video wird lokal auf
   Bildwechsel abgesucht, du übernimmst oder verwirfst jeden Vorschlag
   einzeln.
6. Optional im Tab „GUI-Script" eine extern aufgezeichnete SAPGUI-
   Bedienschrittfolge importieren (GuiXT-Input-Script oder SAP-GUI-
   Scripting/Alt+F12, kein eigener Recorder in BDT) und mit den Marken
   abgleichen.
7. Optional im Tab „Transkript" die Tonspur transkribieren lassen.
8. Im Tab „Export" einen Markdown-Report für den ganzen Prozess erzeugen –
   er öffnet sich im Markdown-Editor zum Speichern/Weiterbearbeiten.

## Funktionen im Detail

- **Hierarchie:** Prozess → Variante → Aufzeichnung. Mehrere Aufzeichnungen
  können demselben Prozess zugeordnet werden (z. B. verschiedene Anläufe).
- **Abschnitt & Sprünge:** Bei einem sehr langen Video kannst du dich auf
  „Minute a bis c" beschränken (Abschnitt) und einzelne Teile beim Abspielen
  automatisch überspringen lassen (Sprünge) – ohne das Video zu schneiden.
- **Marken-Arten:** manuell gesetzt, aus der Auto-Erkennung übernommen, aus
  einer importierten SAP-GUI-Aufzeichnung abgeglichen (Reihenfolge statt
  Zeitmarken – künftig auch aus technischen Traces).
- **GUI-Script-Import:** unterstützt zwei Formate – GuiXT-Input-Script
  (Teil des SAP GUI) und SAP-GUI-Scripting (Alt+F12 → „Script Recording
  and Playback"). Ohne Zeitmarken im Script wird die Reihenfolge der
  Schritte auf die Reihenfolge deiner Marken abgebildet; jede Zuordnung
  zeigt eine Konfidenz und lässt sich per Auswahlliste korrigieren.
  „Ausrichtung in Marken übernehmen" trägt Programm/Dynpro in die
  zugeordneten Marken ein, ohne bereits gepflegte Angaben zu überschreiben.
- **Systeminfos je Marke:** Programm/Dynpro/Tcode lassen sich auch manuell
  eintragen. Bei gewähltem SAP-Endpunkt kannst du „Im Repository suchen"
  nutzen, um ein passendes Objekt zu verknüpfen – mit Sprung zum
  Verwendungsnachweis und (bei lokal installiertem Eclipse/ADT) einem
  direkten ADT-Link. „Als Graph anzeigen" zeigt Prozess/Marken/Objekte als
  Diagramm.
- **Screenshots** landen als Anhang direkt an der jeweiligen Marke.
- Alle Änderungen (Marken, Abschnitt, Sprünge, Transkript) bleiben erst im
  Formular, bis du „Speichern" klickst.

## Tipps & Grenzen

- Das Video selbst wird **nie** gespeichert – nur eine Referenz (Dateiname,
  Größe, Dauer, Hash) plus ein optionaler Link (z. B. auf SharePoint). Beim
  erneuten Öffnen einer Aufzeichnung musst du die Datei erneut wählen; passt
  der Hash nicht mehr zur zuletzt bekannten Datei, wirst du darauf
  hingewiesen.
- Die Auto-Marken-Erkennung ist eine einfache, rein lokale Bildvergleichs-
  Heuristik – sie liefert **Vorschläge**, keine automatisch gesetzten Marken.
- „Im Repository suchen" braucht einen gewählten SAP-Endpunkt (Fußzeile) –
  ansonsten laufen Video/Marken/GUI-Script-Import komplett ohne Endpunkt.
  „In ADT öffnen" wirkt nur mit lokal installiertem Eclipse/ADT + passender
  Projekt-Verbindung.
- STAD-/Trace-Zeitanker (technische Systemspuren) sind für eine spätere
  Ausbaustufe vorgesehen, noch nicht Teil dieser Kachel.
- Diese Kachel ist als Premium-Funktion eingeordnet und noch experimentell.
