# Kanban

Ein Kanban-Board über deine Wissensablage. Die Spalten entstehen aus einer Taxonomie deines
Projekts, jede Karte ist ein Infoobjekt. Wichtig: Eine Karte in eine andere Spalte zu ziehen ist
keine rein visuelle Markierung – es ändert wirklich die Taxonomie-Zuordnung (bzw. die
Asset-Verknüpfung) des zugrunde liegenden Objekts.

## Voraussetzungen

- Ein Projekt mit mindestens einer geeigneten (einwertigen) Taxonomie, aus der die Spalten
  gebildet werden können.
- Kein SAP-Endpunkt nötig.

## Typischer Ablauf

1. Spalten-Taxonomie auswählen – daraus entstehen die Board-Spalten.
2. Optional zusätzlich nach einer zweiten Taxonomie oder Asset-Zuordnung gruppieren, um mehrere
   Boards nebeneinander zu bekommen.
3. Karten bei Bedarf filtern (dieselben Möglichkeiten wie bei der [Suche](search.md)).
4. Karten per Drag&Drop oder über den Verschieben-Dialog in eine andere Spalte bringen.
5. Die aktuelle Konfiguration als Profil speichern, damit sie beim nächsten Besuch wieder steht.

## Funktionen im Detail

- Board-Profile werden am Projekt gespeichert – mehrere Boards (z. B. „nach Status" und „nach
  Verantwortlichem") lassen sich parallel pflegen.
- Der Verschieben-Dialog ist eine Alternative zum Ziehen, z. B. bei vielen Spalten oder auf
  kleinen Bildschirmen.

## Tipps & Grenzen

- Weil ein Kartenzug die Taxonomie wirklich ändert, eignet sich Kanban nicht für eine rein
  visuelle Ablage ohne Bezug zur zugrunde liegenden Struktur – überlege dir vorher, welche
  Taxonomie inhaltlich als „Status" funktioniert.
- Das Clean Core Cockpit nutzt eine eigene, vorbereitete Backlog-Taxonomie – wenn du von dort
  „Replacement Cards" erzeugst, tauchen sie automatisch als Karten in einem passenden Board auf.
