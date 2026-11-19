# Launchpad-Kataloge

Zeigt die Fiori-Kataloge deines SAP-Systems mit ihren Kacheln und Target Mappings. In Customizing-Katalogen
kannst du Einträge ändern, löschen und kopieren, ohne den Launchpad Designer zu öffnen.

## Voraussetzungen

- Ein SAP-Endpunkt (On-Premise). Die Anmeldung übernimmt der Endpunkt – auch SSO.
- Zum Ändern, Löschen und Kopieren: am Endpunkt „Schreibzugriffe erlaubt" und in den Einstellungen unter „Erweiterte
  Verwendung" die ADT-Schreibfreigabe. Ansehen geht ohne.
- In der Browser-Erweiterung sollte der Endpunkt `https://` nutzen – schreibende Aufrufe über `http://` sind
  dort unzuverlässig.

## Typischer Ablauf

1. **Kataloge laden** und über Name, Schicht oder „Nur bearbeitbare" eingrenzen.
2. **Katalog anklicken.** Die Reiter zeigen Kacheln, Target Mappings und sonstige Einträge.
3. **Eintrag anklicken**, um ihn anzusehen oder zu bearbeiten: Titel, Untertitel, Symbol, Suchbegriffe und
   Intent, beim Target Mapping zusätzlich UI5-Komponente und URL.
4. **Papierkorb in der Zeile**, um einen Eintrag zu löschen. Der Dialog sucht vorher nach Gruppen und Katalogen,
   die ihn verwenden.
5. **Zeilen markieren** und **In Katalog kopieren …**, um Einträge in einen anderen bearbeitbaren Katalog zu
   übernehmen, auch aus SAP-Standardkatalogen. Die Vorschau zeigt, was kopiert und was übersprungen wird.
6. **Katalog kopieren …** legt einen neuen Customizing-Katalog an, dessen Einträge alle Referenzen sind.
7. **Neue Kachel …** legt in einem bearbeitbaren Katalog eine Kachel, ein Target Mapping oder beides an.
8. **Intent prüfen …** (oder das Lupen-Symbol in der Zeile) sucht, warum eine Kachel keine App startet.

## Eine Kachel startet die App nicht

Typische Meldung im Launchpad: „App kann nicht geöffnet werden, weil die SAP-UI5-Komponente der Anwendung nicht
geladen werden konnte“. **Intent prüfen** sucht alle Kacheln und Target Mappings des Intents in allen Katalogen und
Gruppen, ähnlich wie die Transaktion /UI2/FLIA, aber ohne Rollenbezug. Für jedes Mapping prüft es:

- ob der App-Index die UI5-Komponente kennt,
- ob unter der URL eine App liegt und ob deren `sap.app.id` zur Komponente passt,
- ob es mehrere Mappings mit unterschiedlichem Ziel gibt.

Häufigster Fehler: Im Mapping steht der BSP-Name statt der `sap.app.id` aus der `manifest.json`, und die URL fehlt.
Dann sucht das Launchpad die Komponente an der falschen Stelle. Die Prüfung findet die richtige ID und bietet
**Korrektur übernehmen** an (nur in Customizing-Katalogen mit Schreibfreigabe). Außerdem öffnet sie die
`manifest.json` der App und den Intent im Launchpad.

## Neue Kachel anlegen

Semantisches Objekt und Aktion eingeben, dann wählen, ob Kachel, Target Mapping oder beides entstehen soll. Für das
Mapping trägst du den Namen der BSP-App ein und übernimmst mit dem Symbol daneben Komponente und URL direkt aus
ihrer `manifest.json`. **Prüfen** (läuft vor dem Anlegen automatisch) warnt bei falscher Komponente, fehlender App
oder wenn es für den Intent schon ein Mapping gibt. Bei Befunden musst du „Trotz der Befunde anlegen“ anhaken.

## Referenz oder eigenständige Kopie?

