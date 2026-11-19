# Architektur-Studio

Ein Arbeitsplatz für Workshops, Übersichten und Anleitungen. Ein **Workspace** besteht aus
mehreren **Sheets** (Reiter unter der Fläche, wie in Excel). Auf jedem Sheet liegen Rahmen,
Texte, Post-its und **lebende Karten**, die direkt in BDT springen. Früher hieß die Kachel
„EA-Whiteboard“.

## Voraussetzungen

- Ein Projekt. Kein SAP-Endpunkt nötig.
- Für Asset-Karten ein Asset-Universum.

## Typischer Ablauf

Die Kachel öffnet mit der **Liste der Workspaces** des Projekts (Karten mit Name,
Beschreibung, Sheets und Änderungsdatum, Suche oben). Ein Klick öffnet den Workspace mit
seinen Sheets, der Zurück-Pfeil oben links führt wieder zur Liste. Das Musterprojekt
„Sascha“ bringt einen fertigen Workspace mit; alte EA-Whiteboards stehen mit Hinweis in
der Liste und werden beim ersten Speichern zum Workspace.

1. „Neuer Workspace“ anlegen und Sheets nach Thema benennen (Doppelklick auf den Reiter).
2. Rahmen für Bereiche anlegen, Überschriften und Texte (Markdown) dazulegen.
3. Lebende Karten einfügen: **Kachel** (mit eigenen Parametern, z. B. `view=stories`),
   **Objekt der Wissensablage** (Persona, Story, Spezifikation, UI-Mockup …), **Asset**, **Link**.
4. **Anleitung** einfügen: eine Zeile je Schritt, optional mit Sprungziel am Zeilenende
   (`-> tile:story-studio?view=stories`, `-> info:<Objekt>`, `-> url:https://…`).
   Die Auswahlfelder im Dialog hängen ein Ziel an.
5. Speichern – der Workspace und jedes Sheet landen in der Wissensablage.

## Funktionen im Detail

- **Öffnen ↗** auf jeder Karte und an jedem Anleitungsschritt öffnet das Ziel in einem neuen Tab.
- Karten speichern nur den Verweis. Titel und Beschreibung kommen beim Anzeigen aus BDT; ein
  gelöschtes Ziel erscheint als Hinweiskarte.
- **Rahmen** nehmen beim Verschieben ihren Inhalt mit. Größe aller Flächen-Elemente per Ziehen
  an den Ecken (Element auswählen).
- **Layout-Rahmen:** Im Rahmen-Dialog wählst du die Anordnung des Inhalts – frei, von links nach
  rechts, von oben nach unten oder Raster. Ein Layout-Rahmen ordnet alles, was in ihm liegt, sofort
  an, auch wenn du etwas hineinziehst oder herausnimmst. Die Reihenfolge bestimmst du durch Ziehen
  (weiter nach links bzw. oben = früher). Ist der Rahmen markiert, landen neu eingefügte Karten,
  zum Beispiel mehrere Assets auf einmal, direkt in ihm. Der Rahmen wächst mit.
- **Rückgängig/Wiederholen** (Kopfleiste oder Strg+Z/Strg+Y) gilt für alle Änderungen auf dem
  Sheet, nicht nur für KI-Änderungen, je Sheet bis zu 100 Schritte. Nicht zurückgenommen werden
  Beziehungen in der Asset-Verwaltung, Kommentare und Einstellungen des Workspace.
- **Mehrere Elemente markieren:** Strg+Klick oder Umschalt+Klick nimmt ein Element dazu oder
  heraus, Umschalt+Ziehen auf der leeren Fläche zieht einen Auswahlrahmen auf, Strg+A markiert
  alles. Markierte Elemente verschiebst du gemeinsam.
- **Ausrichten** (Kopfleiste, ab zwei markierten Elementen): links, zentriert, rechts, oben,
  Mitte, unten; ab drei Elementen auch gleichmäßig verteilen.
- **Format übertragen** (Farbeimer): eine Karte markieren und klicken, um ihr Format
  aufzunehmen, dann Zielkarten derselben Art markieren und erneut klicken. Esc verwirft das
  aufgenommene Format. Gilt für Notizen (Farbe, Form), Textkarten, Rahmen und Asset-Karten.
