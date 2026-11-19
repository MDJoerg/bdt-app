# ABAP Generator

Legt ABAP-Objekte (CDS-Views, Tabellen, Klassen, RAP-Objekte, Services) kontrolliert im SAP-System an,
ändert sie und nimmt sie wieder zurück. Grundlage ist ein **Erzeugungsplan**, den andere Kacheln wie
der Datenkatalog erzeugen oder den du als Datei öffnest. Jeder Lauf wird als **Laufprotokoll** in der
Wissensablage gesichert, bevor etwas geschrieben wird.

## Voraussetzungen

- Ein Projekt (Fußzeile): Die Laufprotokolle liegen in dessen Wissensablage.
- Zum Schreiben ein SAP-Endpunkt mit **Stufe 2 oder höher** (Einstellungen → Endpunkte, „ABAP Generator:
  Stufe", „Schreibzugriffe erlaubt") und in der Erweiterten Verwendung die Häkchen „ADT-Schreibzugriffe"
  und „ABAP-Objekte generieren". Prüfen geht auch mit Stufe 1.

## Typischer Ablauf

1. **Plan öffnen …** lädt einen Plan als JSON (`bdt-abap-plan/1`) oder ein abapGit-ZIP. Pläne aus einer
   Kachel (z. B. Datenkatalog „Im System anlegen …") öffnen denselben Dialog direkt.
2. Im Dialog **Generieren …**: Plan ansehen → Ziel wählen (System, Paket, Transportauftrag, Kommentarkopf,
   Release-Profil) → **Prüfen** (liest nur) → optional **Probelauf …** (Wegwerf-Namen in `$TMP`, danach
   wieder gelöscht) → **Jetzt ausführen**.
3. Die Liste zeigt alle Läufe des Projekts (Ausführungen und Probeläufe) mit Status und Ergebnis. Ein
   Klick öffnet das Laufprotokoll mit **Rückabwickeln …**.

## KI über MCP (Kanal abap)

Der Knopf rechts oben schaltet den Kanal `abap` am BDT-MCP-Gateway ein. Eine externe KI kann dann
Systeme und Läufe lesen, Objekte aus dem System lesen, Pläne prüfen, proben, ausführen und zurücknehmen.

- Schreiben braucht zusätzlich das Häkchen **KI darf ABAP-Objekte generieren** (Einstellungen › MCP ›
  Freigaben, Bereich „ABAP Generator").
- **Jeder schreibende Schritt** (Probelauf, Ausführen, Rückabwickeln) zeigt im Tab eine Bestätigung –
  auch wenn der Bereich auf „Frei bis auf Widerruf" steht.
- Die Stufe am Endpunkt und alle Häkchen stellt nur der Anwender ein, nie die KI.

## Hinweise

- Alles wird zuerst geschrieben und dann gemeinsam aktiviert. Abbrechen wirkt zwischen zwei Objekten.
- Rückabwickeln hält an, wenn sich ein Objekt seit dem Lauf geändert hat, und fragt dann nach.
- Strukturen (TABL/DS) und Nachrichtenklassen lassen sich planen und als abapGit ausgeben, aber noch
  nicht über ADT schreiben.