- Eine **Referenz** folgt der Quelle samt Übersetzungen. Du kannst sie im Ziel nicht ändern, und sie verliert ihren
  Inhalt, wenn die Quelle gelöscht wird.
- Eine **eigenständige Kopie** ist unabhängig und im Ziel änderbar. Übersetzungen entfallen, die Texte bleiben in der
  Originalsprache der Quelle.

## Übersetzungen prüfen

Der Reiter **Übersetzungen** zeigt die Texte eines Katalogs je Sprache. Trag Sprachen ein, zum Beispiel `DE, FR`, oder
lass das Feld leer für alle installierten Sprachen, und klick **Texte lesen**.

| Status | Bedeutung |
|---|---|
| übersetzt | Es gibt einen eigenen Text in dieser Sprache. |
| gleich wie Original | Der Text ist bewusst gleich, zum Beispiel ein Produktname. |
| fehlt | Für diese Sprache ist kein eigener Text gepflegt. |
| nicht geprüft | Das ließ sich nicht sicher feststellen. Schau dir den Text selbst an. |
| nicht übersetzbar | Der Text steht nur in der Kachelkonfiguration, die für alle Sprachen gleich ist. |

Mit **Nur offene Texte** bleibt die Arbeitsliste übrig. Markierte Zeilen füllt **Auswahl mit KI vorschlagen** mit
Vorschlägen, die du in der Tabelle noch ändern kannst. Exportiere die Liste über die Aktionsleiste; beim Neuladen sind
die Vorschläge weg. Eingepflegt werden müssen die Texte außerhalb von BDT, das Werkzeug schreibt keine Übersetzungen
ins System.

## Semantische Objekte suchen

**Semantische Objekte …** in der Katalogliste durchsucht alle Objekte des Systems nach Name, Text und Komponente, wahlweise nur SAP oder nur eigene. Beim gewählten Objekt zeigt **Verwendung suchen**, in welchen Katalogen es als Kachel oder Target Mapping steckt. Referenzen sowie Spaces und Pages findet die Suche nicht.

Dieselbe Suche öffnet das Symbol neben dem Feld **Semantisches Objekt**. **Übernehmen** trägt das Objekt ein, die Knöpfe nach „Mit Aktion übernehmen" zusätzlich die Aktion. Das gibt es auch im BSP-Studio, im UI-Launchpad und im UI-Mockup-Studio.

## Tipps & Grenzen

- Kacheln landen im Customizing-Auftrag aus deinem Benutzerparameter `/UI2/WD_TRKORR_CUST` (Transaktion SU3,
  Reiter „Parameter“). Der Auftrag muss offen sein und eine offene Aufgabe für deinen Benutzer haben, sonst
  meldet das System „Keine geeignete Aufgabe verfügbar …“. Abhilfe: Parameter pflegen oder in SE09/SE10 am
  Auftrag mit „Benutzer hinzufügen“ eine Aufgabe für dich anlegen. Das Werkzeug zeigt diesen Hinweis bei der
  Meldung mit an.
- Bearbeitet werden nur Customizing-Kataloge. Konfigurations- und SAP-Standardkataloge sind hier nur lesbar.
- Das Werkzeug schreibt immer in der **Originalsprache** des Katalogs. Prüfe nach einer Textänderung die Übersetzungen.
- Eine **Referenz** wird in ihrer Quelle gepflegt und lässt sich hier nur ansehen oder löschen.
- SAP verhindert das Löschen einer verwendeten Kachel nicht. Eine Kopie zeigt danach „Reference lost". Die Suche
  nach Verwendungen ist ein Hinweis, keine Garantie: Spaces und Pages sind nicht abgedeckt.
- Wurde ein Eintrag zwischenzeitlich anderswo geändert, bricht das Speichern mit einem Hinweis ab. Lade dann neu.
- ABAP Cloud (BTP) wird noch nicht unterstützt.