- **Text direkt auf der Fläche:** Doppelklick auf ein Post-it oder eine Textkarte (oder markieren
  und Eingabetaste/F2) öffnet ein Schreibfeld direkt auf der Karte. Die kleine Leiste darüber kennt
  fett, kursiv, unterstrichen und Aufzählung (auch Strg+B/Strg+I/Strg+U; eine Zeile mit „- "
  beginnt eine Aufzählung, die Eingabetaste setzt sie fort). Klick daneben oder Strg+Eingabe
  übernimmt, Esc verwirft. „⋯" öffnet den bisherigen Dialog für Form, Farbe und Größe, ebenso
  Alt+Doppelklick.
- **Vollbild-Arbeitsmodus:** „Vollbild" in der Kopfleiste (oder F) blendet alles außer der Fläche
  aus. Die Bedienung liegt in Leisten an den Ecken: oben links Workspace, Rückgängig und Speichern;
  links die Einfüge-Gruppen als ausklappbare Panels; oben rechts Kommentare, Workshop, Präsentieren,
  Eigenschaften und KI-Chat; unten links Sheet wechseln und Navigator; unten rechts Darstellung,
  Zeitleiste und Browser-Vollbild. Über markierten Elementen erscheint eine Leiste zum Ausrichten,
  Gruppieren, Format übertragen und Löschen. Esc schließt ein offenes Panel, F oder der Knopf oben
  links führt zurück. Präsentieren läuft immer in diesem Modus. Verwaltung (Vorlagen, Import,
  Sortieransicht, MCP-Kanal) bleibt im normalen Modus.
- **Markdown-Karten (Begleitdokumente):** „Neue Markdown-Karte …" in der Gruppe „Begleitdokumente"
  legt ein echtes Markdown-Dokument in der Wissensablage an und zeigt es als Karte mit gerendertem
  Inhalt. Doppelklick schreibt direkt auf der Karte (wie bei Post-its); gespeichert wird beim
  Übernehmen sofort in der Wissensablage. Neue Dokumente landen im Ordner mit dem Namen des
  Workspace und lassen sich danach frei einsortieren – die Karte verweist über die Id und bricht
  nie; die Liste „Begleitdokumente" zeigt sie weiter an, egal wo sie liegen (in der Wissensablage
  steht „Erfasst im Workspace"). Wurde das Dokument inzwischen anderswo geändert (z. B. im
  Markdown-Editor), fragt das Studio nach: als neues Dokument speichern, überschreiben oder
  verwerfen; der Markdown-Editor fragt umgekehrt ebenso. „Notizen als Protokoll sammeln" macht aus
  markierten Post-its ein Dokument (Lesereihenfolge, ein Punkt je Notiz, je Rahmen eine
  Überschrift); „In Notizen aufteilen" legt die Aufzählungspunkte einer Markdown-Karte als Post-its
  daneben. Der Workspace muss dafür einmal gespeichert sein.
