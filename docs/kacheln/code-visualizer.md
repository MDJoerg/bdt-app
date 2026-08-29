# EW Code Visualizer

Visualisiert ABAP-Entwicklung als **Code-Stadt**: eine Treemap, in der jedes
Objekt eine Kachel („Gebäude") ist – die Fläche und die Farbe sind frei
wählbare Metriken. Große rote Kacheln springen sofort ins Auge: viel Code
mit vielen Findings oder häufigen Änderungen – die besten
Refactoring-Kandidaten („Hotspots").

Die Idee stammt aus Enno Wulffs SAP-Community-Blog „I Have A Dream:
Code Visualization" (2020) – der Kachel-Name ist die Hommage an den Autor.

## Voraussetzungen

- **Live-Quelle:** ein SAP-Endpunkt in der Fußzeile (liest Quelltexte und
  optional die Versionsverwaltung des Systems – rein lesend).
- **Offline-Quelle:** keine – ein abapGit-ZIP-Archiv (z. B. von GitHub)
  funktioniert ganz ohne Endpunkt in allen Umgebungen.
- ATC-Findings kommen ausschließlich aus einem **aufgehobenen Lauf** des
  Clean Core Cockpits – die Kachel startet selbst keinen ATC-Lauf.
- „Lauf aufheben" und die Findings-Auswahl brauchen ein Projekt (Fußzeile).

## Typischer Ablauf

1. Quelle wählen: „SAP-System (live)" mit Paketen (Suchhilfe über das
   Wertehilfe-Symbol, `*`-Muster erlaubt) oder „abapGit-Archiv" mit einer
   ZIP-Datei.
2. Optional „Änderungshistorie laden" anhaken (Live-Quelle) und einen
   aufgehobenen Clean-Core-Lauf für die ATC-Findings wählen.
3. „Analysieren" drücken – die Kachel lädt die Quelltexte (max. 3 parallel,
   abbrechbar) und vermisst jedes Objekt.
4. In der **Stadt** Fläche/Farbe umschalten (z. B. Fläche = Quelltextzeilen,
   Farbe = Findings je 100 LOC); Klick auf ein Gebäude öffnet die
   Objekt-Details mit allen Metriken, ADT-Link und Quelltext-Vorschau.
5. Im Reiter **Tabelle** sortieren/filtern, exportieren oder als Datensatz
   ins Daten-Studio übernehmen; optional „Verwendungen laden"
   (Where-Used-Zähler je Objekt).
6. „Lauf aufheben" speichert die Metriken als Analyse-Lauf in der
   Wissensablage – im Reiter **Vergleich** lassen sich zwei Stände
   gegenüberstellen (gewachsen/geschrumpft/neu/entfernt), im Reiter
   **Trend** die Entwicklung mehrerer aufgehobener Läufe DERSELBEN
   Quelle/Auswahl über die Zeit.
7. „Markdown-Report erzeugen" bereitet eine Management-Summary mit
   Top-Hotspots/-Findings (als Mermaid-Diagramm) für den Markdown-Editor
   vor; „Als cc.json exportieren" lädt dieselben Metriken im
   [CodeCharta](https://maibornwolff.github.io/codecharta/)-Format herunter
   – beides funktioniert auch für einen historischen, read-only geöffneten
   Lauf.
8. „Als XR-Stadt begehen (Flug)" öffnet dieselbe Analyse in einem neuen Tab in der
   Kachel **XR-Universum** – die Gebäude stehen dort begehbar im Raum statt
   in einer flachen Treemap, per Autopilot angeflogen wie ein Sonnensystem
   (ebenfalls live oder read-only nutzbar).
   Gebäude mit ATC-Findings tragen dort ein Findings-„Monster" (n Arme =
   n Findings) und – wenn diese Findings seit dem letzten vergleichbaren
   Lauf abgenommen haben – zusätzlich einen goldenen Funken.
9. „Als begehbare Stadt betreten" öffnet dieselbe Analyse stattdessen in
   einem neuen Tab in der Kachel **XR-Raum** – eine ECHTE Stadt mit
   Bezirken (Pakete) und Straßen statt eines Flugmodus: du gehst zu Fuß
   hindurch (VR: Thumbstick-Gehen + Teleport-Wurf; Desktop: Klick auf den
   Boden). Bezirke ohne Findings erscheinen als grüner Park, betroffene
   Bezirke als graue Straßenfläche – so erkennst du auf einen Blick,
   welches Paket betroffen ist, bevor du überhaupt ein Gebäude anklickst.
   Dieselben Findings-„Monster" und die goldene Vergleichs-Belohnung wie im
   Flugmodus, ohne die dortige Monster-Jagd-Mission.

