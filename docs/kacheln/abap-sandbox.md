# ABAP Sandbox

Schreibe ABAP und führe es direkt im Browser aus, ganz ohne SAP-System. Reports, Klassen, ABAP Unit und einfache Datenbankzugriffe laufen lokal. Das passt für Schulungen, Katas und eigenen Code, der ohne SAP-Standard auskommt.

## Voraussetzungen

- Ein Projekt zum Speichern. Ein SAP-Endpunkt ist nicht nötig.

## Ablauf

1. Beim Öffnen liegt ein Beispiel bereit. Weitere Vorlagen findest du über das Plus neben **Projekte**.
2. Wähle links eine Datei und bearbeite sie. Über das Plus neben **Dateien** kommen Reports, Klassen, Testklassen, Interfaces und Tabellen dazu.
3. **Prüfen** zeigt Syntaxfehler mit Datei und Zeile. Ein Klick springt an die Stelle.
4. Wähle oben, was laufen soll, und klicke auf **Ausführen**:
   - ein Report
   - eine Klasse mit `if_oo_adt_classrun`, gestartet über `main`
   - alle ABAP-Unit-Tests
5. **Speichern** legt das Projekt in der Wissensablage ab. Das Symbol mit dem Pfeil nach unten lädt es als abapGit-ZIP herunter.

## Funktionen im Detail

- **Formatieren:** Der Knopf über dem Editor (oder Umschalt+Alt+F) richtet die geöffnete ABAP-Datei aus: Groß-/Kleinschreibung und Einzug. Strg+Z macht es rückgängig. Texte und Kommentare bleiben unverändert.
- **Einfärbung und Formatierung einstellen:** Das Paletten-Symbol neben **Formatieren** öffnet die Einstellungen: Farbschema, eigene Farben je Kategorie, fett, Einfärbung aus; Schlüsselwörter und Bezeichner groß, klein oder unverändert, Einzug und TRY/CATCH. Die Einstellungen gelten auch im abapGit Studio und im ABAP Unit Cockpit.
- **Reiter Daten:** Wähle eine Tabelle und wechsle zwischen drei Ansichten:
  - **Felder:** Felder anlegen und entfernen.
  - **Startdaten:** Zeilen, die vor jedem Lauf in der Tabelle stehen. Klicke zum Ändern in eine Zelle oder füge Zeilen aus Excel ein.
  - **Nach dem Lauf:** der Inhalt nach dem letzten Lauf. Ein Lauf ändert die Startdaten nicht.
- **Projekte übernehmen:** Das Plus neben **Projekte** importiert auch ein abapGit-ZIP. **In ABAP Sandbox öffnen** gibt es außerdem im abapGit Studio, im Spezifikation-Studio (Testgerüst, alle Tests zunächst rot) und im Datenkatalog (Tabellen samt Feldern, ohne Daten).
- **Reiter ABAP Unit:**
  - **Lauf aufheben** legt den Lauf in der Wissensablage ab, das Projekt muss dafür gespeichert sein. **Im Cockpit öffnen** zeigt ihn im ABAP Unit Cockpit, samt Verlauf.
  - Das KI-Symbol in einer Zeile erklärt den Fehlschlag im KI-Chat.
  - **Testklasse vorschlagen** fragt die KI nach Tests für die geöffnete Klasse.
  - **Als Kanban-Karten** legt fehlgeschlagene Tests als Karten an. Im Kanban wählst du dafür die Taxonomie „ABAP-Unit-Backlog".

## Tipps & Grenzen

- **Abgeschottet:** Der Code läuft ohne Netz und ohne Zugriff auf deine Daten, auch wenn er aus einer fremden Quelle stammt.
- **Zeitbudget:** Ein Lauf endet spätestens nach der oben gewählten Zeit. **Abbrechen** beendet ihn sofort, auch bei einer Endlosschleife.
- **Kein SAP-Standard:** Mitgeliefert sind nur die Ausnahmeklassen, `cl_abap_unit_assert` und `if_oo_adt_classrun`. Anderer Standard fehlt, dafür meldet **Prüfen** einen Fehler. Es gibt auch kein `MANDT` und keine Berechtigungsprüfung.
- **Formatierung:** Lange Anweisungen werden nicht umgebrochen, der Einzug ist fest zwei Leerzeichen. Die Einfärbung ist eine Annäherung: Ein Feld, das wie ein Schlüsselwort heißt, wird mitgefärbt.
- **Feste Systemwerte:** `sy-sysid` ist `ABC`, `sy-mandt` ist `123`.
- **`WRITE`:** Die Ausgabe hat keine Abstände zwischen den Werten und ist kein Abbild einer SAP-Liste.
- **Moderne Syntax:** Sie wird vor dem Lauf automatisch umgewandelt. Nicht alles lässt sich umwandeln, dann erscheint ein Fehler.
- **Laufzeitfehler:** Sie nennen die Ausnahme, aber noch keine ABAP-Zeile.
- **CDS und RAP:** Beides läuft hier nicht. Solche Dateien stehen in der Liste mit „Läuft hier nicht" und bleiben beim Export erhalten.
- **abapGit-ZIP:** Das Einspielen in ein echtes SAP-System ist noch nicht geprüft.
