# Grundkonzepte

Ein paar Begriffe tauchen in fast jeder Kachel auf. Wenn du sie einmal verstanden hast, findest
du dich in jedem Werkzeug sofort zurecht.

## Launchpad

Die Startseite von BDT ist ein Launchpad im Fiori-Kachel-Design: Kacheln, gruppiert nach Thema
(Wissen, Kreativität, ADT Tools, KI Tools, …), jede Kachel öffnet ein eigenständiges Werkzeug.
Du kannst Kacheln als Favorit markieren (Stern), die Reihenfolge der Gruppen anpassen und die
Sichtbarkeit einschränken – dazu mehr in den [Tipps](tipps.md).

## Projekte

Alles, was du in BDT anlegst – Wissensablage-Inhalte, Assets, Endpunkte, Einstellungen für
einzelne Werkzeuge – gehört zu einem **Projekt**. Du kannst beliebig viele Projekte anlegen, z. B.
eines je Kunde oder je System-Landschaft, und jederzeit zwischen ihnen wechseln (unten in der
Fußzeile jeder Seite). Ein neues Projekt ist leer und komplett getrennt von den anderen.

Projekte lassen sich vollständig exportieren und wieder importieren – praktisch für ein Backup
oder um sie an Kolleg:innen weiterzugeben. Details: [Backup](../experten/backup.md).

## Endpunkte

Ein **Endpunkt** ist eine Verbindung zu einem System außerhalb von BDT: ein SAP-System (ADT/
OData), ein generischer HTTP-Dienst, ein KI-Anbieter, eine BaSyx-Instanz oder ein BDT Hub.
Du richtest Endpunkte einmal in den Einstellungen ein (URL, Anmeldeart, ggf. Zugangsdaten) und
wählst sie dann unten in der Fußzeile jeder Kachel aus, die einen Endpunkt braucht.

Viele Kacheln – Wissensablage, alle Kreativ-Editoren, das Daten-Studio (ohne OData-Anbindung) –
brauchen **gar keinen Endpunkt** und funktionieren komplett offline.

