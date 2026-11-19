# Asset-Explorer

Der Haupteinstieg in die Asset-Verwaltung: eine Übersicht aller Asset-Typen (List Report), von
dort in eine einzelne Instanz (Object Page) mit allen Feldern, wahlweise auch als Baum- oder
Graph-Sicht auf die Beziehungen zwischen Assets.

Ein **Asset** ist ein digitales Abbild eines realen oder gedachten Objekts (z. B. eine Maschine,
eine Komponente, ein Dokument) nach dem Industrie-4.0-Standard „Asset Administration Shell"
(AAS). Assets gehören zu einem **Universum** – einer thematischen Sammlung, die du über den
Fußzeilen-Kontext auswählst.

## Voraussetzungen

- Ein Projekt mit mindestens einem Asset-Universum (angelegt in der
  [Asset-Verwaltung](asset-manager.md)).
- Kein SAP-Endpunkt nötig.

## Typischer Ablauf

1. Universum im Fußzeilen-Kontext wählen.
2. Asset-Typ auswählen – die Liste zeigt alle Instanzen dieses Typs.
3. Eine Instanz öffnen (Object Page) – alle Felder gemäß dem zugehörigen Datenmodell.
4. Zwischen Listen-, Baum- und Graph-Sicht wechseln, je nachdem, ob du eine flache Liste, eine
   Hierarchie oder Beziehungen visuell sehen willst.
5. Optional in den Bearbeitungsmodus wechseln und Werte ändern.

## Funktionen im Detail

- **Baumsicht:** Gruppe → Typ → Instanz, mit automatischer Bucket-Bildung bei sehr vielen
  Instanzen desselben Typs.
- **Graph-Modus:** zeigt ein Fokus-Asset mit seinen direkten Nachbarn; ein Klick auf einen
  Nachbarn wechselt den Fokus dorthin.
- **Aufgabe anlegen:** in der Objektseite legt der Knopf „Aufgabe anlegen“ eine Aufgabe an, die das
  Objekt betrifft (Beziehung „betrifft“), optional mit Plan-Start und Plan-Ende. Voraussetzung ist die
  Vorlage „Vorgänge“; die Aufgaben erscheinen im [Gantt](gantt.md).

## Tipps & Grenzen

- Neue Asset-Typen/-Instanzen legst du in der [Asset-Verwaltung](asset-manager.md) an, nicht
  hier im Explorer.
