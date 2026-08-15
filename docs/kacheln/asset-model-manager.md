# Semantische Typen & Datenmodelle

Pflegt die Bausteine, aus denen sich Asset-Typen zusammensetzen: Concept Descriptions
(semantische Typen, z. B. „Temperatur" oder „Seriennummer" mit einer eindeutigen Bedeutung) und
Submodel-Templates (wiederverwendbare Feldgruppen).

## Voraussetzungen

- Ein Projekt.
- Kein SAP-Endpunkt nötig.

## Typischer Ablauf

1. Semantischen Typ anlegen (Bezeichnung, Datentyp, Einheit).
2. Submodel-Template aus mehreren semantischen Typen zusammenstellen.
3. Das Template in der [Asset-Verwaltung](asset-manager.md) einem Asset-Typ zuordnen.

## Funktionen im Detail

- Semantische Typen sind wiederverwendbar über mehrere Asset-Typen/Universen hinweg – einmal
  „Seriennummer" definiert, überall gleich verwendbar.

## Tipps & Grenzen

- Eine Änderung an einem bereits genutzten Datenmodell wirkt sich auf alle Asset-Typen aus, die
  es verwenden – prüfe vorher, wo es schon im Einsatz ist.
