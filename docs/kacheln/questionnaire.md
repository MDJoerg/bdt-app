# Fragebogen

Fragebögen als Teilmodelle: ausgeben, am Objekt ausfüllen und über Objekte, Asset-Typen und
Fragebögen hinweg auswerten.

## Voraussetzungen

- Ein Projekt mit einem Asset-Universum und mindestens einem Fragebogen. Der Fragebogen ist ein
  Datenmodell mit dem Merkmal „Fragebogen“ ([Semantische Typen & Datenmodelle](asset-model-manager.md)).
  Die Vorlage „Fragebogen“ (Einstellungen › Assets › Universum aus Vorlage) bringt ein Beispiel mit.
- Kein SAP-Endpunkt nötig.

## Typischer Ablauf

1. Fragebogen anlegen: Datenmodell mit Fragen als Elementen; jede Frage bekommt einen Begriff
   (Semantische Typen), an dem die Antwortmöglichkeiten stehen (z. B. Skala 1–5).
2. „Bogen ausgeben …“ legt den Bogen an allen Objekten eines Typs an, die ihn noch nicht haben.
3. Ausfüllen im [Asset-Explorer](asset-explorer.md) auf der Objektseite (Teilmodell-Formular);
   ein Klick auf den Objektnamen in „Antworten je Objekt“ springt dorthin.
4. Auswerten in dieser Kachel.

## Funktionen im Detail

- **Auswertung je Frage:** Verteilung bei Auswahlfragen, Mittelwert und Spanne bei Zahlen, die
  Antworten bei Freitext, darunter die Aufteilung nach Asset-Typ.
- **Identität der Frage:** Maßgeblich ist die semanticId der Frage, nicht der Bogen. Tragen zwei
  Fragebögen oder zwei Typen dieselbe Frage, werden ihre Antworten gemeinsam gezählt.
- **Antworten je Objekt:** eine Zeile je Objekt und Bogen, „Nur unvollständige“ zeigt Pflichtfragen
  ohne Antwort. Export als Tabelle.

## Tipps & Grenzen

- Revisionen der Antworten (wer hat wann was geändert) und das Verteilen an Personen ohne BDT folgen
  mit dem BDT Hub.
- Eine Frage ohne Begriff wird nur innerhalb ihres Fragebogens ausgewertet.
