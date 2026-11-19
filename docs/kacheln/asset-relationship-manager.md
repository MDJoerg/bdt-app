# Beziehungen

Pflegt Beziehungstypen (z. B. „besteht aus", „ist verbunden mit") und legt Beziehungen zwischen
konkreten Assets an – inklusive einer Ontologie-Baumsicht, die zeigt, welche Beziehungstypen für
welchen Asset-Typ überhaupt erlaubt sind.

## Voraussetzungen

- Ein Projekt mit mindestens einem Asset-Universum.
- Kein SAP-Endpunkt nötig.

## Typischer Ablauf

1. Universum wählen.
2. Beziehungstyp anlegen oder einen bestehenden wiederverwenden.
3. Zwei Assets auswählen (optional einen dritten Partner) und die Beziehung anlegen.
4. Im Baum nachvollziehen, welche Beziehungen zu einem Asset-Typ bereits bestehen bzw. erlaubt
   sind.

## Funktionen im Detail

- Der Experten-Modus schaltet die Baum-Kind-Ebene von reinen Instanzen auf zulässige
  Beziehungstypen samt Ziel-Typen um – hilfreich, um die Struktur eines Universums zu verstehen.
- Beziehungen lassen sich auch direkt im [Asset-Explorer](asset-explorer.md) per Drag & Drop
  zwischen zwei Instanzen anlegen.

- Zusatzattribute eines Beziehungstyps haben einen Datentyp: Text, Zahl, Wahrheitswert, Datum,
  **Datum und Uhrzeit**, **Zeitspanne** (ISO 8601, z. B. `P2D` für zwei Tage, `PT4H` für vier Stunden,
  mit `-` davor für einen Vorlauf) oder **Aufzählung**. Die Werte einer Aufzählung kommen aus dem
  verknüpften semantischen Typ; im Dialog „Neue Beziehung" erscheint dann eine Auswahlliste. Ungültige
  Eingaben werden vor dem Speichern abgewiesen.

## Tipps & Grenzen

- Für eine visuelle, kartenbasierte Bearbeitung eignet sich die
  [Beziehungs-Canvas](asset-relationship-canvas.md) oft intuitiver.