BDT ruft **nie von sich aus** ein fremdes System auf. Ein Netzwerkzugriff passiert nur, wenn du
ihn auslöst (z. B. „Suchen" klicken) und nur an den Endpunkt, den du selbst konfiguriert hast.

## Der Tresor (Vault)

Zugangsdaten (Passwörter, API-Keys, Tokens) landen nie im Klartext, sondern verschlüsselt im
**Vault** – einem Tresor, den du mit einem eigenen Master-Passwort schützt. Beim ersten
Verbindungsaufbau musst du den Vault entsperren; danach bleibt er für die Sitzung offen (Schloss-
Symbol in der Kopfzeile). Vergisst du das Master-Passwort, sind die gespeicherten Zugangsdaten
verloren – du müsstest sie neu eintragen.

## Wissensablage

Die Wissensablage ist die zentrale Notiz- und Wissensablage von BDT: Markdown-Seiten, Diagramme,
Whiteboards, JSON, Folien, Mindmaps, Grafiken und mehr – organisiert in Ablagen/Taxonomien,
durchsuchbar per Volltext- und Vektorsuche (KI-gestützt), mit Kalender- und Kanban-Sicht. Fast
jeder Kreativ-Editor speichert direkt dorthin.

## Fußzeilen-Kontext

Am unteren Rand jeder Seite findest du eine Kontextleiste: aktuelles Projekt, aktueller Endpunkt
(sofern relevant), bei manchen Kacheln zusätzlich ein Universum oder ein Zeitpunkt. Diese Auswahl
gilt seitenübergreifend – wechselst du das Projekt, wechseln alle Kacheln automatisch mit.

## Sammelkörbe

Ein Sammelkorb sammelt Objekte aus verschiedenen Werkzeugen (Suchtreffer, Tabellenzeilen,
Diagramm-Ausschnitte, …), damit du sie gebündelt weiterverarbeiten kannst – z. B. in die
Wissensablage übernehmen, als Datensatz im Daten-Studio öffnen oder dem KI-Chat als Kontext
mitgeben. Das Korb-Symbol in der Kopfzeile zeigt an, wie viele Objekte gerade gesammelt sind.

## Erweiterte Verwendung

Ein paar Funktionen laden Inhalte von externen Quellen nach (z. B. der Draw.io-Diagramm-Editor
oder der Import von 3D-Modellen im XR-Raum). Aus Datenschutz-/Sicherheitsgründen sind diese
Funktionen standardmäßig **aus** – du schaltest sie einzeln in den Einstellungen unter
„Erweiterte Verwendung" frei, bevor du sie zum ersten Mal nutzt. Die Seite zeigt alle Freigaben
kompakt in Gruppen (SAP-System schreiben, externe Dienste, Code ausführen, KI über MCP-Kanäle);
das „?" je Zeile erklärt, was genau freigegeben wird.

## Asset-Universen

Neben der Wissensablage (Dokumente, Diagramme, Notizen) kennt BDT **Assets**: strukturierte
Objekte wie Systeme, Rollen, Prozesse, Aufgaben oder Geräte, jeweils mit Feldern und Beziehungen
untereinander. Grundlage ist der Industrie-Standard „Asset Administration Shell“ (AAS).

Assets leben in einem **Universum** – einer thematischen Sammlung innerhalb eines Projekts, z. B.
„Systemlandschaft Kunde A“ oder „Vorgänge“. Ein Universum legt fest, welche **Asset-Typen** es gibt,
welche Felder sie haben (über **Datenmodelle**) und welche **Beziehungstypen** zwischen ihnen
erlaubt sind. Du musst das nicht von Hand aufbauen: in den Einstellungen unter „Assets“ legt
„Universum aus Vorlage“ fertige Modelle an (z. B. Vorgänge, Projektleiter, Anwendungen und
Datenflüsse).

Das aktuelle Universum wählst du im Fußzeilen-Kontext. Viele Kacheln arbeiten darauf: Asset-Explorer,
Beziehungen, Gantt, RACI-Matrix, Architektur-Studio, Graph-Viewer und das XR-Universum.

## Ordner-Sync

Die Inhalte eines Projekts liegen zunächst nur im Browser. Mit dem **Ordner-Sync** gleicht BDT ein
Projekt mit einem Ordner auf deinem Rechner ab – als Markdown-Dateien mit Kopfzeilen, Bilder und
Anhänge daneben. So kannst du dieselben Inhalte in Obsidian lesen, mit Git versionieren oder über
OneDrive bzw. ein Netzlaufwerk mit Kolleg:innen teilen.

Eingerichtet wird der Abgleich in der Kachel **Sync-Center**. Je Verbindung legst du fest, wer führt
(BDT, der Ordner oder beide als Partner), und startest zuerst einen Probelauf, der nur zeigt, was
passieren würde. Bei Konflikten entscheidest du selbst. Löschen passiert nur, wenn du es ausdrücklich
freigibst.

## KI und MCP-Gateway

BDT bringt einen eigenen **KI-Chat** mit (auf jeder Seite als Seitenleiste), der mit einem Modell
deiner Wahl arbeitet: dem eingebauten Chrome-Modell oder einem OpenAI-kompatiblen Anbieter wie
Ollama, LM Studio oder einem Firmen-Gateway.

Umgekehrt kann eine **externe KI** (z. B. Claude Code, Copilot oder ein eigener Agent) BDT bedienen –
über das **MCP-Gateway**. Jede Kachel, die das unterstützt, hat einen Kanal-Schalter; ist er an,
kann die KI dort lesen und – nur nach deiner Freigabe – schreiben, etwa Karten aufs Whiteboard legen,
ein Mockup ergänzen oder Assets anlegen. Der Kanal **Remote Control** (`rc`) lässt die KI zusätzlich
Kacheln finden und öffnen. Welche Kanäle freigegeben sind und was die KI gerade tut, siehst du im
Leitstand auf dem Launchpad. Einrichten: Kachel MCP-Konfigurator und Einstellungen → Verbindungen › MCP.
