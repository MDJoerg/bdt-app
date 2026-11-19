# abapGit Studio

Öffnet abapGit-ZIP-Archive (z. B. von GitHub oder dotabap.org heruntergeladen) komplett
lokal im Browser: Paketbaum, Objekte nach Typ gruppiert, Quelltext- und Metadaten-Ansicht
je Objekt sowie eine Paket-Seite mit Dashboard, Sprachen-Übersicht und exportierbarer
Stückliste. Dazu ein Umbenennungs-Wizard fürs Einspielen unter anderem Namen, eine
Übersetzungs-Workbench sowie eine offline laufende Abhängigkeits-Analyse.
[abapGit](https://abapgit.org) ist das Standard-Werkzeug der SAP-Community für
Open-Source-ABAP-Projekte – wer nicht direkt aus dem SAP-System auf Git zugreifen kann,
nutzt den Offline-Weg über ZIP-Dateien. Genau diese Dateien macht die Kachel durchsuchbar.

## Voraussetzungen

- Keine – kein SAP-Endpunkt, kein Projekt nötig. Alles läuft lokal im Browser, es wird
  nichts hochgeladen. Nur für „Als Datensatz im Daten-Studio öffnen" brauchst du ein
  Projekt in der Fußzeile (das Dataset muss ja irgendwo zugeordnet werden), und nur für
  die optionale Existenzprüfung in der Abhängigkeits-Analyse einen SAP-Endpunkt.

## Typischer Ablauf

1. Ein abapGit-Archiv öffnen – drei Wege stehen zur Wahl:
   - **„ZIP laden …"**: ein vorher heruntergeladenes ZIP hochladen (Mehrfachauswahl möglich).
   - **„Von Git-URL laden …"**: eine github.com-Adresse, ein `owner/repo`-Kürzel oder eine
     direkte ZIP-URL eintippen – der Standard-Branch wird automatisch ermittelt und direkt
     heruntergeladen. Für einen anderen Branch eine URL mit `/tree/<branch>` verwenden.
   - **„dotabap-Marktplatz …"**: die öffentliche Projektliste von
     [dotabap.org](https://dotabap.org) durchsuchen (Freitextfilter, optional „Verwandte
     Projekte einbeziehen") und ein Projekt direkt per Klick auf „Laden" öffnen.
2. Links im Baum navigieren: Archiv → Pakete → Objekttyp → Objekt.
4. Am Archiv- oder einem Paket-Knoten die drei Reiter nutzen: **Dashboard**
   (Kennzahlen + Objekte je Typ und je Unterpaket als Diagramm, dazu die Test-Quote:
   wie viele Klassen, Programme und Funktionsgruppen Testklassen enthalten), **Sprachen**
   (Übersetzungsabdeckung je Sprache) und **Stückliste** (filterbare Tabelle aller
   Objekte – ein Zeilenklick öffnet das Objekt). Der Umschalter „Unterpakete
   einbeziehen" wirkt auf alle drei Reiter.
5. Beim Einzelobjekt die Reiter „Quelltext", „Metadaten" und „Rohdateien" ansehen
   (einzelne Dateien lassen sich dort auch herunterladen).
6. Über die Archiv-Kopfzeile (oder per Rechtsklick im Baum) eine Kopie anlegen, das
   Archiv mit einem anderen vergleichen oder es wieder schließen – s. eigener Abschnitt
   „Archiv-Werkzeuge" unten.
7. An der Archiv-Wurzel „Umbenennungs-Wizard" öffnen, um das Archiv (z. B. vor dem
   Einspielen beim Kunden) umzubenennen – s. eigener Abschnitt unten.
8. Über „Übersetzungs-Workbench" (Archiv-, Paket- oder Objekt-Kopfzeile bzw. den
   Sprachen-Tab) Übersetzungen direkt im Archiv lesen und bearbeiten – s. eigener
   Abschnitt „Übersetzungs-Workbench" unten.
9. Über „Abhängigkeiten analysieren" (Archiv-, Paket- oder Objekt-Kopfzeile) prüfen,
   was das Archiv außerhalb seiner selbst nutzt – s. eigener Abschnitt
   „Abhängigkeits-Analyse" unten.

## Umbenennungs-Wizard

