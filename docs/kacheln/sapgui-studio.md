# SAPGUI-Studio

Du hast einen **klassischen ABAP-Report** mit Selektionsbild, `SELECT` und ALV-Ausgabe und
möchtest daraus eine Fiori-App auf Basis von CDS/RAP/Fiori Elements machen? Das SAPGUI-Studio
liest den Report ein und zeigt dir, was sich direkt übertragen lässt und was nicht.

Die Kachel **analysiert** den Report und **erzeugt** daraus ein lesendes List-Report-Gerüst
(CDS-Views, UI-Annotationen, Service) als einspielbares abapGit-Archiv.

## Voraussetzungen

- **Quelltext einfügen** und **abapGit-ZIP**: nichts weiter, die Analyse läuft komplett lokal.
- **Aus SAP-System**: ein SAP-Endpunkt mit ADT-Zugang (nur lesend).

## Typischer Ablauf

1. Eingang wählen:
   - **Quelltext einfügen**: Hauptprogramm einfügen, bei Bedarf über „Include hinzufügen"
     weitere Includes ergänzen. Optional die Textelemente als `Name=Text`-Zeilen einfügen
     (z. B. `S_VBELN=Verkaufsbeleg`, `001=Belegauswahl`).
   - **Aus SAP-System**: Programmnamen eingeben oder über „Suchen …" finden. Das Studio lädt
     Programm, alle Includes und die Selektionstexte/Textsymbole.
   - **abapGit-ZIP**: Archiv wählen, in der Liste das Programm anklicken. Includes und
     Textelemente kommen aus demselben Archiv.
2. **Analysieren** klicken.
3. Ergebnis in den Reitern prüfen:
   - **Selektionsbild**: links so, wie es im SAP GUI aussieht (Blöcke mit Titeln, Von/Bis-
     Felder, Checkboxen, Radiobuttons), rechts je Feld die geplante Umsetzung in der
     Fiori-Filterleiste. Ein Klick auf eine Zeile markiert das Feld im GUI-Bild.
   - **Datenquelle & Spalten**: erkannte `SELECT`-Anweisungen, vorgeschlagene Primärtabelle,
     Ausgabespalten aus dem ALV-Feldkatalog (sonst aus der `SELECT`-Liste), Navigation
     (`CALL TRANSACTION`, `SET PARAMETER`, `SUBMIT`).
   - **Hinweise**: alles, was nicht direkt in einen List Report passt, mit Fundstelle.
   - **Quelltexte**: die eingelesenen Dateien. Ein Klick auf eine Fundstelle springt dorthin.
4. Über die Aktionsleiste die Analyse als Markdown kopieren, herunterladen oder an den KI-Chat
   geben.

## Gerüst erzeugen (Reiter „Generierung")

1. **Namensprofil** wählen: „SAP-Generator / RAP" (`ZR_…`/`ZC_…`) oder „VDM klassisch"
   (`ZI_…`/`ZC_…`), dazu Präfix bzw. Namensraum, ein optionales Kürzel und den Objektnamen.
   Die Tabelle darunter zeigt alle entstehenden Namen samt Länge. Über „Als Profil speichern" merkst
   du dir Präfix/Kürzel/Profil im Projekt.
2. **Datenmodell**: „CDS-View auf Tabelle" ist der Normalfall. Findet das Studio keinen einfachen
   `SELECT` auf eine einzelne Tabelle (die Daten kommen z. B. aus einem Funktionsbaustein, oder der
   `SELECT` verknüpft mehrere Tabellen), schlägt es **„Custom Entity + Query-Klasse"** vor und sagt dir,
   warum. Dann entsteht statt der CDS-Views eine Custom Entity mit einer ABAP-Klasse, in der Filter,
   Sortierung und Blättern schon fertig sind. Die eigentliche Datenbeschaffung überträgst du selbst aus
   dem alten Report — die Klasse zeigt dir die passenden Stellen. In der zusätzlichen Spalte **Typ**
   steht je Feld der Datentyp (leer = aus dem DDIC). Du kannst jederzeit umschalten, deine Eingaben
   bleiben erhalten.
3. Optional **„Felder aus DDIC laden"** (braucht einen SAP-Endpunkt, liest nur): holt die
   Feldliste der Tabelle mit Schlüsseln und Bezeichnern. Ohne diesen Schritt musst du die
   Schlüsselfelder selbst markieren.
