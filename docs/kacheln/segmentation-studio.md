# Segmentierungs-Studio

Modelliert Datenmengen als Knoten auf einer Fläche und kombiniert sie über Mengenoperationen –
z. B. „Kunden, die einen Ansprechpartner haben" und „Kunden, die keinen haben" aus einer
gemeinsamen Quelle berechnen. Für komplexere, wiederverwendbare Auswertungen als eine einfache
Filterung im [Daten-Studio](data-studio.md).

## Voraussetzungen

- Ein Projekt mit mindestens zwei Datasets im Daten-Studio (für eine Kombination – ein einzelner
  Filter-Knoten funktioniert auch mit nur einem Dataset).

## Typischer Ablauf

1. Datenquellen-Knoten aus deinen Daten-Studio-Datasets auf die Fläche ziehen.
2. Bei Bedarf einen Filter-Knoten anschließen (Kriterien, Rang-Dedublizierung je Gruppe oder
   eine Zufalls-Stichprobe).
3. Zwei Zweige über einen Kombinationsknoten verknüpfen – liefert automatisch drei Ausgänge:
   Schnittmenge, nur die eine Seite, nur die andere Seite.
4. Optional einen Veredelungs-Knoten anhängen (z. B. eine berechnete Zusatzspalte).
5. Am Export-Knoten die gewünschten Spalten wählen und als neues Dataset/Datei/Sammelkorb-
   Eintrag exportieren.
6. Optional „Lauf aufheben" – speichert einen Snapshot samt Ergebnistabellen in der
   Wissensablage.

## Funktionen im Detail

- Ein Knoten zeigt sichtbar an, ob sein Ergebnis „veraltet" ist (eine vorgelagerte Quelle hat
  sich geändert) – Neuberechnung ist bewusst nie automatisch, sondern ein eigener Klick.
- Die Berechnung läuft im Hintergrund (Web Worker), die Oberfläche bleibt währenddessen
  bedienbar.
- Beziehungsvorschläge zwischen Datasets nutzen dieselbe semantische Typ-Zuordnung wie der
  Daten-Navigator im Daten-Studio.

## Tipps & Grenzen

- Für eine einfache, einmalige Filterung reicht ein Segment im [Daten-Studio](data-studio.md) –
  das Segmentierungs-Studio lohnt sich, sobald mehrere Datenquellen kombiniert werden.
