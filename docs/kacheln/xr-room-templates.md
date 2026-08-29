# XR-Raum-Vorlagen

Verwaltung der **Raum-Vorlagen** für die Kachel [XR-Raum](xr-room.md): eine projekteigene Bibliothek
gespeicherter Szenen (Raum-Hülle, Bausteine, Anordnung), aus der du direkt eine neue XR-Szene startest.

## Voraussetzungen

- Ein Projekt.
- Kein SAP-Endpunkt nötig.
- Mindestens eine im [XR-Raum](xr-room.md) gespeicherte Szene, die du als Vorlage ablegen willst.

## Typischer Ablauf

1. Im [XR-Raum](xr-room.md) eine Szene bauen und die Anordnung speichern.
2. Hier „Aktuelle Szene als Vorlage speichern …" – die Szene wird als eigenständige Vorlage dupliziert.
3. Später „Szene starten" an einer Vorlage: der XR-Raum öffnet sich in der Vorlagen-Vorschau; „Als eigene
   Szene übernehmen" macht daraus wieder eine bearbeitbare Projekt-Szene.

## Funktionen im Detail

- Liste aller Vorlagen des Projekts mit Kurzfassung des Inhalts und Änderungsdatum.
- „Szene starten", „Umbenennen", „Löschen" je Vorlage.
- Die Kachel rendert selbst keine 3D-Szene – alles Darstellen und Bewegen bleibt im XR-Raum.

## Tipps & Grenzen

- Vorlagen erscheinen bewusst nicht in der normalen Szenen-Suche des XR-Raums, damit sich Vorlage und
  Arbeitsstand nicht vermischen.
- Ein Kompositions-Editor (mehrere Vorlagen zu einer Szene kombinieren) ist noch nicht Teil dieser Kachel.