- **Schnellansicht („Inhalt"):** „◧" an einer Markdown-Karte öffnet das Dokument im Reiter „Inhalt"
  des Seitenpanels (im Vollbild breit über der Fläche, oben rechts „Inhalt") – mit dem vollen
  Markdown-Editor, ohne Tab-Wechsel. „Speichern" schreibt in die Wissensablage; schließt du mit
  ungespeicherter Änderung, fragt das Studio (speichern, verwerfen oder offen lassen). Unter
  „Karte zeigt" wählst du einen Abschnitt: die Karte zeigt dann nur diesen Teil des Dokuments –
  so kann dasselbe Dokument mehrfach in verschiedenen Ausschnitten auf Sheets liegen.
  Doppelklick auf eine solche Karte öffnet die Schnellansicht am Abschnitt. Wird ein Dokument
  anderswo gespeichert (Markdown-Editor in einem anderen Tab, KI über einen MCP-Kanal), zeichnen
  sich alle Karten dieses Dokuments sofort neu; ein offener Markdown-Editor lädt die neue Fassung
  nach, solange dort nichts Ungespeichertes steht. Die Liste „Begleitdokumente" zeigt jetzt
  Dokumente jedes Typs. BPMN-Diagramme zeigen auf der Karte ein Vorschaubild und öffnen sich mit
  „◧" ebenfalls in der Schnellansicht (voller BPMN-Editor).
- **Legende und Notizen als Assets:** Unter „Assets › Legende …" legst du fest, was Form und Farbe
  einer Notiz bedeuten – z. B. Kreis = Use Case, blaues Post-it = Prozess, dazu optional ein
  Feldwert wie „Workshop-Status: offen". „Kombinationen dieses Sheets ergänzen" trägt alle
  vorkommenden Formen und Farben als Zeilen ein. Die Legende erscheint als Kasten auf dem Sheet
  (Klick klappt zu, Doppelklick öffnet die Pflege). „Notizen als Assets übernehmen …" nimmt die
  markierten Notizen (ohne Auswahl alle des Sheets), zeigt eine Prüfliste mit Titel, Typ, Feldwert
  und Verbindungen und schreibt erst nach „In die Assets schreiben". Danach liegen an Stelle der
  Notizen Asset-Karten; Verbindungen zwischen den Notizen werden zu Beziehungen, wenn der Typ
  passt. Notizen ohne Bedeutung in der Legende bleiben Notizen.
- **Live-Session (BDT Hub):** „Live" in der Werkzeugleiste (im Vollbild oben rechts) gibt das
  aktive Sheet frei. Teilnehmer brauchen kein Projekt und kein Konto: Code, QR-Code oder Link
  genügen (oder die Kachel „An Sitzung teilnehmen"). Sie sehen das Sheet nur lesend, auch
  Sheet-Wechsel und Änderungen, und folgen deinem Bildausschnitt. Mit „Ansicht sperren" können
  sie nicht selbst schieben oder zoomen; sonst dürfen sie sich umsehen und mit „Folgen" zurück.
  Alle Mauszeiger sind für alle sichtbar. Gespeichert wird nur bei dir; „Sitzung beenden"
  macht den Code ungültig. Eingebettete Inhalte (z. B. ein laufender Story-Player) siehst nur
  du. Braucht einen BDT-Hub-Endpunkt mit Mitgliedschafts-Key und das Häkchen unter
  „Erweiterte Verwendung".
- **Tastenkürzel:** N legt ein gelbes Post-it an, T einen Text – beide kannst du sofort
  beschreiben; Umschalt+N bzw. Umschalt+T öffnen den Dialog. R legt einen Rahmen an, Strg+G gruppiert. Die vollständige Liste zeigt der Knopf mit der Tastatur in der
  Kopfleiste.
- **Kreise** bleiben kreisrund, auch beim Ziehen an den Ecken.
- Die **Schriftfarbe** von Textkarten ohne eigene Farbe richtet sich nach dem Hintergrund darunter
  (Rahmen oder Sheet), damit Text auch im dunklen Design lesbar bleibt.
- **Navigator** (links) listet die Rahmen des Sheets; ein Klick fliegt hin.
- **Präsentieren** blendet alles außer der Fläche aus und blättert von Rahmen zu Rahmen
  (Pfeiltasten, Esc beendet). Häkchen in Anleitungen bleiben bedienbar.
- **Assets verbinden:** vom Anfasser einer Asset-Karte zur anderen ziehen. Ein Dialog bietet die
  erlaubten Beziehungstypen an; „Anlegen“ schreibt die Beziehung sofort in die Asset-Verwaltung.
  Gibt es sie schon, wird sie nur gezeigt. Einen Pfeil zu entfernen löscht die Beziehung nicht.
  Pfeile zu anderen Karten sind Anmerkungen.
- **Typen verbinden:** Verbindest du zwei Asset-Typen, fragt ein Dialog nach dem Beziehungstyp
  (oder „Nur Anmerkung“) und bietet bei Bedarf an, die erlaubten Kombinationen zu ergänzen.
- **Konfiguration** (Kopfleiste) enthält die Hintergrundfarbe des Sheets und „Beziehungen
  einblenden …“. Das zeigt Beziehungen, die zwischen den Assets des Sheets schon
  bestehen, aber noch keinen Pfeil haben. Gestrichelte Pfeile „nicht angelegt“ aus älteren Boards
  legst du per Doppelklick an.
- **Vorschau:** ⓘ auf einer Asset-, Objekt- oder Kachel-Karte zeigt die wichtigsten Felder und bei
  Assets die Beziehungen; „Öffnen“ springt in die Kachel. Im Whiteboard gibt es dieselbe Vorschau
  für Post-its, die du aus einem Asset eingefügt hast.
- **Assets einfügen:** Die Asset-Typen stehen nach ihrer Gruppierung aus der Asset-Verwaltung; ein
  Klick auf einen Typ öffnet die Auswahl schon gefiltert; „Alle Treffer auswählen“ wählt die ganze
  gefilterte Liste. „Neues Asset …“ legt ein Asset mit Typ,
  Titel und Beschreibung direkt an und setzt es auf das Sheet. Für alles Weitere öffnet „In der
  Asset-Verwaltung pflegen“ einen neuen Tab; kommst du zurück, lädt das Studio die Assets neu.
- **Bilder:** „Aus der Bild-Bibliothek …“ legt ein Bild als Karte ab, „Bild hochladen …“ speichert
  neue Bilder in der Bild-Bibliothek. Lädst du ein Bild hoch, das schon dort liegt, wird das
  vorhandene genommen. Doppelklick auf die Karte ändert Bildunterschrift und Darstellung,
  „⤢“ zeigt das Bild groß.
- Ein altes EA-Whiteboard öffnet als Workspace mit einem Sheet; beim Speichern entsteht ein
  neuer Workspace, das Original bleibt erhalten.

## Tipps & Grenzen

- Im **Musterprojekt Sascha** liegt der Workspace „Sascha – vom Problem zur Lösung“ mit
  Überblick, „Ein Tag mit Sascha“ (Bilder aus der Schulung), Schritt-für-Schritt-Anleitungen,
  Werkzeugkoffer mit Landkarte und Architektur, „Systemlandschaft im Zeitverlauf", einer Situations-Übung, „MCP Beispiele“ (Eingaben
  für einen KI-Chat je Bereich) und Kachel-Übersicht.
- Link-Karten laden die Seite nicht; sie zeigen, was du einträgst.
- **Personas und Stories:** Unter „Story-Studio" fügst du eine Persona ein – als Figur (ⓘ öffnet den
  Steckbrief mit Zielen, Frustrationen und Zitat) oder gleich als Steckbrief-Karte, auf Wunsch mit anderem
  Gesichtsausdruck. Eine Story-Karte zeigt Titel, Szenen und Figuren; „▶ Abspielen" startet den Player direkt
  auf dem Board, „⤢" groß mit Erzählerstimme.
- **Bild tauschen:** Doppelklick auf eine Bild-Karte zeigt das aktuelle Bild; „Aus der Bild-Bibliothek …"
  oder „Hochladen …" wählt ein anderes. Die Karte passt ihre Höhe an das neue Bild an.
- **Lifecycle und Zeitregler:** Markiere eine Asset-Karte und wähle unten „Lifecycle …", um die
  Startdaten der Phasen einzutragen (Geplant, Im Aufbau, Aktiv, Im Auslauf, Außer Betrieb). Schalte
  „Zeit" ein und zieh den Schieber oder drück ▶ – die Karten zeigen ihre Phase. „vergleichen mit" markiert,
  was seit einem anderen Zeitpunkt neu (+), entfallen (–) oder in eine andere Phase gewechselt ist (↻).
  Je Sheet wählst du, ob die Phase als Farbe, nur als Rand oder durch Ausblenden gezeigt wird.
  Die Daten liegen im Datenmodell „BDT Lifecycle" und sind auch im Asset-Explorer pflegbar.
- **Darstellung:** In der Seitenleiste unter „Darstellung" legst du Designs an. Ein Design „am Asset-Typ"
  gilt für alle Karten dieses Typs, ein Preset ziehst du auf eine Karte oder wählst es als Sheet-Design.
  Je Design bestimmst du Hintergrund, Rahmen, Schrift, Dichte (Kompakt/Normal/Detail) und welche Felder
  die Karte zeigt – auch Werte aus den Datenmodellen der Assets. Spezifisches gewinnt: Karte vor Preset
  vor Sheet-Design vor Design am Typ vor der Typ-Farbe. Markierte Karte → „Markierte Karten darstellen …"
  zeigt, woher ihre Darstellung kommt.
- **Linsen und Heatmap:** „Linse → Neu …" wählt Bedingungen (Typ, Phase, Tag, Datenmodell-Werte) und die
  Wirkung: Treffer hervorheben, Rest abblenden oder ausblenden. Eine Heatmap färbt die Karten nach einem
  Zahlenwert von grün nach rot. Linsen gehören zum Workspace und wirken auf jedem Sheet.
- **Gerenderte Bereiche:** Unter „Assets" → „Gerenderter Bereich …" baust du eine Ansicht aus den Asset-Daten:
  Landscape (Assets in Gruppen – die Gruppen kommen aus Beziehungstypen, die als Strukturbeziehung markiert
  sind), Matrix (zwei Asset-Typen, die Zelle zeigt die Beziehungen), Lifecycle-Roadmap (Balken je Phase,
  der Zeitpunkt des Zeitreglers als Linie) oder Abhängigkeitsgraph (ab einem Start-Asset, 1–4 Schritte).
  Der Bereich merkt sich sein Ergebnis; ⟳ berechnet ihn neu. „Einfrieren" wandelt ihn in normale Rahmen,
  Karten, Pfeile, Balken oder eine Tabelle, die du danach frei bearbeiten kannst. Doppelklick ändert die Abfrage.
- **Szenarien:** „Szenarien …" in der Zeitleiste legt Was-wäre-wenn-Stände an (z. B. „CRM-Ablösung ein Jahr später").
  Ist ein Szenario gewählt, ändert „Lifecycle …" nur das Szenario; der Umschalter wechselt zwischen Ist-Stand und
  Szenario. Der Dialog zeigt alle Abweichungen mit der Phase am gewählten Zeitpunkt, als Markdown kopierbar, und
  übernimmt sie nach einem Probelauf in die Assets.
