# Clipboard-Util

Überträgt eine Datei (z. B. ein ZIP) in Paketen über die Zwischenablage – etwa aus einem Cloud-PC,
wenn außer der Zwischenablage nichts durchgereicht wird. Die Kachel läuft auf beiden Seiten.

## Voraussetzungen

- Kein Projekt, kein Endpunkt, kein Secret nötig. Es gibt keinen Netzwerkzugriff.
- Die Kachel ist auf Sender und Empfänger geöffnet (z. B. Webapp im Cloud-PC, Erweiterung lokal).
- Kopieren braucht einen sicheren Kontext (HTTPS, localhost oder die Erweiterung).

## Typischer Ablauf

1. Auf beiden Seiten dieselbe **Paketgröße** eintragen (Zeichen je Paket).
2. Sender: **Größentest kopieren**, beim Empfänger im Einfügefeld Strg+V drücken. Kommt weniger an,
   setzt der Empfänger einen kleineren Wert – diesen auch beim Sender eintragen.
3. Sender: Datei wählen, optional eine **Phrase**, **Pakete vorbereiten**. Die Kachel zeigt vorab,
   wie viele Pakete es werden.
4. Sender: **Paket … kopieren**, Empfänger: einfügen – so lange, bis alle Pakete angekommen sind.
   Beide Seiten zeigen den Fortschritt, der Empfänger nennt fehlende Paketnummern.
5. Empfänger: **Prüfen und speichern unter …**.

## Funktionen im Detail

- **Senden / Empfangen:** zwei Bereiche auf derselben Seite. Die Datei ziehst du beim Sender in das
  Feld oder wählst sie per Klick.
- **Erneut kopieren:** „Letztes erneut kopieren“ oder ein Klick auf eine Paketnummer kopiert genau
  dieses Paket noch einmal. Reihenfolge ist egal, doppelte Pakete werden erkannt.
- **Einfügen beim Empfänger:** Strg+V im Einfügefeld oder „Aus Zwischenablage lesen“;
  „Zurücksetzen“ verwirft einen angefangenen Empfang.
- **Prüfsummen:** Jedes Paket trägt eine CRC32-Prüfsumme; die ganze Datei wird beim Empfänger per
  SHA-256 geprüft.
- **Phrase:** Mit Phrase wird die Datei mit AES-GCM verschlüsselt; Dateiname und Größe sind dann
  ebenfalls verborgen.

## Tipps & Grenzen

- Gekürzte Pakete erkennt der Empfänger und schlägt eine kleinere Paketgröße vor. Dann beim Sender
  neu vorbereiten – ein neuer Transfer ersetzt den angefangenen.
- Die Phrase bitte auf anderem Weg weitergeben.
- Prüfe, ob das Übertragen von Daten aus dem Cloud-PC in deiner Organisation erlaubt ist.
