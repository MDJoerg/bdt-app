# Spezifikation-Studio

Hier klärst du gemeinsam mit deinen Anwendern eine **Anforderung** – nicht als lange Prosa,
sondern über **Regeln, konkrete Beispiele und offene Fragen**. Alles steht in einem einzigen,
lesbaren Text: Ziel, Begriffe, nummerierte Regeln (R1, R2 …), Szenarien („Angenommen … Wenn
… Dann …"), Fragen und nicht-funktionale Anforderungen. Das Studio prüft den Text laufend auf
Widersprüche und Lücken.

## Voraussetzungen

- Ein Projekt.
- Kein SAP-Endpunkt nötig.
- Läuft uneingeschränkt in allen Targets (Erweiterung, Desktop-App, Web-App).

## Typischer Ablauf

1. „Neue Spezifikation" wählen – es öffnet sich das **Example-Mapping-Board**. Oben kannst
   du ein **Projekt** eintragen (freier Text); in der Liste gibt es dafür eine eigene Spalte
   und einen Filter. Ist in der Liste ein Projekt-Filter gesetzt, übernimmt die neue
   Spezifikation es direkt.
   *Mit KI schneller:* Titel/Ziel und Projekt eintragen, „KI-Prompt kopieren", den Prompt in
   einer KI deiner Wahl ausführen und die Antwort im Reiter „Text" einfügen (vorhandenen Text
   ersetzen). Danach weiter im Board prüfen und ergänzen.
2. Auf die gelbe Story-Karte klicken: Titel und Ziel (wer will was erreichen?) eintragen.
3. Mit „+ Regel" jede Geschäftsregel als blaue Karte anlegen.
4. Unter jeder Regel mit „+ Beispiel" konkrete Beispiele als einen Satz notieren, z. B.
   „Antrag ohne Zeitraum, senden → Meldung". Das geht im Gespräch schnell.
5. Was keiner beantworten kann, mit „+ Frage" als rote Karte festhalten (Regelbezug in
   Klammern, z. B. „(R2)"). Geklärte Fragen mit dem Häkchen samt Antwort abschließen.
6. Danach die Beispiele mit dem Stift-Symbol „Als Szenario ausformulieren": Angenommen /
   Wenn / Dann ausfüllen – der Vorschlag kommt aus dem Satz.
7. In der „Übersicht" prüfen, was die Prüfung meldet; Namen vergeben und speichern.

## Funktionen im Detail

- **Example Mapping**: Story-Karte (gelb), je Regel eine Spalte (blau) mit ihren Beispielen
  (grün – durchgezogen = ausformuliertes Szenario, gestrichelt = Beispielskizze als Satz),
  Fragen rechts (rot, geklärte grau). Die Reife-Einschätzung oben rechts liest das Board:
  viele offene Fragen = noch nicht reif, Regel ohne Beispiel = zu abstrakt, Regel mit sehr
  vielen Beispielen = besser aufteilen. Jede Änderung am Board landet sofort im Text.
- **Mockup**: ein UI-Mockup aus dem Projekt binden. Szenarien mit `@ui` oder `@mockup:<Seite>`
  laufen dann gegen das Mockup – je Schritt grün (stimmt), rot (mit Begründung) oder grau (Satz
  gehört nicht zum gebundenen Vokabular, bitte selbst prüfen). „Im Simulator ansehen" spielt
  ein Szenario Schritt für Schritt im UI-Mockup-Studio ab. Grün heißt: das Mockup passt zur
  Erwartung – nicht, dass die Erwartung richtig ist. Die erkannten Satzmuster stehen im Tab.
- **MCP**: einen MCP Simulator aus dem Projekt binden. Szenarien mit `@mcp` rufen Tools,
  Ressourcen und Prompts auf („Wenn ich das Tool "list_customers" mit country "DE" aufrufe",
  „Dann enthält die Antwort 2 Einträge") – „Abspielen" gegen den Simulator oder, als Abnahmetest,
  gegen einen echten Server aus den MCP-Inspector-Profilen. Dort laufen Tools, die der Server nicht
  als nur lesend kennzeichnet, erst nach Rückfrage. „Szenarien aus Beispielen" übernimmt die im
  Simulator aufgezeichneten Beispiele. Die erkannten Satzmuster stehen im Tab.
- **Quellen**: woher die Anforderung kommt. Eine **Story** binden: „Personas als Akteure
  übernehmen", „Design-Thinking-Objekte übernehmen" (Ideen/Prototypen werden Regeln, Tests und
  Feedback Beispiele, Annahmen Fragen – ein zweiter Klick verdoppelt nichts) und je Szene ein
  „Szenario-Entwurf". Einen **Datenkatalog** binden: Felder ankreuzen und als Begriffe
  übernehmen; im Ausformulieren-Formular gibt es dann eine Feldauswahl. Eine **Aufzeichnung aus
  dem Prozess-Studio** binden: Marken ankreuzen, „Soll-Szenario aus Marken" – das erwartete
  Ergebnis trägst du selbst ein. Verweise ins Leere meldet die Prüfung.
- **Übergabe**: was die Entwicklung bekommt. Markiere Szenarien mit `@validation`,
  `@determination` oder `@action` (optional mit Namen, z. B. `@action:approveOrder`) – daraus
  entstehen BDEF-Fragmente samt Meldungstexten. Jedes Szenario wird eine Methode im
  ABAP-Unit-Testgerüst. „Kontext-Paket herunterladen" bündelt alles mit einem Prompt für die KI
  der Entwickler. „Ins AIPC ablegen" speichert die Spezifikation als Leitfaden (GUIDE) und auf
  Wunsch offene Fragen als ISSUE. Alles sind Vorlagen – in SAP wird nichts geschrieben.
- **Fragen ins Kanban**: das Symbol in der Fragen-Spalte legt jede nummerierte Frage als Karte
  in der Wissensablage an, einsortiert in die Taxonomie „Klärungsbedarf" (Offen / In Klärung
  / Geklärt) – im Kanban diese Taxonomie als Spalten wählen. Bereits übernommene Fragen
  werden erkannt. Die Spezifikation muss dafür gespeichert sein.

