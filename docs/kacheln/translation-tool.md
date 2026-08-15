# Übersetzungswerkzeug

Vergleicht Quell- und Zielsprache von übersetzungsrelevanten SAP-Texten (z. B. Datenelemente,
Nachrichtenklassen, Domänen-Festwerte, CDS-/Fiori-Elements-Bezeichner) und zeigt, wo eine
Übersetzung fehlt, zu lang ist oder identisch mit dem Quelltext ist. Entwürfe für fehlende
Übersetzungen lassen sich von Hand oder mit KI-Unterstützung erstellen – und für einen Teil der
Objekttypen direkt zurück ins SAP-System einspielen.

## Voraussetzungen

- Ein eingerichteter SAP-Endpunkt.
- Für das **Zurückschreiben** zusätzlich: ein separat auf deinem SAP-System zu installierender
  offener LISA-Handler, das Häkchen „Schreibzugriffe erlauben" unter „Erweiterte Verwendung",
  sowie „Schreibzugriffe erlaubt" am Endpunkt selbst. Ohne LISA funktionieren Anzeige und
  manuelle Entwurfserstellung trotzdem – nur das Einspielen fehlt dann.
- Für „Mit KI übersetzen"/„Mit KI kürzen" ein eingerichteter KI-Anbieter.

## Typischer Ablauf

1. Paket-/Objekt-Auswahl treffen, Objekttypen ankreuzen, Quell-/Zielsprache wählen (die
   führende Sprache wird automatisch vorgeschlagen).
2. Suchen – die Ergebnistabelle zeigt je Zeile Quelltext, aktuellen Zieltext und einen
   Prüfstatus (ok/fehlt/zu lang/gleich wie Quelltext/…).
3. Fehlende oder unpassende Texte im Entwurfsfeld bearbeiten – von Hand, per „Mit KI
   übersetzen" oder per „Mit KI kürzen" (liefert mehrere Alternativen zur Auswahl).
4. Fertige Zeilen markieren, „Auswahl einspielen" – Transportauftrag wählen/anlegen, Ergebnis
   je Objekt einzeln zurückmelden.

## Funktionen im Detail

- Ein Filter-Seitenpanel grenzt nach Typ, Status, Paket und Texttyp ein.
- Status „geprüft" sperrt eine Zeile bewusst gegen weitere (auch automatisierte) Änderungen.
- „Entwurf verwerfen" stellt gezielt den letzten automatisch gesetzten Vorschlag wieder her,
  nicht einfach ein leeres Feld.
- Domänen-Festwerte/CDS-Feld-Bezeichner haben eine bekannte Maximallänge – ein „Kürzen"-Knopf
  hilft bei Überlänge.

## Tipps & Grenzen

- Zurückschreiben funktioniert (Stand jetzt) für Datenelemente, Nachrichtenklassen,
  Domänen-Festwerte, CDS-Views/Metadata Extensions und Funktionsgruppen-Textsymbole – für
  Klassen-Textsymbole und einige Sonderfälle bleibt es vorerst nur lesend.
- Ein Schreibversuch in die von SAP erkannte Originalsprache eines Objekts wird von LISA
  bewusst abgelehnt (keine „Übersetzung" der Ursprungssprache) – die Fehlermeldung erklärt das
  und verweist auf den passenden klassischen Pflegeweg.