Der typische Anlass: du hast mit KI-Unterstützung auf deinem eigenen System
entwickelt (z. B. `ZSD_*`) und willst die Lösung unter einem anderen Namen
(z. B. `ZOTC_*`) beim Kunden per abapGit einspielen, weil dort nicht mit KI
entwickelt werden kann.

1. **Regeln erfassen:** „Namensraum" ersetzt einen verankerten Präfix
   (z. B. „Z" → „Y" oder einen echten Namensraum „/ABC/" → „Z"), „Substring"
   ersetzt die erste Fundstelle irgendwo im Namen (z. B. „ZSD_" → „ZOTC_").
   Bei mehreren passenden Regeln gewinnt die mit dem längsten „Von"-Wert.
   Optional lässt sich über „Gespeicherte Zuordnung laden …" eine frühere
   Zuordnung als Ausgangspunkt übernehmen (praktisch für ein zweites, darauf
   aufbauendes Archiv).
2. **„Vorschau berechnen"** zeigt das abgeleitete Objektverzeichnis (Alt →
   Neu je Objekt), Konflikte (zu lange Namen, zwei Objekte landen beim
   gleichen Ziel) sowie eine Datei-Vorschau. In der Tabelle lässt sich jede
   Zeile per Hand anpassen: den vorgeschlagenen neuen Namen ändern oder eine
   Zeile über „Übernehmen" ganz vom Lauf ausschließen.
3. Ein Klick auf eine Zeile der Datei-Vorschau zeigt den Zeilen-Vergleich der
   betroffenen Datei.
4. **„Lauf ausführen"** (mit einer Kennzahlen-Bestätigung) benennt Dateien
   *und* Inhalte (Code, XML, JSON, Übersetzungsdateien) im gesamten Archiv
   um. Häkchen „Als neues Archiv anlegen" behält das Original zusätzlich.
5. **„Zuordnung speichern"** legt die verwendeten Regeln + das konkrete
   Objektverzeichnis als Infoobjekt in deiner Wissensablage ab – Grundlage
   für „vorher anwenden" bei einem später aufeinander aufbauenden Archiv.
6. In der Archiv-Kopfzeile steht jetzt auch „Als ZIP exportieren" – lädt das
   komplette Archiv (original oder umbenannt) als eine einzige ZIP-Datei
   herunter, bereit zum Einspielen per abapGit.

## Archiv-Werkzeuge

