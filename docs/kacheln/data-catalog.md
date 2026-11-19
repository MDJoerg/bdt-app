# Datenkatalog

Hier sammelst du die **alten SAP-Tabellen und -Felder** (z. B. MARA, MAKT, MVKE), die ein
Bericht, ein Mockup oder eine Ablösung auf CDS-Basis braucht – samt den Beziehungen zwischen
den Tabellen. Der Katalog ist die Grundlage, um später passende freigegebene CDS Views samt
Feld-Mapping zu finden (folgt als nächster Ausbauschritt).

## Voraussetzungen

- Ein Projekt (der Katalog liegt als Infoobjekt in der Wissensablage).
- Für Systemsuche und Feldlisten: ein SAP-Endpunkt mit ADT-Zugang (nur lesend, Freestyle-SQL
  der Data-Preview). Ohne Endpunkt kannst du Tabellen/Felder per Text einfügen.

## Aufbau

- **Startseite = Liste deiner Kataloge.** Filter oben: Suche über Name/Beschreibung/Objekte,
  „Enthält Objekt" (Tabelle oder CDS View), „Enthält Feld" (wahlweise nur unter den ausgewählten
  Feldern), „Geändert seit", „Nur Kataloge mit CDS Views", „Nur mit offenen Vorschlägen". Jede
  Zeile zeigt Kennzahlen (Tabellen, CDS Views, ausgewählte/alle Felder, Beziehungen, Vorschläge,
  Zuordnungen). „Neu" legt einen Katalog an, Zeile anklicken öffnet ihn; markierte Zeilen lassen
  sich öffnen, duplizieren oder löschen.
- **Ein Katalog** öffnet sich als eigene Seite mit Kopf (Name, Textsprache, Kennzahlen, Speichern)
  und den Reitern **Einträge & Felder**, **Modell**, **Umfeld**, **Beziehungen**, **CDS-Mapping** und **Export**.
  „←" führt zurück zur Liste. Der Link in der Adresszeile öffnet den Katalog samt Reiter direkt.

## Typischer Ablauf

1. „Tabelle suchen …": Namensmuster eingeben (z. B. `MAR*`), Treffer mit „Hinzufügen" in den
   Katalog holen. Feldliste, Bezeichnungen und Schlüssel werden aus dem System gelesen.
2. Oder „Feldliste einfügen …": Zeilen wie `MARA-MATNR` oder eine aus Excel/PDF kopierte
   Tabelle (Tabelle, Feld, …) einfügen – die Felder gelten dann als ausgewählt.
3. Je Tabelle die benötigten Felder ankreuzen („Auswahl") und Selektionsfelder markieren („Sel.").
4. Beziehungen: „Vorschläge" leitet sie aus Fremdschlüsseln, gleichnamigen Schlüsselfeldern und
   CDS-Assoziationen ab; „Neue Beziehung …" legt eine von Hand an. Eine Beziehung kann mehrere
   Feldpaare haben (z. B. Beleg + Position) und hat eine Art: Join (inner/left/right outer),
   Assoziation, Komposition, Eltern-Beziehung, Text- oder Wertehilfe-Assoziation – dazu
   Kardinalität und einen Alias (CDS-Name wie `_Kunde`). Vorschläge erscheinen blass als
   „Vorschlag", bis du sie bestätigst (einzeln oder „Alle Vorschläge bestätigen"). Die
   Herkunft steht jeweils in der Liste.