4. **Felder** prüfen: übernehmen, Alias, Label (leer = Text aus dem DDIC), Schlüssel, Spalte
   (Position, Wichtigkeit) und Filter (Filterart, Pflicht, Vorbelegung).
5. **Nicht direkt abbildbare Selektionsfelder**: eine Checkbox ohne Feldbezug kannst du einem
   Feld zuordnen; Radiobutton-Gruppen werden als Filter mit festen Werten angelegt (die fachliche
   Bedeutung je Option trägst du später nach).
6. Optional **Wertehilfen**: in der Spalte „Wertehilfe" einen CDS-View als `View.Element` eintragen oder
   „Wertehilfen vorschlagen" klicken (braucht einen SAP-Endpunkt). Vorschläge kommen aus den Prüftabellen
   der Felder; „freigegeben" heißt: der View ist von SAP freigegeben, „prüfen": bitte selbst bewerten.
7. Unter **Prüfung** müssen alle Fehler behoben sein, dann **„Als abapGit-ZIP exportieren"**.
8. Optional **Gegen das System prüfen** (liest nur, speichert nichts):
   - „Zielnamen prüfen" zeigt, ob ein Name im System schon vergeben ist.
   - „Syntax prüfen" testet den Basis-View bzw. die Custom Entity gegen einen leeren Prüf-View (Standard
     `ZBDT_SGS_CHECK`). Den legst du einmal selbst an, z. B. in `$TMP`; er darf nicht verwendet werden.
     Dass die Query-Klasse noch fehlt, ist dabei normal — sie entsteht erst beim Einspielen.
9. **Weitergeben**: die Metadata Extension im MDE Studio bearbeiten, die Oberfläche als UI-Mockup für einen
   Workshop mit Anwendern öffnen oder das Archiv im abapGit Studio weiterbearbeiten (umbenennen, übersetzen).
10. **Veredelung mit KI**: Was das Gerüst bewusst offen lässt (Actions, Prüfungen, Bedeutung der
    Radiobuttons, Checkboxen ohne Feldbezug, bei der Custom Entity die Datenbeschaffung, Absprünge,
    Berechtigungen), steht hier als Aufgabenliste mit Fundstellen im Original. Themen abwählen, bei Bedarf
    eine eigene Anweisung ergänzen und den fertigen Prompt kopieren oder per KI-Symbol an den KI-Chat geben.
    „Kontext-Paket (ZIP)" packt Prompt, Original-Quelltext und Archiv zusammen, z. B. für Claude Code.
    BDT ruft dabei selbst keine KI auf — prüfe das Ergebnis der KI, bevor du es einspielst.

Einspielen: im Zielsystem abapGit öffnen (z. B. `ZABAPGIT_STANDALONE`), „New Offline", Paket
wählen, „Import ZIP", „Pull". Die Datei `MIGRATION-NOTES.md` im ZIP listet alle erzeugten Objekte und
offenen Punkte.

> **Achtung:** abapGit überschreibt gleichnamige Objekte ohne Rückfrage. Prüfe vor dem Import,
> dass die Namen im Zielsystem frei sind, sonst Kürzel oder Objektnamen ändern.

## Was bedeuten die Kennzeichen?

- **direkt**: lässt sich ohne Nacharbeit als Filter übernehmen (z. B. `SELECT-OPTIONS … FOR
  tabelle-feld`).
- **manuell**: braucht eine Entscheidung, etwa eine Checkbox ohne Feldbezug oder eine
  Radiobutton-Gruppe.
- **Hinweis**: übernehmbar, aber mit Besonderheit (z. B. ausgeblendetes Feld).

## Tipps & Grenzen

- Die Analyse liest nur den Quelltext; der Report wird nie ausgeführt.
- Fehlt ein Include, fehlen auch die darin enthaltenen `SELECT`s und Feldkataloge. Das Studio
  meldet das als Hinweis.
- Labels mit dem Zusatz „(DDIC)" kommen im System aus dem Datenelement; über „Felder aus DDIC
  laden" siehst du den echten Text.
- Das Gerüst ist rein lesend: Aktionen, Prüflogik und Berechtigungen ergänzt du danach.
- Eigene Dynpros, WRITE-Listen und schreibende Logik werden erkannt und gemeldet, aber nicht
  übernommen.
