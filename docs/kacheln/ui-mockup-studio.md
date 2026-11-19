# UI-Mockup-Studio

Hier entwirfst du gemeinsam mit deinen Anwendern **Fiori-Oberflächen-Mockups** – statt
PowerPoint-Folien mit nachgebauten Screens oder Excel-Feldlisten baust du eine Seite aus
echten Bereichen und Elementen (Filterleiste, Tabelle, Feldgruppen, Aktionen …) zusammen.
Dahinter steht ein strukturiertes Modell (Seiten, Entitäten, Felder, Aktionen), kein freies
Zeichnen – dadurch bleibt jedes Mockup automatisch „Fiori-konform" und lässt sich sofort als
Skizze **oder** als Hi-Fi-Vorschau (echte UI5 Web Components) ansehen.

## Voraussetzungen

- Ein Projekt.
- Kein SAP-Endpunkt nötig.
- Läuft uneingeschränkt in allen Targets (Erweiterung, Desktop-App, Web-App).

## Typischer Ablauf

1. „Neue Entität" anlegen und Felder eintragen (Name, Bezeichnung, Typ, optional als
   Schlüsselfeld markieren) – oder direkt „Beispiel laden" für eine fertige Demo-Szene
   („Kundenaufträge").
2. „Neue Seite" anlegen: Titel/Untertitel vergeben, einen Floorplan wählen (List Report,
   Worklist oder Object Page) und die Entität zuordnen, deren Daten die Seite zeigt.
3. Bei Bedarf zuerst unter „Aktionen" festlegen, was beim Klick passiert (zu einer anderen
   Seite navigieren, einen Dialog/eine Meldung anzeigen oder nichts tun).
4. In den „Bereichen" der Seite (z. B. „Filterleiste"/„Tabelle" beim List Report,
   „Abschnitte" bei der Object Page) über „Element hinzufügen" Felder, Feldgruppen, Tabellen,
   Kennzahlen, Aktionen oder Meldungen einfügen – Reihenfolge per Pfeil-Symbolen ändern.
5. Unten in der Vorschau zwischen „Skizze" und „Hi-Fi" umschalten.
6. Namen vergeben und speichern.

## Funktionen im Detail

- **Spezifikation im Simulator**: „Aufzeichnen" merkt sich Filter, geöffnete Zeilen und
  Aktionen; „Beenden und übernehmen" macht daraus einen Szenario-Entwurf (Angenommen/Wenn/Dann)
  für eine gebundene oder neue Spezifikation im Spezifikation-Studio. Das Buch-Symbol blendet
  die gebundene Spezifikation ein (Regeln, offene Fragen) – Beispiele und Fragen lassen sich
  dort direkt ergänzen. Spielt das Spezifikation-Studio ein Szenario ab, zeigt der Simulator
  es Schritt für Schritt mit grün/rot. Der Perspektiven-Reiter weist auf gebundene
  Spezifikationen hin.

- **Struktur links**: „Übersicht" (Startseite wählen, kurze Notizen zu Voraussetzungen/
  Ablauf/Erwartungshaltung/Ausblick), „Entitäten" und „Seiten" – ein Klick öffnet die
  jeweilige Bearbeitungsansicht.
- **Entitäten**: technischer Name, Bezeichnung, Typ (Text/Zahl/Datum/Status/Link) und ob ein
  Feld als Schlüssel gilt. Ein einmal angelegter technischer Name lässt sich nicht mehr
  umbenennen – bei Bedarf das Feld löschen und neu anlegen.
- **Seiten**: Floorplan List Report (Filterleiste + Tabelle + Tabellen-Aktionen), Worklist
  (Tab-Leiste für Sichten statt Filterleiste) oder Object Page (Kopf-Kennzahlen/-Aktionen +
  beliebig viele Abschnitte mit Feldgruppen oder Tabellen).
- **Startseite**: über den Stern-Knopf in der Seiten-Ansicht oder die Auswahl in der
  Übersicht festlegen.
- **Aktionen**: „Navigieren" (springt beim Abspielen zu einer anderen Seite), „Dialog
  anzeigen", „Meldung anzeigen" (mit Text und Art Erfolg/Warnung/Fehler/Information) oder
  „Nichts tun". Erst eine angelegte Aktion lässt sich in einem Bereich als Element
  referenzieren.