5. Reiter **Modell**: jede Tabelle bzw. CDS View ist eine
   Karte mit ihrer Feldliste, jede Beziehung eine Linie – durchgezogen für Joins, gestrichelt für
   Assoziationen, ◆ für Komposition/Eltern-Beziehung, blass für Vorschläge. Ziehe den Punkt rechts
   an einem Feld auf ein Feld einer anderen Karte, um eine Beziehung anzulegen (gibt es zwischen den
   beiden Karten schon eine, wird das Feldpaar dort ergänzt). Linie anklicken = bearbeiten oder
   bestätigen. „Felder" wählt Alle / Nur ausgewählte / Automatisch (zeigt die ausgewählten, sobald du
   aus einer Tabelle einzelne Felder gewählt hast); je Karte lässt sich das umschalten oder die Karte
   ausblenden. „Anordnen" ordnet die Karten entlang der Beziehungen; die Positionen speicherst du
   mit dem Katalog. Doppelklick auf eine Karte springt zu ihren Feldern (Reiter „Einträge & Felder").
   **CDS-Entwurf …** erzeugt ab einer Wurzel (die markierte Karte) einen View-Entwurf: Joins werden
   über weitere Karten verfolgt, Assoziationen, Text, Wertehilfe und Komposition entstehen eine Ebene
   tief, die Elemente sind deine ausgewählten Felder. Unbestätigte Vorschläge zählen nur mit Häkchen
   „Vorschläge einbeziehen"; nicht verbundene Karten stehen in den Hinweisen. Kopieren, herunterladen,
   mit einem leeren Prüf-DDLS auf Syntax prüfen lassen (nichts wird gespeichert) oder „An MDE Studio"
   für die Metadata Extension. Der Entwurf wird nie ins System geschrieben. Das Prüf-DDLS selbst
   gehört nicht in den Katalog – es ist nur der Platzhalter, gegen den geprüft wird. Unter
   „Annotationen" wählst du, was gleich mit erzeugt wird (Text-Assoziation, Wertehilfe,
   Fremdschlüssel, Erweiterbarkeit, Feldbezeichnungen, Berechtigungsprüfung). Die Warnung
   „Suchhilfezuordnung … nicht geerbt" ist ein reiner Hinweis und lässt sich nicht wegannotieren.
   Nach dem Syntax-Check bieten bekannte Fehler einen Korrektur-Knopf an (Karte oder Feld, das es im
   System nicht gibt, weglassen; fehlendes Währungs-/Einheitenfeld ergänzen). Ein Klick prüft gleich
   erneut; die Korrekturen gelten nur für den Entwurf und lassen sich zurücksetzen. „Als
   abapGit-ZIP" erzeugt ein Archiv, das du mit abapGit in ein Paket einspielst; prüfe vorher mit
   „Namen prüfen", ob der View-Name im System noch frei ist (abapGit überschreibt ohne Rückfrage).
6. „CDS-Kandidaten …" an einer Tabelle: sucht zu den gewählten Feldern CDS Views (direkte
   Basistabellen-Felder), zeigt Freigabestatus (C1-Vertrag), Abdeckung und das Feld-Mapping;
   „Übernehmen" legt die Zuordnung im Katalog ab. „Views darauf prüfen" findet Views auf Views
   und liest die Feldzuordnung aus dem CDS-Quelltext.
7. „Zwischenschicht …" (Karte CDS-Mapping): plant je Tabelle, ob eine freigegebene View genügt oder
   eine eigene Interface-View über mehrere Views nötig ist, zeigt das DDL-Gerüst und das
   Mapping-Dokument alt ↔ neu (Kopieren/Download).
8. Namen vergeben und speichern; als Markdown exportieren (Tabelle, Feld, Beschreibung, Sel.).



### Reiter „Umfeld" – wer nutzt diese Tabelle oder View?

Wähle oben einen Eintrag deines Katalogs als **Start** und klicke **Umfeld laden**. Der Graph zeigt, welche CDS Views
die Tabelle (oder View) lesen – direkt per FROM/JOIN oder über eine Assoziation –, bei einer CDS View zusätzlich ihre Quellen.
So prüfst du zum Beispiel, ob es zu einer nicht freigegebenen View (etwa `R_ApplicationLogHeader`) eine freigegebene
Alternative gibt, und findest sonst eine **Kopiervorlage** für eine eigene Z-View.

- **Farbe** = Freigabestatus (grün freigegeben, orange veraltet, rot nicht zur Freigabe vorgesehen, grau nicht freigegeben).
  Violetter Rahmen = eigenes Z/Y-Objekt, Tonne = Tabelle.
- **Beschriftung** „7/7 ✓": so viele deiner im Reiter „Einträge & Felder" gewählten Felder stecken in der View (auch über
  mehrere Views hinweg); „WHERE" heißt, dass die View filtert.
- **Klick** auf einen Knoten zeigt Freigabe, Paket, fehlende Felder, die WHERE-Klausel und den Quelltext (WHERE-Zeilen
  hervorgehoben, Kopieren möglich). **Doppelklick** (oder „Verbraucher laden") klappt die nächste Ebene auf.
- Die Zeile über dem Graph fasst zusammen, ob freigegebene Alternativen gefunden wurden; die Chips darunter nennen die
  besten Kopiervorlagen. „Im Graph-Viewer" öffnet einen Schnappschuss.

Je „Verbraucher laden" werden höchstens 40 Quelltexte geprüft (Rest über „Weitere prüfen"). Alle Abfragen sind lesend und
laufen nur auf deinen Klick.