- **Link-Karten:** „⟳ Daten holen" liest Titel, Beschreibung und Datum der Seite. Eigene Angaben im Link-Dialog
  gewinnen. Ändert sich die Seite, zeigt die Karte „● geändert" (alter Stand im Tooltip) bis „Gesehen". Nach dem ersten
  Abruf aktualisiert der Workspace seine Link-Karten beim Öffnen; abschalten im Link-Dialog (Doppelklick auf die Karte).
- **Weitere Karten:** Kommentar (Anmerkung mit Autor und Datum, abhakbar, zählt nicht als Inhalt), Typ-Karte (Asset-Typ
  oder Beziehungstyp mit Sprung in die Pflege), Liste von Assets eines Typs (Klick je Zeile öffnet das Asset) und
  Markdown-Starter: „Neues Dokument ▸" öffnet den Markdown-Editor mit Vorlage und Namen wie „{Datum} {Workspace}
  Protokoll"; nach dem Speichern liegt das Dokument als Karte neben dem Starter.
- **Kachel mit Profil:** In einer Kachel-Karte öffnet der Parameter `profile=<Name>` die Kachel direkt mit einem
  gespeicherten Suchprofil.
- **KI im Studio:** Ist ein Workspace offen, steht im KI-Chat der Server „Architektur-Studio: …" bereit (für externe KI
  über den Kanal-Knopf in der Kopfzeile, /mcp/ea). Die KI kann lesen, Lücken im Modell finden und aus dem Board ein
  Protokoll schreiben, das in der Wissensablage landet. Ändern darf sie erst mit dem Häkchen „KI darf das
  Architektur-Studio ändern" (Einstellungen → MCP → Freigaben): Notizen, Rahmen, Karten vorhandener Assets, Pfeile und
  gerenderte Bereiche – nie löschen, nie Assets anlegen. „KI-Änderung rückgängig" nimmt jede Änderung zurück, gespeichert
  wird nur über „Speichern". Im Rahmen-Dialog legst du fest, ob ein Rahmen für die KI gesperrt oder als einziger
  Bereich freigegeben ist.