- **Kopie anlegen:** legt eine unabhängige Kopie des Archivs im Baum an (Name
  editierbar, Vorschlag „‹Archiv› (Kopie)"). Änderungen an der Kopie – z. B. ein
  Umbenennungs-Lauf – wirken sich nicht auf das Original aus.
- **Vergleichen mit …:** vergleicht das Archiv objektweise mit einem anderen bereits
  geladenen Archiv (Objektname + -typ, unabhängig vom Paket). Vier Gruppen: „Nur in
  Archiv A", „Nur in Archiv B", „Gleich" und „Unterschiedlich" – Letztere zeigt zu jedem
  unterschiedlichen Objekt einen Zeilen-Vergleich je betroffener Datei, die anderen
  Gruppen öffnen direkt das jeweilige Objekt. „Seiten tauschen" dreht den Vergleich um.
- **Objekt/Paket entfernen:** über das Kontextmenü an einem Paket- oder Objekt-Knoten
  (oder den Knopf in dessen Kopfzeile) lässt sich ein einzelnes Objekt oder ein ganzes
  Paket samt Unterpaketen wieder aus dem Archiv nehmen – mit einer Bestätigung, wie viele
  Objekte und Dateien betroffen sind. Dateien ohne erkanntes abapGit-Namensmuster (z. B.
  eine lose `.txt`-Datei) bleiben dabei unangetastet.
- **Inhalt entfernen …:** an der Archiv-Wurzel oder an einem Paket (Kopfzeile oder
  Kontextmenü). Der Dialog listet die Unterpakete und Objekte dieser Ebene zum Ankreuzen
  (mit Filter und „Alle/Keine/Umkehren"); ein Klick entfernt alles Gewählte auf einmal.
  Unterpakete verschwinden dabei vollständig, auch mit losen Dateien in ihrem Ordner.
- **Als ZIP exportieren:** der Export ist komprimiert und damit etwa so groß wie ein
  von abapGit erzeugtes ZIP.

## Übersetzungs-Workbench

Bearbeitet die i18n-`.po`-Übersetzungsdateien eines Archivs (der neuere, experimentelle
abapGit-Übersetzungsweg, Dateien `<name>.<typ>.i18n.<sprache>.po`) direkt im Browser.
Erreichbar über den Knopf „Übersetzungs-Workbench" in der Archiv-, Paket- oder
Objekt-Kopfzeile, über den Sprachen-Tab (nur wenn dort mindestens eine `.po`-Sprache
gefunden wurde) oder per Rechtsklick im Baum.

1. **Bereich wählen:** ganzes Archiv, ein Paket inkl. Unterpakete oder ein einzelnes
   Objekt (Einzelpflege) – abhängig davon, wo der Knopf geklickt wurde.
2. **Sprache wählen:** bei mehr als einer verfügbaren `.po`-Sprache erscheint zuerst
   ein Auswahldialog, bei genau einer wird direkt geöffnet.
3. Die Tabelle zeigt je Zeile Objekt/Kontext/Quelltext (nicht editierbar) und ein
   editierbares Entwurfsfeld – Status **ok**/**fehlt**/**gleich**/**zu lang** wird
   automatisch berechnet (eine Maximallänge kennt die Workbench nur, wenn eine
   `.po`-Datei einen entsprechenden Kommentar trägt).
4. Eine oder mehrere Zeilen markieren (Auswahlspalte links) und „Auswahl mit KI
   übersetzen" nutzt deine in den Einstellungen konfigurierte KI (lokale Chrome-KI oder
   ein eingerichteter Anbieter) – auch eine einzelne markierte Zeile ist eine gültige
   Auswahl.
5. **„Änderungen speichern"** schreibt nur die geänderten Texte zurück (Kommentare/
   Ursprungstext/alle anderen Einträge bleiben unverändert) und kehrt danach zur
   Archiv-Ansicht zurück. „Änderungen verwerfen" macht alle Bearbeitungen dieser
   Sitzung rückgängig.

**Wichtig:** ältere, direkt ins Objekt-XML eingebettete Übersetzungen (der historische
abapGit-Weg) sind hier NICHT editierbar – sie bleiben nur im Sprachen-Tab als reiner
Sprachnachweis sichtbar.

## Abhängigkeits-Analyse

Beantwortet die Frage „Was nutzt das Archiv außerhalb seiner selbst?" – komplett
offline, ohne SAP-Endpunkt. Erreichbar über den Knopf „Abhängigkeiten analysieren" in
der Archiv-, Paket- oder Objekt-Kopfzeile bzw. per Rechtsklick im Baum (Bereich wie bei
der Übersetzungs-Workbench: ganzes Archiv, ein Paket inkl. Unterpakete oder ein
einzelnes Objekt).

1. Die Kachel durchsucht den Quelltext jedes Objekts nach möglichen Bezeichnern (eine
   textbasierte Heuristik, kein echter ABAP-Parser) und gleicht sie in drei Töpfen ab:
   **intern** (ein Treffer unter den anderen Objekten desselben Archivs), **extern**
   (ein Treffer in einer über die Kachel „Clean Core Radar" importierten
   SAP-Cloudification-Datenbasis – inklusive Cloud-Level und Nachfolgeobjekt, falls
   bekannt) und **unbekannt** (weder noch – vermutlich ein anderes Z-Paket oder ein
   nicht gelistetes SAP-Objekt).
2. Kennzahlen + ein Kreisdiagramm zeigen die Referenzen nach Herkunft; die Tabelle
   zeigt je Objekt die drei Zähler – ein Zeilenklick öffnet die konkreten Namen.
3. **„Als Graph anzeigen"** öffnet die Beziehungen im Graph-Viewer, **„Als Datensatz im
   Daten-Studio öffnen"** sichert die Tabelle als Dataset.
4. Ein eigener Abschnitt listet alle unbekannten Namen (mit Konsumentenzahl). Mit einem
   in der Fußzeile gewählten SAP-Endpunkt lässt sich darüber optional prüfen, ob ein
   Name im System tatsächlich existiert (Typ/Paket, bei installiertem Eclipse/ADT auch
   ein direkter Link).

**Ohne importierte SAP-Cloudification-Datenbasis** landet jede Nicht-interne Referenz
unter „unbekannt" – die Datenbasis stammt aus der Kachel „Clean Core Radar" (Tab
„Datenbasis").

## Funktionen im Detail

- GitHub-Download-ZIPs haben einen zusätzlichen Wurzelordner (`<repo>-<branch>/`) – der
  wird automatisch erkannt und übersprungen.
- Namensräume (`/ABC/…`) werden aus beiden abapGit-Dateinamens-Kodierungen dekodiert.
- Die Archiv-Ansicht zeigt Mastersprache, Ordnermodus, Objekte je Typ sowie ehrlich
  getrennt „sonstige" und „nicht zugeordnete" Dateien.
- Bereits vorhandene Übersetzungsdateien (`….i18n.<sprache>.po`) werden je Objekt als
  Sprache ausgewiesen; der Sprachen-Reiter erkennt zusätzlich Sprachfelder in den
  XML-Metadaten (die Mastersprache zählt dabei bewusst nicht als „Übersetzung").
- Testklassen erkennt das Studio am Quelltext (`FOR TESTING` außerhalb von Kommentaren),
  nicht am Dateinamen – ein leeres `….clas.testclasses.abap` zählt also nicht. Die Stückliste
  zeigt das in der Spalte „Testklassen" (`ja (Klassen, Methoden)`, `nein` oder `–` für Typen,
  die keine Tests enthalten können). Die Zahl der Testmethoden ist eine Schätzung.
- Die Stückliste ist filter- und sortierbar; Export, Sammelkorb und „Als Datensatz im
  Daten-Studio öffnen" nehmen deine Auswahl bzw. die gefilterte Menge mit – die
  Daten-Studio-Übernahme kommt bereits mit fertig klassifizierten Feldern an
  (Dimensionen/Kennzahlen), du kannst dort sofort Diagramme bauen.
- Der Umbenennungs-Wizard zieht bei Funktionsgruppen auch die generierten
  Folgenamen mit (Hauptprogramm `SAPL<Name>`, Top-Include `L<Name>TOP` usw.),
  benennt also nicht nur das Objekt selbst um.
- Treffer innerhalb eines String-Literals (z. B. bei dynamischen Aufrufen wie
  `CALL METHOD ('ZCL_…')`) oder eines Kommentars werden ersetzt, aber in der
  Vorschau nicht gesondert hervorgehoben – bei dynamischen Aufrufen lohnt sich
  ein zweiter Blick in die betroffene Datei.

## Tipps & Grenzen

- **Geladene Archive sind nur für diese Sitzung im Speicher** – ein Seiten-Neuladen
  verwirft sie. Das ZIP selbst bleibt natürlich unverändert auf deiner Platte.
- SAP-Paketnamen stehen nicht absolut im Archiv – sie ergeben sich erst beim Einspielen
  aus dem gewählten Wurzelpaket und dem Ordnermodus. Der Baum zeigt deshalb die
  Ordnernamen plus die Paketbeschreibung. Der Umbenennungs-Wizard benennt deshalb
  bewusst nur Objekt-Dateinamen und -Inhalte um, keine Ordnerpfade.
- Die Sprachen-Erkennung aus den XML-Metadaten ist eine Best-Effort-Heuristik – nicht
  jeder Objekttyp trägt überhaupt übersetzbare Texte, 100 % Abdeckung sind selten.
- Der Download „Von Git-URL laden …"/aus dem dotabap-Marktplatz läuft direkt aus dem
  Browser gegen GitHub – je nach Laufzeitumgebung (Local Bridge/Electron/VS Code) oder
  einer CORS-Blockade in der reinen Chrome-Erweiterung kann das fehlschlagen; dann hilft
  der klassische Weg über „ZIP laden …" mit einer manuell heruntergeladenen Datei.
- Die dotabap-Projektliste enthält nur Projektnamen (kein Beschreibungstext, keine
  Sterne/Lizenz) – der Marktplatz-Filter ist deshalb eine reine Namenssuche.
- Die Abhängigkeits-Analyse ist wie der Umbenennungs-Wizard eine textbasierte
  Heuristik – Kommentare und Zeichenketten werden mitgescannt, ein exakter
  Namensabgleich hält die Fehlerquote aber klein. Objekte ohne eigene Quelltextdatei
  (z. B. reine Metadaten wie Domänen) werden als „ohne Quelltext" ausgewiesen und
  bleiben in der Tabelle außen vor.
