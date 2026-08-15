# BDT Hub

Der BDT Hub ist ein optionaler Server-Baustein für alles, was über ein einzelnes Gerät
hinausgeht. Du brauchst ihn nicht, um BDT zu nutzen – ohne ihn läuft alles rein lokal.

## Was der BDT Hub kann

- **Projekte zwischen Geräten synchronisieren:** dieselben Wissensablage-Inhalte und Assets auf
  Laptop, Desktop und einem zweiten Gerät verfügbar haben, inklusive Konflikterkennung, wenn
  beide Seiten dasselbe Objekt geändert haben.
- **Backup off-site:** ein Ende-zu-Ende-verschlüsseltes Backup außerhalb deines Rechners, siehe
  [Backup](backup.md).
- **XR-Sitzungen teilen:** einen XR-Raum oder ein XR-Universum per Link/QR-Code/Meeting-Code mit
  anderen teilen – bis hin zu einem echten Mehrpersonen-Meeting mit Sprachchat, Warteraum und
  eigenem Avatar.
- **Verwaltung:** ein Admin verwaltet Kunden, Organisationen (Tenants) und Personen mit Zugriff,
  vergibt API-Zugänge und behält den Überblick über die genutzte Datenmenge – alles über eine
  eigene BDT-Kachel, keine separate Weboberfläche nötig.

## Einrichten

1. Ein Endpunkt vom Typ „BDT Hub (Backend)" wird in den Einstellungen unter „Endpunkte"
   angelegt – die Adresse und deinen Zugangsschlüssel bekommst du von deinem Admin.
2. Für die Erst-Einrichtung gibt es ein **Konfigurationspaket**: ein Admin erzeugt in der Kachel
   „BDT Hub Verwaltung" eine einzelne, verschlüsselte Datei mit allem Nötigen (Zugang + Projekt-
   Verknüpfung). Du lädst sie einmalig in den Einstellungen hoch und trägst einen dir separat
   mitgeteilten Token ein – Endpunkt, Zugangsdaten und Projekt-Verknüpfung sind danach fertig
   eingerichtet, ohne dass du irgendetwas selbst abtippen musst.
3. Danach verknüpfst du (falls nicht schon durch das Paket geschehen) ein lokales Projekt unter
   „Projekte" → „BDT-Hub-Sync" mit einem Remote-Projekt auf dem Hub.

## Sync bedienen

Push/Pull laufen nie automatisch im Hintergrund – du löst sie bewusst aus und bekommst vorher
immer eine Vorschau (was würde sich ändern?), bevor tatsächlich etwas übertragen wird. Erkennt
BDT einen Konflikt (beide Seiten haben dasselbe Objekt geändert), entscheidest du je Objekt, ob
deine oder die andere Version gelten soll – es wird nie automatisch etwas überschrieben.

## Ohne eigenes Projekt an einem Meeting teilnehmen

Für ein XR-Meeting brauchst du nicht zwingend ein eigenes BDT-Projekt oder einen eigenen Zugang:
über die Karte „Meeting per Code beitreten" im XR-Raum reicht ein von dir eingetippter
Meeting-Code – BDT baut dafür eine anonyme, temporäre Verbindung auf und hinterlässt danach keine
lokalen Spuren.
