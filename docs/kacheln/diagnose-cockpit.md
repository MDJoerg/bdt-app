# Diagnose-Cockpit

Analysiert die ABAP-Laufzeitfehler (ST22-Dumps) des gewählten SAP-Systems ohne SAPGUI – über
denselben offiziellen ADT-Feed, den auch der Eclipse-Feed-Reader nutzt, rein lesend. Statt einer
rohen Dump-Liste bekommst du ein Dashboard, **Häufungen** („derselbe Fehler n-mal") und ein
Dump-Detail mit Fehleranalyse, Quelltext-Ausschnitt und Aufrufstack.

## Voraussetzungen

- Ein eingerichteter SAP-Endpunkt (ADT). Die normale ST22-Berechtigung eines Entwicklers/Admins
  genügt – die Kachel liest nur, was der Feed für deinen Benutzer freigibt.

## Typischer Ablauf

1. Endpunkt in der Fußzeile wählen, Zeitraum (Standard „Letzte 24 Stunden") und optional einen
   Benutzer setzen, dann „Dumps laden".
2. **Übersicht:** Zeitverlauf (gestapelt nach Fehler-ID), Fehler-ID-Donut, Top-Programme (Pareto),
   Benutzer, Wochentag×Stunde-Heatmap – dazu ein Trend über aufgehobene Läufe.
3. **Häufungen:** gleiche Fehler-ID + Programm + Abbruchstelle werden zu einer Zeile gebündelt
   („47×, 12 Benutzer, zuletzt gestern") – die schnellste Antwort auf „ist das EIN Problem?".
4. Klick auf einen Dump (oder eine Häufung) öffnet das Detail: Was ist passiert?, Fehleranalyse,
   Abbruchstelle, Quelltext-Ausschnitt, Aufrufstack.
5. Aus dem Detail heraus: „In ADT öffnen", Repository-Suche, Verwendungsnachweis, „Enthaltende
   Transporte" (Transport Cockpit) oder „Mit KI erklären".

## Funktionen im Detail

- **Benutzer-Filter:** filtert serverseitig – ideal für „bei Kollegin X knallt es gerade".
- **Max. Dumps:** der Feed liefert 100 Dumps je Seite; ältere Seiten werden bis zur Grenze
  (Standard 500, max. 1000) nachgeladen. Eine Kappung wird sichtbar gemeldet.
- **Explorer:** Baum nach Fehler-ID, Programm oder Benutzer – je Knoten eine gefilterte
  Dump-Tabelle und ein „Arbeitsauftrag"-Export (Markdown-Task-Liste, z. B. für eine KI).
- **Lauf aufheben:** speichert einen kompakten Analyse-Snapshot in der Wissensablage (read-only
  wieder zu öffnen); mehrere Läufe mit demselben Suchprofil ergeben den Trend-Chart. Die
  vollständigen Dump-Texte bleiben bewusst eine Live-Ansicht.
- **Exporte:** Markdown-Report (inkl. Mermaid-Diagramm), Daten-Studio-Datensatz (vorklassifiziert),
  Graph-Viewer (Programm → Fehler-ID), Wordcloud der Kurztexte.
- **„Mit KI erklären":** übergibt die Analyse-Abschnitte des Dumps an den KI-Chat – bewusst nicht
  den vollen Roh-Dump (dessen Parameter können Geschäftsdaten tragen).
- **Weitere Quellen:** drei zusätzliche Reiter derselben ADT-Feed-Familie – **Gateway-Fehlerlog**
  (OData-Frontend-/Backend-Fehler inkl. Service-Informationen und EPP-Transaction-ID; „Service im
  OData Browser öffnen" springt bei V2-Services direkt in den passenden Service), **EEE-Fehlerlog**
  und **Systemmeldungen**. Nur im Experten-Modus zusätzlich **RAP Contract Check Violations**. Jeder
  Reiter hat einen eigenen „laden"-Knopf und nutzt denselben Zeitraum/Benutzer wie die Dumps-Suche.
  Im Detail eines Eintrags zeigt die Kachel zeitlich nahe Dumps desselben Benutzers (±60 Sekunden)
  als Näherungs-Korrelation – ein Anhaltspunkt, welcher Dump zu welchem Fehler gehören könnte.
- **Ad-hoc-Beobachtung** – zweiter Einstieg oben („Ad-hoc-Beobachtung" statt „Post-Mortem-Analyse")
  für „es klemmt gerade": Benutzer (Pflichtfeld – ein enges Ziel statt eines Systemweit-Pollings),
  Quellen (Dumps/Gateway/EEE/Systemmeldungen) und Beobachtungsdauer (5/15/30 Minuten) wählen, dann
  „Beobachtung starten". Die Kachel merkt sich je Quelle nur einen Zeitstempel-Wasserstand („Stand
  jetzt", keine Vollkopie) und zeigt danach – auf Klick „Jetzt prüfen" oder optional automatisch
  alle 15 Sekunden – ausschließlich NEU hinzugekommene Einträge auf einer gemeinsamen Zeitachse,
  hart begrenzt auf die gewählte Dauer mit sichtbarem Countdown; „Sitzung beenden" geht jederzeit.
  Ein Klick auf einen neuen Eintrag öffnet dasselbe Detail wie in der Post-Mortem-Ansicht. Optional
  zusätzlich ein ABAP-Trace (SAT) für den beobachteten Benutzer anlegen (braucht „Schreibzugriffe
  erlaubt" am Endpunkt UND „Erweiterte Verwendung – ADT-Schreibzugriffe" in den Einstellungen).
  „Als Post-Mortem-Analyse übernehmen" spielt die gefundenen Dumps direkt in die normale Dashboard-/
  „Lauf aufheben"-Ansicht; ein eigener Markdown-Sitzungsbericht steht daneben bereit.
- **ABAP Cross Trace** – dritter Einstieg oben. Zeigt einen kompletten Request über ALLE
  RAP-Schichten (Gateway → SADL → Behavior → Draft → BAdIs). „Aktivierungen & Traces laden" zeigt
  vorhandene Aktivierungen/Traces; „Neue Aktivierung anlegen …" braucht „Schreibzugriffe erlaubt" +
  „Erweiterte Verwendung – ADT-Schreibzugriffe" (Trace-Level IMMER mit Klartext wählen – essential/
  extended/expert/verbose, eine falsche Stufe erfasst kommentarlos KEINE Records) und bietet eine
  nach Komponentenfamilie gruppierte Checkliste mit Presets („RAP komplett"/„Nur Gateway"/„Events/
  EEE"/„Alles"). Traces entstehen automatisch, sobald der gefilterte Benutzer eine passende Anfrage
  auslöst. Ein Trace-Klick zeigt Kopfdaten (inkl. EPP-Transaction-ID) und wechselt zwischen einer
  eingerückten **Hierarchie**-Ansicht (Komponenten farbcodiert, Dauer je Schritt) und einem echten
  **Mermaid-Sequenzdiagramm** – „Als Markdown öffnen" übergibt beides direkt an den Markdown-Editor.
  Lesen/Löschen von Aktivierungen und Traces bleibt frei, nur das Anlegen ist gegated. Records mit
  tatsächlich erfassbarem Rohinhalt (die meisten Records liefern keinen) bekommen in der Hierarchie
  einen kleinen „Inhalt"-Knopf – öffnet ein Detail mit dem (meist als JSON hübsch formatierten) Text
  und derselben Kopieren/Herunterladen/E-Mail/KI-Aktionsleiste wie überall.
- **„Mit KI bewerten"** (Häufungen-Tab) – schickt bis zu 40 Häufungen auf einmal an die eingestellte
  KI und trägt je Zeile eine Priorität (Kritisch/Hoch/Mittel/Niedrig, farbig) plus eine kurze
  Begründung ein. Nützlich, um bei vielen Häufungen schnell zu sehen, wo zuerst hingeschaut werden
  sollte – die KI kennt dabei nur Fehler-ID/Programm/Anzahl/Benutzerzahl/Kurztext, keine Geschäfts-
  daten. Kann je nach KI-Anbieter (vor allem lokale „nachdenkende" Modelle) mehrere Minuten dauern.
- **„Nach AIPC …"** – schreibt den aktuellen Analyse-Report (dieselben Inhalte wie „Markdown-Report")
  als ein Dokument (z. B. Typ FINDING) in ein AIPC-Projekt desselben Endpunkts – braucht dieselbe
  Freigabe wie das Anlegen einer Cross-Trace-Aktivierung.

## Tipps & Grenzen

- Zeitangaben laufen in der Systemzeit (UTC) des SAP-Systems – bei Zeitzonen-Differenz den
  Zeitraum großzügiger wählen.
- Die Kachel zeigt, was die jeweiligen ADT-Feeds liefern; Berechtigungen steuert das SAP-System.
- Der Gateway-Fehlerlog filtert Zeitraum/Benutzer clientseitig nach dem Laden (der Feed selbst
  liefert immer alle vorhandenen Einträge).
- ABAP Cross Trace zeigt in der Komponenten-Auswahl nur „einfache" Komponenten (z. B.
  „SAP.GW.SERVER") – die vom SAP-System zusätzlich angebotenen Sammel-Knoten (z. B. „alles unter
  SAP.BC") sind bewusst nicht wählbar, da unklar ist, ob sie automatisch alle Kinder mit-aktivieren.
