# Melodie-Studio

Hilft beim Keyboard-Lernen mit Zahlen und Farben: Du beschreibst einmal, wie dein Keyboard beklebt
wird, tippst Lieder als Zahlenfolge ein, spielst sie ab und druckst Lernblätter. Gedacht für
Einsteiger, etwa Kinder, die nach Zahlen-Aufklebern spielen. Die Kachel ist experimentell.

## Voraussetzungen

- Ein Projekt. Keyboard-Profile und Lieder werden dort in der Wissensablage gespeichert.
- Kein SAP-Endpunkt nötig.
- „Aus Audio-Datei erkennen …“ läuft nur in der Webapp, der Desktop-App und VS Code, nicht in der
  Chrome-Erweiterung.

## Typischer Ablauf

1. Auf der Startseite die Kachel **Mein Keyboard** öffnen und **Neues Profil** anlegen: Name,
   Tastatur-Vorlage, Nummernschema, Farben und den beklebten Bereich wählen, dann **Speichern**.
2. Über **Drucken** „Mein Keyboard“, die „Aufkleber-Vorlage“ oder „Musik verstehen“ ausgeben und
   das Keyboard bekleben.
3. Ein neues Lied anlegen, z. B. über **Komponieren** (leer beginnen).
4. Im Reiter „Abspielen“ das Keyboard-Profil wählen, eine Zahlenfolge eintippen und **Anhängen**
   klicken – oder direkt auf die Tasten der Klaviatur klicken.
5. **Abspielen** – die Vorschau zeigt die kommenden Tasten.
6. Im Reiter „Ausdrucken“ Ausrichtung und Inhalte wählen und **Liedblatt drucken**.

## Funktionen im Detail

- **Nummernschema:** „12 je Oktave (empfohlen)“, „Weiße Tasten 1–7 je Oktave
  (Social-Media-Standard)“, „Fortlaufend über alle weißen Tasten“ oder „1–9, dann A–B–C je Oktave
  (Papier-Vorlage)“. Farben als 7 Regenbogenfarben, 12 Farben oder keine; einzelne Töne lassen sich
  einzeln einfärben. Dazu Tonnamen (Deutsch H / Englisch B), Oktav-Kennzeichnung und
  Aufkleber-Größe in mm.
- **Eingabe:** Zahlenfolge mit wählbarem Eingabe-Schema und Notenwert, „Pause einfügen“, Klick auf
  die Klaviatur oder die PC-Tastatur (Tasten `A W S E D F T G Y H U J K O L P ;`, wenn das Feld
  fokussiert ist).
- **Schritte:** Jeder Schritt lässt sich verschieben, löschen und mit einem Liedtext versehen;
  „+“ fügt danach eine Note ein. Wiederholungen („×N“) legst du über „Von Schritt“, „Bis Schritt“
  und „Anzahl“ an.
- **Abspielen:** Tempo (BPM), Transposition um −12/−1/+1/+12 Halbtöne, „Auf beklebten Bereich
  einpassen“, Metronom und Taktlinien in der Vorschau.
- **Lieder anlegen:** „Lied laden“ (JSON-Datei), „Aus MIDI-Datei“ (Assistent: Stimme wählen,
  Abschnitt festlegen, in Notenwerte umwandeln), „Aus Audio-Datei“ (Handy-Aufnahme oder Video,
  Ausschnitt wählen, Melodie automatisch erkennen) und „Komponieren“.
- **Liedtext erkennen:** Im Audio-Assistenten optional mit der lokalen Spracherkennung „Whisper“.
- **Meine Lieder:** Suche, Ordner anlegen/umbenennen/löschen, Lied verschieben oder löschen,
  Export der sichtbaren Liste als JSON (Austauschformat) über die Aktionsleiste.
- **Liedblatt:** Querformat oder Hochformat, „Takte je Zeile“, wahlweise Notennamen, Farbe,
  Notensymbol, Liedtext und Zeitmarken je Zeile. Die Zahl auf dem Aufkleber bleibt immer stehen.

## Tipps & Grenzen

- Die automatische Erkennung aus Audio liefert nur einen Vorschlag – prüfe und korrigiere die
  Schritte danach.
- Die Liedtext-Erkennung lädt beim ersten Mal ein größeres Sprachmodell herunter.
- Ohne Keyboard-Profil nutzt ein Lied das Standardschema (12 je Oktave). Für das Liedblatt lohnt
  sich ein eigenes Profil.
- Die Zeitmarken auf dem Liedblatt sind aus Tempo und Notenwerten geschätzt; Wiederholungen zählen
  dabei nur einmal.
- Die Übungs-Eignung in der Liederliste ist eine Heuristik, keine musikalische Bewertung.