## Funktionen im Detail

- **Metrik-Katalog:** Quelltextzeilen, Code-Zeilen, Kommentaranteil,
  Methoden, Statements (geschätzt; im Archiv-Modus optional exakt über
  abaplint), Ø Statements je Methode, ATC-Findings + Dichte,
  Änderungstage/Alter/Autoren (aus der SAP-Versionsverwaltung),
  Hotspot-Score (LOC × Änderungstage), Verwendungen, Cloud-kritische
  Bezugnahmen (gegen die im Clean Core Radar importierte
  Cloudification-Datenbasis).
- **Farbskala:** grün (gut) → gelb → rot (schlecht); grau heißt ehrlich
  „nicht ermittelt" – z. B. Findings ohne gewählten Lauf. Ist die gewählte
  Farb-Metrik komplett leer, fällt die Stadt sichtbar auf
  „Ø Statements je Methode" zurück.
- **Änderungshistorie:** liest die Versionsverwaltung (Tabelle VRSD) über
  ein SELECT im Zielsystem – als Änderungsrate zählen unterschiedliche
  Änderungstage, nicht rohe Versionszeilen.
- **Vergleich:** zwei aufgehobene Läufe (oder die aktuelle Analyse)
  nebeneinander – welche Gebäude sind gewachsen, geschrumpft, neu oder
  verschwunden (Code-Radar-Idee).
- **Trend:** berücksichtigt nur Läufe mit exakt derselben Quelle/Paket-
  bzw. Archiv-Auswahl wie der aktuelle/gewählte Lauf (sonst wäre die
  Zeitreihe nicht sinnvoll) – „Lauf aufheben" mehrfach für dieselbe
  Auswahl nutzen, um eine Entwicklung zu sehen.
- **cc.json-Export:** reiner Datei-Download im Format der
  CodeCharta-Community-Konvention, Anschluss an eine bestehende
  ABAP→CodeCharta-Kette aus der SAP-Community – nicht ermittelte Metriken
  fehlen im Export bewusst, statt als 0 zu erscheinen.
- **Als XR-Stadt begehen (Flug):** dieselben Objekte als begehbare Gebäude im
  XR-Universum – Höhe/Farbe entsprechen den hier gewählten Metriken,
  Gebäude mit ATC-Findings glühen, per Autopilot angeflogen wie ein
  Sonnensystem. Nur sinnvoll in der Web-App/PWA (WebXR).
- **Gamification (im Flugmodus, XR-Universum):** Gebäude mit ATC-Findings tragen ein
  Findings-„Monster" (so viele Arme wie Findings, ab 8 gekappt mit
  sichtbarer „+N"-Anzeige); kürzlich geänderte Gebäude pulsieren leicht.
  Wurden Findings seit dem letzten vergleichbaren Lauf reduziert, glänzt
  das Gebäude zusätzlich golden – die „Vergleichs-Belohnung". Eine eigene
  „Monster-Jagd"-Karte (statt der generischen Mission, die auf mehrere
  Regionen ausgelegt ist) lässt eine Zielanzahl Monster besiegen –
  optional beschränkt auf ein Paket; besiegt ist ein Monster, sobald sein
  Objekt-Detail geöffnet wird.
- **Als begehbare Stadt betreten:** dieselben Objekte als echte Stadt zum
  Zu-Fuß-Erkunden in der Kachel **XR-Raum** (`docs-user/kacheln/xr-room.md`)
  – Bezirke (Pakete) sind auf dem Boden erkennbar (grüner Park ohne,
  graue Straßenfläche mit Findings), Findings-„Monster"/goldener Funke
  erscheinen unverändert wie im Flugmodus, aber ohne eigene Monster-Jagd-
  Mission. Nur Gehen in v1 (Auto-/Flugtaxi-Modus als spätere Ausbaustufe),
  nur sinnvoll in der Web-App/PWA (WebXR).

## Tipps & Grenzen

- Die Hotspot-Metrik ist nur so gut wie der Versionsstand des Systems:
  Versionen entstehen vor allem bei Transportfreigaben – auf einem frisch
  aufgesetzten System bleibt die Historie dünn.
- Analysierbar sind Objekte mit Quelltext (Klassen, Programme, Interfaces,
  CDS Views) – andere Treffer werden mit Hinweis übersprungen.
- Der Quelltext bleibt nur während der Sitzung im Speicher – ein
  aufgehobener Lauf enthält ausschließlich die Metriken, nie den Code.
- „Verwendungen laden" stellt je Objekt eine Anfrage an das System –
  bei großen Paketen entsprechend Zeit einplanen (abbrechbar).