## Testdaten

Unter der Feldliste jedes Eintrags gibt es den Abschnitt **Testdaten**:

- **Aus System laden** liest über Data Preview bis zu 200 Zeilen aus dem gewählten SAP-System,
  auf Wunsch nur die gewählten Felder. Das klappt für Tabellen und CDS Views.
- **Einfügen …** übernimmt einen Excel- oder CSV-Bereich. Die erste Zeile enthält die Spaltennamen
  (Feldname, Element oder Beschreibung); Spalten ohne passendes Feld werden genannt und weggelassen.
- Werte lassen sich direkt in der Tabelle ändern, Zeilen hinzufügen und entfernen.
- Testdaten werden mit dem Katalog gespeichert und gehen mit Export, Import, Sicherung und Sync mit.
  Daten aus einem echten System können personenbezogen sein – dann den Katalog vertraulich
  kennzeichnen oder nur Beispielwerte verwenden.
- **In ABAP Sandbox öffnen** nimmt sie als Startdaten mit, das UI-Mockup-Studio übernimmt sie beim
  Übernehmen von Feldern als Beispieldaten.

## Views für mehrere Einträge

Im Dialog „CDS-Entwurf“ öffnet **Views für mehrere Einträge …** eine Auswahl aller Einträge
(vorausgewählt: alle Tabellen). Je gewähltem Eintrag entsteht ein View mit denselben Einstellungen wie
der Einzel-Entwurf (VDM-Ebene, Präfix, Annotationen, Vorschläge). Assoziationen zwischen gewählten
Einträgen zeigen auf die mitgenerierten Views statt auf die Tabellen – z. B. `ZI_Order` →
`association to ZI_Site`. Die Vorschau zeigt je View Elemente, Assoziationen, Hinweise und den
Quelltext. **Im System anlegen …** übergibt alle Views als **einen** Plan an den ABAP Generator (gemeinsam
angelegt und aktiviert, gemeinsam zurücknehmbar), **Als abapGit-ZIP** lädt dieselben Views als Archiv.

## Kanal für externe KI

Über das Stecker-Symbol (in der Liste und auf der Objektseite) schaltest du den Kanal `/mcp/dc` des
BDT-MCP-Gateways ein. Eine KI wie Claude Code oder goose kann dann die Kataloge des Projekts lesen,
Felder und Beziehungen ansehen, Vorschläge berechnen und einen CDS-Entwurf oder das Objektpaket einer
Hierarchie als Text erzeugen. Mit dem Häkchen „KI darf den Datenkatalog ändern" (Einstellungen → MCP →
Freigaben) schlägt sie zusätzlich Änderungen vor: Kataloge anlegen, Einträge und Felder ergänzen, Felder
auswählen, Beziehungen anlegen, ändern oder bestätigen, Hierarchien anlegen. Geschrieben wird erst nach
deiner Bestätigung im Tab. Einen offenen Katalog mit ungespeicherten Änderungen fasst die KI nicht an;
nach dem Schreiben lädt die Seite neu. Über diesen Kanal wird nichts gelöscht und nichts ins SAP-System
geschrieben – Feldlisten aus dem System lädst du selbst, das Anlegen im System läuft weiter über
„Im System anlegen …".

## Tipps & Grenzen

- Kandidaten sind standardmäßig auf **freigegebene** CDS Views beschränkt; die Häkchen im
  Dialog blenden nicht freigegebene und klassische DDIC-Views ein. Der Freigabestatus kommt live
  aus dem System (`ARS_W_API_STATE`) und ist release-abhängig.
- Das Mapping ist Best Effort: durchgereicht werden Felder, Aliasse und einfache Casts;
  Ausdrücke und Assoziationspfade erscheinen nicht.

- Im Modell werden höchstens 60 Felder je Karte gezeigt (Felder mit Beziehung immer); ab 40 Karten
  wird die Fläche träge – Karten ausblenden oder „Nur ausgewählte" nutzen.
- Bezeichnungen kommen in der gewählten Textsprache (E/D).
- Beziehungsvorschläge aus Fremdschlüsseln sind Best Effort (das Zielfeld wird über den
  Feldnamen erraten) – bitte prüfen.
- Die Anwendungstabellen einer Testinstallation (z. B. ohne Materialstamm) können fehlen; dann
  Feldlisten-Text nutzen.
