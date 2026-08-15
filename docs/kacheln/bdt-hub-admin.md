# BDT Hub Verwaltung

Self-Service-Verwaltung für Kunden-Admins: pflegt den eigenen Baum-Ausschnitt im
[BDT Hub](../experten/bdt-hub.md) – Tenants, Subtenants, Personen, Mitgliedschaften, API-Zugänge
und Projekte – ohne eine separate Weboberfläche außerhalb von BDT.

## Voraussetzungen

- Ein eingerichteter BDT-Hub-Endpunkt mit einem Zugang, der Verwaltungsrechte hat (Kunden-Admin
  oder höher).

## Typischer Ablauf

1. Kunden-ID eingeben – lädt den zugehörigen Baum (Tenants/Subtenants/Personen/Mitgliedschaften/
   API-Keys/Projekte).
2. Im Baum navigieren, per Rechtsklick oder über das Detail-Panel Einträge anlegen/ändern/
   widerrufen.
3. Einen API-Zugang erzeugen – der Klartext-Token wird dir genau einmal angezeigt, danach nicht
   mehr abrufbar.

## Funktionen im Detail

- Root-Zugänge sehen zusätzlich „Als Root: Kunden verwalten" (Kundenliste, Neuanlage) – ein
  reiner Kunden-Admin-Zugang bekommt hier eine ehrliche Fehlermeldung statt eines leeren
  Ergebnisses.
- Ein „Konfigurationspaket" bündelt Zugang + Endpunkt + Projekt-Verknüpfung in einer
  verschlüsselten Datei, die eine andere Person nur noch hochladen muss (siehe
  [BDT Hub](../experten/bdt-hub.md)).
- „Nutzung anzeigen" liefert eine reine Mengenübersicht je Tenant/Subtenant (Anzahl + letzte
  Änderung je Kategorie), ohne Einzelinhalte zu zeigen.

## Tipps & Grenzen

- Ein reiner Tenant-Admin-Zugang kann seinen Bereich in der aktuellen Version noch nicht selbst
  über diese Kachel entdecken – dafür braucht es (noch) einen Kunden-Admin-Zugang.
- Ein einmal angezeigter Klartext-Token lässt sich später nicht erneut abrufen – notiere ihn
  sofort sicher, oder erzeuge im Zweifel einen neuen.