- **Übersicht**: Kennzahlen (Regeln, Szenarien, Beispielzeilen, offene Fragen, Fehler,
  Hinweise), das Ziel, jede Regel mit der Zahl ihrer Szenarien („kein Beispiel" ist markiert),
  die Fragen (offene zuerst) und das Prüfergebnis. Ein Klick auf einen Eintrag springt im Text
  an die Stelle.
- **Text**: der eigentliche Inhalt. Fehler und Hinweise stehen unter dem Editor, ein Klick
  springt in die Zeile. „Umformatieren" bringt den Text in die einheitliche Form (feste
  Abschnittsreihenfolge, deutsche Schlüsselwörter, ausgerichtete Tabellen).
- **Szenarien**: Lesesicht auf alle Beispiele, gruppiert nach Regel, mit Tags und
  Beispieltabellen.
- **Prüfungen**: Widerspruch (gleiche Ausgangslage und Handlung, aber anderes Ergebnis),
  doppelte Szenarien, Regel ohne Beispiel, Szenario ohne Regel, Frage zu einer unbekannten
  Regel, fett markierter Begriff ohne Eintrag unter „## Begriffe", Oberflächenbegriffe
  („Button", „Seite" …) in einem fachlichen Szenario ohne `@ui`, Akteur ohne Persona im
  Projekt, zu viele Szenarien je Regel. Keine Prüfung blockiert das Speichern.
- **.feature exportieren**: jede Funktionalität als eigene Datei für Cucumber & Co. (mehrere
  Dateien als ZIP). Nur ohne Fehler möglich.
- **Bausteine**: Beispiel-Spezifikation und Regel-Muster; eigene Bausteine über „Als
  Baustein ablegen …".
- **KI**: „KI-Prompt kopieren" (im Board und im Reiter „Text") liefert eine Anleitung für eine
  externe KI – mit Titel, Projekt und bereits notiertem Ziel als Ausgangspunkt. „Als Kontext
  an KI-Chat" gibt den Text an den eingebauten KI-Chat.

## Tipps & Grenzen

- Schreib Beispiele fachlich („Angenommen ein Auftrag ohne Position, Wenn er gesichert wird,
  Dann …"), nicht als Klickanleitung. Oberflächenbezogene Szenarien markierst du mit `@ui`.
- Mehrere Werte für dieselbe Regel gehören in einen „Szenariogrundriss" mit Beispieltabelle.
- Nicht-funktionale Anforderungen (Antwortzeit, Mandantenfähigkeit …) bewusst als Liste, nicht
  als Szenario.
- Doc-Strings in Szenarien mit `"""` schreiben (drei Backticks beenden den Codeblock).
- Änderungen am Board schreiben den Text in die einheitliche Form – eigene Formatierung im Text
  geht dabei verloren, der Inhalt bleibt.
- Am einfachsten entstehen Oberflächen-Szenarien im UI-Mockup-Studio: im Simulator
  „Aufzeichnen", klicken, Erwartung eintragen, „Im Spezifikation-Studio übernehmen".
- Aus einer Story im Story-Studio geht es noch schneller: Reiter „Design-Thinking-Brücke" →
  „Als Spezifikation anlegen".
- **KI-Hilfen** (Knopf im Example-Mapping-Board): fehlende Beispiele vorschlagen, Widersprüche
  und Lücken als Fragen finden, Regeln aus dem Ziel ableiten oder eine Beispielskizze als Szenario
  ausformulieren lassen. Die Vorschläge erscheinen als Liste zum Anhaken – nur Angehaktes wird
  übernommen. Ohne eingerichtete KI: „Manuell über eine externe KI" – Prompt kopieren, die
  Antwort einfügen, „Antwort auswerten". Welche KI genutzt wird, legst du in den Einstellungen
  unter „KI Funktionen" fest.
- **Kanal für externe KI** (Stecker-Symbol): Über das BDT-MCP-Gateway (`/mcp/spec`) liest eine KI
  wie Claude Code oder goose die Spezifikationen des Projekts, sieht das Board und die Prüfung und
  schlägt Änderungen vor (Regeln, Skizzen, Szenarien, Antworten auf Fragen, Begriffe). Geschrieben
  wird erst nach deiner Bestätigung im Tab und nur mit dem Häkchen „KI darf Spezifikationen anlegen
  und ändern" (Einstellungen → Erweiterte Verwendung). Eine geöffnete Spezifikation mit
  ungespeicherten Änderungen fasst die KI nicht an; nach dem Schreiben lädt die Seite neu.
- Noch nicht enthalten: die Rückmeldung echter ABAP-Unit-Ergebnisse – folgt in einer späteren
  Ausbaustufe.