- **Vorlagen:** In der Seitenleiste unter „Vorlagen“ legst du Sheets aus einer Vorlage an, fügst einen fertigen
  Bereich (z. B. SWOT oder Architekturentscheidung) ein oder speicherst den Workspace, das aktuelle Sheet oder einen
  markierten Rahmen als eigene Vorlage. Platzhalter wie {Kunde} füllst du beim Anwenden aus, {Datum} setzt BDT selbst.
  Assets und Personas merkt sich eine Vorlage über ihren Namen und sucht sie im jeweiligen Projekt; was fehlt, erscheint
  als rote Karte „Nicht gefunden“. In der Workspace-Liste startet „Aus Vorlage …“ einen neuen Workspace.
- **Präsentieren und Workshop:** Doppelklick auf einen Rahmen legt fest, ob er beim Präsentieren eine Folie ist,
  auf welchen Tag der Zeitregler dabei springt und wie lange die Timebox dauert. In der Seitenleiste unter
  „Workshop" findest du den Timer, die Abstimmung mit Punkten (Klick auf eine Karte gibt einen Punkt,
  Alt+Klick nimmt ihn zurück, „Ergebnis …" zeigt die Rangliste), den Parkplatz für Themen, die gerade nicht
  dran sind, sowie „Agenda-Sheet …" (ein Rahmen je Punkt mit Timebox) und „Breakout-Sheets …" (Kopien für
  Arbeitsgruppen). Beim Präsentieren hat die Leiste unten zusätzlich Timer, Abstimmung und Parkplatz.
- **Folien exportieren:** „Folien als PDF …" öffnet den Druckdialog (eine Seite je Rahmen), „Als
  Marp-Foliensatz" öffnet die Folien im Marp-Editor. Beide zeigen eine vereinfachte Darstellung der Rahmen
  (Kästen mit Titeln, Farben, Bildern und Linien).
