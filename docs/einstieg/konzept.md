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
„Erweiterte Verwendung" frei, bevor du sie zum ersten Mal nutzt.
