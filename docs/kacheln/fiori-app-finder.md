# Fiori App Finder

Findet zur klassischen SAP-GUI-Transaktion (z. B. VA01) die passende Fiori-App, liefert einen
„Will ich haben"-Steckbrief für die SAP Basis und wertet den Bestand aus (Analyse, Release-Vergleich).

## Voraussetzungen

- Kein Projekt, kein SAP-Endpunkt, kein Secret nötig.
- Einmalig einen Bestand laden: die Kachel liest danach ausschließlich aus dem lokalen Bestand und
  funktioniert offline. Quellen: die öffentliche klassische SAP Fiori Apps Reference Library (kein
  Login) oder die neue FAL in SAP Cloud ALM (Anmeldung im Browser).

## Typischer Ablauf

1. **Bestand verwalten** → **Releases hinzufügen …**: Releases wählen (vorbelegt: neuestes S/4HANA
   Private Cloud/On-Premise und Public Cloud), **Laden**. Ein Release enthält die komplette App-Liste;
   mehrere Releases lohnen sich vor allem für den Release-Vergleich.
2. **Zurück zur Suche**: Transaktion, App-Name, App-ID, OData-Service oder Rolle eingeben, **Suchen**.
   Ohne gewähltes Release erscheint jede App einmal (neuester geladener Stand); „Alle Release-Stände
   zeigen" listet sie je Release.
3. Zeile anklicken: Steckbrief mit Software-Komponenten, OData-Services, Rollen, Kataloge, Intents,
   Links. **Zusatzdetails laden** ergänzt ICF-Knoten, Notes, Vorgänger/Nachfolger.
   Dazu Links zu Screenshots, Videos und Präsentationen; **Bilder anzeigen** lädt die Screenshots
   (von support.sap.com) erst auf Klick.
4. Mehrere Zeilen markieren, **„Will ich haben" (Auswahl)**: Sammelauftrag als Markdown.
5. **Analyse**: Release und Anwendungskomponenten (z. B. `SD`, `SD, LE-SHP`, `MM-PUR*`) wählen,
   **Analysieren**. Übersicht nach UI-Kategorie/-Technologie, App-Typ, Komponente; Heatmap
   Komponente × UI (Zelle anklicken zeigt die Apps); Release-Vergleich zweier Releases (neu,
   entfallen, geändert, Fiori-Anteil).

## Bestand verwalten

- Je Release: Quelle, Anzahl, Status, Ladezeit. Markierte Releases **synchronisieren** (neu laden)
  oder **löschen**.
- **Exportieren** sichert die markierten Releases (ohne Markierung alle) als Datei, **Importieren**
  ersetzt nur die Releases aus der Datei – alle anderen bleiben erhalten. Die klassische Bibliothek
  wird von SAP abgekündigt: rechtzeitig exportieren.
- **MCP-Server einrichten …** stellt den Bestand einer KI (z. B. Claude Code) zur Verfügung: du lädst
  eine Serverdatei und den Snapshot herunter und bekommst die fertige `.mcp.json` bzw. den Befehl
  `claude mcp add …`. Der Server läuft lokal mit Node.js, liest nur die Snapshot-Datei und greift auf
  kein Netzwerk zu. Nach einem neuen Export den Server neu starten.
- **Im KI-Chat:** über „MCP-Server für diesen Chat" den Eintrag „Fiori App Finder (lokal)" einschalten.
  Die KI befragt dann den hier geladenen Bestand direkt im Browser, ohne Datei und ohne Netzwerk.
  Das klappt nur mit einem OpenAI-kompatiblen KI-Anbieter (z. B. Ollama, LM Studio); sehr kleine
  lokale Modelle sind mit Werkzeugen langsam.

## Begehbare App-Stadt

In der **Analyse** nach „Analysieren" in der Gruppe „Begehbare Stadt" auf **Als begehbare Stadt betreten** klicken. Die Apps der
Analyse (Release und Komponentenfilter) werden zur Stadt:

- **Stadtteile** sind die Anwendungskomponenten der ersten Ebene (SD, MM …), darin
  **Wohngebiete** (SD-SLS) und **Straßenzüge** (SD-SLS-SO). Die größten stehen am Stadteingang.
- Jedes **Gebäude** ist eine Anwendungskomponente, jedes **Stockwerk** eine App mit Name und
  App-ID in Klammern (F1234). Die Farbe zeigt die UI-Technologie: grün Fiori elements, blau Fiori/SAPUI5,
  türkis analytisch, violett Web Client, orange Web Dynpro, grau SAP GUI.
- **Stockwerk anklicken** öffnet den Steckbrief, „Zusatzdetails laden" ergänzt OData, ICF, Notes sowie
  Links zu Screenshots, Videos und Präsentationen. „Bilder anzeigen" zeigt die Screenshots.
  **Dach anklicken** listet alle Apps des Gebäudes.
- Bewegen: Pfeiltasten oder W-A-S-D, Maus ziehen zum Umsehen, Bild ↑/↓ zum Fliegen, Boden
  anklicken zum Springen. **Umschalt** dazu halten macht schneller, je länger, desto mehr;
  nach dem Loslassen rollt man aus. Aus der Luft zeigen gelbe Kürzel die Stadtteile (SD, MM …). Mit VR-Brille über „Enter VR".
- **Einkaufsliste:** Im Steckbrief „Will ich haben" (in der Stadt und in der Kachel) oder in der
  Suche „Auf Einkaufsliste" für markierte Zeilen. „Einkaufsliste (n)" öffnet den
  Aktivierungsauftrag. In der Stadt tragen vorgemerkte Stockwerke 🛒.
- **Rundgang:** In der Stadt Stadtteil, UI-Technologie (beim Vergleich auch Status) oder „Nur
  Einkaufsliste" wählen und „Rundgang starten". ◀ ▶ fliegen die Gebäude an, „Apps" zeigt die
  passenden Apps, eine Notiz je Stopp landet im „Protokoll" (Markdown, exportierbar).
- **Aktivierung im System:** In der Analyse unter „Begehbare Stadt" mit gewähltem SAP-Endpunkt
  „Aktivierung im System prüfen". BDT liest dafür per Freestyle-SQL, welche UI-Knoten (ICF) aktiv
  und welche OData-Services registriert sind. In der Stadt schaltet dann „Nacht" die Ansicht um:
  aktive Apps leuchten, teilweise aktive halb, der Rest bleibt dunkel.
- **Vergleich als Stadt:** Unter **Betrachtung** „Zwei Releases vergleichen" wählen, von/nach
  Release setzen, „Analysieren", dann die Stadt betreten. Neue Apps haben einen gelben Rahmen (★),
  geänderte orange Streben (⚒), entfallene sind rot gestrichelt und durchsichtig (✝). Mit „Nur
  Veränderungen zeigen" bleiben unveränderte Apps weg.
- **max. Apps** (Gruppe „Begehbare Stadt") begrenzt die Größe (Standard 2.000). Ohne Komponentenfilter füllen die
  größten Komponenten die Grenze – für einen Rundgang besser auf ein Modul einschränken.

## Tipps & Grenzen

- Transaktionscodes werden tokengenau abgeglichen (VA01 findet nicht FMVA01).
- „Möglicher Nachfolger" und „Fiori-Alternative" im Release-Vergleich sind eine Heuristik über
  gemeinsame Transaktionscodes, keine SAP-Angabe.
- Die API ist undokumentiert; Inhalte sind Englisch. Tabellennamen finden hier nichts – der Weg
  dahin führt über den Datenkatalog.
