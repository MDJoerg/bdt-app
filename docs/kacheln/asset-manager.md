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

## Tipps & Grenzen

- Zum reinen Ansehen/Bearbeiten bestehender Instanzen (statt Neuanlage) ist der
  [Asset-Explorer](asset-explorer.md) meist der schnellere Weg.
