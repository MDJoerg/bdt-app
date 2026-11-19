# BSP-Studio

Erzeugt aus einem OData-V4-Service-Binding eine Fiori-Elements-App (List Report mit Objektseite) und lädt
sie über deinen SAP-Endpunkt ins BSP-Repository – ohne Business Application Studio, ohne npm und ohne
Build. Auf Wunsch legst du danach Kachel und Target Mapping in einem bestehenden Launchpad-Katalog an.

## Voraussetzungen

- Ein SAP-Endpunkt (On-Premise). Die Anmeldung übernimmt der Endpunkt – auch SSO.
- Ein **publiziertes** OData-V4-Service-Binding.
- Zum Hochladen: am Endpunkt „Schreibzugriffe erlaubt" und in den Einstellungen unter „Erweiterte
  Verwendung" die ADT-Schreibfreigabe. Lesen (Binding, Entitäten, App-Liste, ZIP) geht ohne.
- In der Browser-Erweiterung sollte der Endpunkt `https://` nutzen – schreibende Aufrufe über
  `http://` sind dort unzuverlässig.

## Typischer Ablauf

1. **Service Binding** eingeben oder über die Suchhilfe wählen, **Binding lesen**. Das Werkzeug ermittelt
   die Service-URL und lädt die Entitäten aus `$metadata`. Stimmt die URL nicht, kannst du sie anpassen
   und neu laden.
2. **Entität** wählen (vorgeschlagen wird die Draft-Wurzel), Titel und Beschreibung prüfen.
3. **Paket, BSP-Name, Transport**: `$TMP` braucht keinen Auftrag, sonst einen Transportauftrag eingeben,
   prüfen oder neu anlegen. BSP-Name (höchstens 15 Zeichen), App-ID und semantisches Objekt sind
   vorbelegt.
4. **Dateien erzeugen**: manifest.json, Component.js, i18n und optional index.html. Klick auf eine Datei
   zeigt den Inhalt. Existiert die App schon, siehst du je Datei „neu", „geändert", „unverändert" oder
   „wird gelöscht". **Hochladen** legt die App an oder aktualisiert sie; danach öffnet der Link die App
   direkt im Browser.
5. **Kachel anlegen** (optional): Katalog wählen, Titel/Untertitel/Symbol setzen. Target Mapping und
   Kachel landen im Katalog; der Link öffnet die App im Launchpad.

Jeder Schritt bleibt änderbar – änderst du ein früheres Feld, springt der Assistent dorthin zurück.

## Bestehende Apps

Im Bereich **Bestehende Apps** lädst du die Liste der BSP-Anwendungen des Systems, filterst sie und
lädst eine App als ZIP herunter.

## Tipps & Grenzen

- Die App kommt ohne `Component-preload.js` aus; das System pflegt den App-Index beim Hochladen selbst.
- Ein Update ersetzt die App vollständig: Dateien, die im neuen Stand fehlen, werden im System gelöscht.
- Kacheln entstehen nur in Customizing-Katalogen (mandantenabhängig). Konfigurations-Kataloge brauchen
  einen Workbench-Auftrag und sind noch nicht unterstützt.
- Kacheln landen im Customizing-Auftrag aus deinem Benutzerparameter `/UI2/WD_TRKORR_CUST` (Transaktion SU3,
  Reiter „Parameter“). Der Auftrag muss offen sein und eine offene Aufgabe für deinen Benutzer haben, sonst
  meldet das System „Keine geeignete Aufgabe verfügbar …“. Abhilfe: Parameter pflegen oder in SE09/SE10 am
  Auftrag mit „Benutzer hinzufügen“ eine Aufgabe für dich anlegen. Das Werkzeug zeigt diesen Hinweis bei der
  Meldung mit an.
- Kataloge sind nur in ihrer Originalsprache änderbar – das Werkzeug schreibt automatisch in dieser
  Sprache.
- Die Kachel ist erst sichtbar, wenn der Katalog einer Rolle des Anwenders zugeordnet ist.
- ABAP Cloud (BTP) wird noch nicht unterstützt.
