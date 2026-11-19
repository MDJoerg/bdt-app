# Asset-Verwaltung

Legt Asset-Typen und -Instanzen an und pflegt sie – das Werkzeug, mit dem ein
[Asset-Universum](asset-explorer.md) überhaupt erst entsteht.

## Voraussetzungen

- Ein Projekt.
- Kein SAP-Endpunkt nötig.

## Typischer Ablauf

1. Neues Universum anlegen (oder ein bestehendes über den Fußzeilen-Kontext wählen).
2. Asset-Typ anlegen und mit einem Datenmodell verknüpfen (siehe
   [Semantische Typen & Datenmodelle](asset-model-manager.md)).
3. Instanzen dieses Typs anlegen – das Formular richtet sich automatisch nach dem gewählten
   Datenmodell.
4. Pflegen: Werte ändern, Typen umbenennen, Instanzen löschen.

## Funktionen im Detail

- Änderungen an einem Typ (z. B. neue Felder im Datenmodell) wirken sich auf alle Instanzen
  dieses Typs aus.

## CDS/RAP-Gerüst erzeugen

Das Symbol `<>` über dem Typen-Baum erzeugt aus den Asset-Typen und ihren Datenmodellen ein abapGit-ZIP für
die Umsetzung in SAP: je Typ eine Tabelle, Basis-View, Projektion, UI-Annotationen und Verhaltensdefinition,
dazu Service-Definition und -Binding (OData V4). Wertelisten werden Festwert-Domänen, Verweise und
n:1-Beziehungen werden Assoziationen. Was das Gerüst nicht abbildet (z. B. n:m-Beziehungen), steht in der
mitgelieferten README.md. Du kannst jede Datei vorab ansehen, das ZIP herunterladen oder es direkt im
abapGit Studio öffnen. Ins System wird nichts geschrieben.

## MCP-Tools als Funktionen übernehmen

Das Symbol neben `<>` liest die Tools eines MCP-Servers – aus dem MCP Simulator, über ein
MCP-Inspector-Profil oder als eingefügtes tools/list-JSON – und legt sie als Funktionen mit
Art „MCP-Tool" an. Sie hängen an einem Modul (dem MCP-Server), das zum gewählten System gehört.
Vorhandene Funktionen gleichen Namens werden übersprungen; höchstens 49 Tools je Lauf.

## Für externe KI freigeben (MCP)

Externe MCP-Clients wie Claude Code, VS Code oder goose erreichen das gewählte Universum über das
BDT-MCP-Gateway: einmal unter Einstellungen → Verbindungen › MCP „BDT als MCP-Server" aktivieren, dann hier den
Knopf **„Kanal für externe KI"** (Stecker-Symbol) einschalten – oder direkt in der Gateway-Karte
„Kachel öffnen" klicken. Die KI kann lesen und Änderungen planen. Geschrieben wird nur, wenn unter
Einstellungen → MCP → Freigaben „KI darf Assets anlegen und ändern" angehakt ist – und erst,
wenn du die Änderungsliste im offenen Tab bestätigst. Gelöscht wird nie. Das geht nur in der Webapp
und in der VS-Code-Erweiterung, und der Tab muss offen bleiben. Anleitung:
[BDT mit Claude fernsteuern](../quickstart/mcp-claude-code.md).

## Beziehungen und Begriffe zu BaSyx schreiben

Im Dialog „Synchronisieren" (Aktionsmenü eines Asset-Typs, Universum im Modus „sync") schreibt BDT
bisher die Shells. Mit dem Häkchen **„Beziehungen und Begriffe mitschreiben"** kommen dazu:

- je Quell-Asset ein Submodell **„Relationships"** mit den ausgehenden Beziehungen. Zeitraum,
  Richtung, Kontext und alle Zusatzattribute (z. B. Abhängigkeitsart und Versatz) stehen als
  Annotationen darin;
- die **Begriffe** (semantische Typen), die diese Attribute verwenden, samt Aufzählungswerten.
  Begriffe aus einem externen Standard bleiben unberührt.

Der Dry Run zeigt zuerst, was neu angelegt, aktualisiert oder unverändert ist. Er schreibt nichts.
Beziehungen, deren Partner noch keinen Schlüssel hat, werden übersprungen und im Dry Run genannt. Ein
Submodell, das auf dem Server liegt, obwohl es lokal keine Beziehungen mehr gibt, wird gemeldet,
aber nie gelöscht. Fremde Submodell-Verweise an einer Shell bleiben erhalten.

## Teilmodelle zu BaSyx schreiben

Das zweite Häkchen **„Teilmodelle mitschreiben"** im Dialog „Synchronisieren" ergänzt:

- je verwendetem Datenmodell ein Submodell als **Vorlage** (Template);
- je Teilmodell-Instanz der Objekte ein Submodell mit den **ausgefüllten Werten**. Verweise auf andere
  Objekte werden als Referenz auf deren Shell geschrieben, wenn das Objekt einen Schlüssel hat.

Objekte ohne Schlüssel und Instanzen ohne Datenmodell werden im Dry Run genannt und übersprungen.
Leere Felder werden nicht geschrieben. Es wird nichts auf dem Server gelöscht.

## Tipps & Grenzen

- Zum reinen Ansehen/Bearbeiten bestehender Instanzen (statt Neuanlage) ist der
  [Asset-Explorer](asset-explorer.md) meist der schnellere Weg.