- **Element hinzufügen**: die verfügbaren Arten richten sich nach dem jeweiligen Bereich
  (z. B. nur „Feld" in der Filterleiste, nur „Feldgruppe"/„Tabelle" in den Abschnitten einer
  Object Page). Eine Tabelle in den Abschnitten einer Object Page kann bewusst eine ANDERE
  Entität zeigen als die Seite selbst (z. B. Positionen zu einem Auftrag).
- **Löschen mit Aufräumen**: wird ein Feld, eine Entität, eine Seite oder eine Aktion
  gelöscht, entfernt das Studio automatisch alle Verweise darauf (z. B. verschwindet ein
  gelöschtes Feld auch aus jeder Feldgruppe/Tabelle, eine gelöschte Seite lässt jede
  „Navigieren"-Aktion darauf auf „Nichts tun" zurückfallen) – nie eine unsichtbar kaputte
  Referenz.
- **Validierung**: eine Meldungszeile über der Struktur zeigt Fehler (z. B. eine unbekannte
  Startseite) und Warnungen, sobald das Modell welche enthält.
- **Skizze/Hi-Fi**: dieselbe Seite lässt sich jederzeit zwischen einer handgezeichneten
  Skizze und einer Hi-Fi-Vorschau aus echten UI5 Web Components umschalten – kein
  Datenverlust beim Wechseln.
- **Beispiel laden**: überschreibt Entitäten/Seiten des aktuellen Mockups mit der fertigen
  Demo-Szene „Kundenaufträge" (Fragt vorher nach Bestätigung).

## KI-Assistent (Chat)

Der Floorplan **KI-Assistent (Chat)** beschreibt einen Assistenten, der ohne eigene Oberfläche
arbeitet – zum Beispiel per Sprache im Auto.

- **Rolle und Grenzen**: wer der Assistent ist und was er nicht tun soll.
- **Werkzeuge**: aus einem MCP Simulator übernehmen; angezeigt wird, ob ein Werkzeug nur liest
  oder Daten ändert.
- **Beispieldialoge**: je Situation (Arbeit – Sprache, Pause – Smartphone, Zentrale – Desktop)
  eine Folge aus Nutzer, Werkzeugaufruf und Antwort. Jede Antwort hat eine Form: Kurzantwort,
  Rückfrage, Bestätigung, Karte, Liste, Tabelle oder Fehler.
- **Prüfung**: meldet Formen, die nicht zur Situation passen (z. B. Tabelle per Sprache), zu lange
  Sprachantworten und ändernde Werkzeuge ohne vorherige Bestätigung.
- **Simulator**: spielt einen Dialog Schritt für Schritt ab; Sprachantworten liest auf Wunsch eine
  lokale Stimme vor.
- **Als Agent speichern**: legt einen Agenten mit passendem Systemprompt an, der den Simulator als
  Werkzeugquelle nutzt. „Im KI-Chat testen" öffnet ihn direkt.

## Tipps & Grenzen

- Bearbeitet wird über Formular + Live-Vorschau, nicht über freies Zeichnen – dadurch lässt
  sich im Workshop keine Oberfläche entwerfen, die es in Fiori Elements so nicht gibt.
- Die Hi-Fi-Vorschau ist Fiori-nah, aber nicht pixelgleich mit einer echten Fiori-Elements-
  App (UI5 Web Components sind keine Fiori-Elements-Floorplans).
- Perspektiven-Reiter mit Kommentaren je Element, der Simulator (Klicken durch die Seiten),
  Excel-Mockup-Import, der Entwicklungs-Export (DDLX-Entwurf) sowie echte Daten aus einem
  SAP-System sind spätere Ausbaustufen – die Übersicht bietet dafür schon eine Kurzform der
  Perspektiven als Textfelder.

- **Datenkatalog als Feldquelle:** „Aus Datenkatalog …" an einer Entität übernimmt Felder einer Katalogtabelle; „Anforderung" erzeugt ein Anforderungsdokument (Ebenen, Feldlisten, Selektion, offene Punkte); im Entwicklungs-Export leitet „Basis-Views aus Datenkatalog ableiten" die Basis-Views ab.
