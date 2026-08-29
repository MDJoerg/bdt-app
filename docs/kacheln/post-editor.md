# Post-Editor

Schreibt formatierte Posts für Social Media (zuerst LinkedIn). Anders als der
[Markdown-Editor](markdown-editor.md) gibt es hier kein Markdown – LinkedIn & Co.
können das nicht darstellen, wohl aber Unicode. „Fett"/„Kursiv"/… wandeln deshalb
jedes Zeichen der Auswahl direkt in ein passendes Unicode-Zeichen um; was du im
Feld siehst, ist bereits genau der Text, den du versendest.

## Voraussetzungen

- Ein Projekt.
- Kein SAP-Endpunkt nötig.

## Typischer Ablauf

1. „Neues Objekt" öffnet einen leeren Post.
2. Text schreiben, Auswahl markieren und über die Werkzeugleiste stylen.
3. Emojis über den Emoji-Picker einfügen (☆ am Emoji merkt es als Favorit).
4. Über die Aktionsleiste in die Zwischenablage kopieren und im Social-Tool einfügen.

## Funktionen im Detail

- 14 Unicode-Textstile (Fett, Kursiv, Fett Kursiv, Schreibschrift, Fett
  Schreibschrift, Fraktur, Fett Fraktur, Serifenlos in vier Varianten,
  Monospace, Doppelstrich, Eingekreist) – ein erneuter Klick auf einen anderen
  Stil ersetzt den vorherigen, statt ihn zu kombinieren.
- Unterstreichen/Durchgestrichen als echte Unicode-Textdekoration (kein CSS).
- Aufzählung, nummerierte Liste, Zitat, Trennlinie – als Zeichen-Präfix je
  Zeile, kein Markdown.
- Emoji-Picker mit Suche (auch nach Kategorie, z. B. „Flagge") und
  Favoriten-Ablage (☆) – derselbe Picker steht auch im Markdown-Editor zur
  Verfügung.

## Tipps & Grenzen

- Die Unicode-Textstile decken nur A–Z/a–z/0–9 ab – deutsche Sonderzeichen
  (ä/ö/ü/ß) sowie Satzzeichen bleiben unverändert stehen (das machen alle
  vergleichbaren Web-Tools genauso). Zusätzlich lesen Screenreader diese
  „Buchstaben" oft nicht als Wörter vor, da es technisch andere
  Unicode-Zeichen sind, keine gestylte Schrift.
- Ein Zeichenzähler mit plattformspezifischer Grenze sowie wiederverwendbare
  Post-Bausteine (Begrüßung/Signatur/Call-to-Action) sind vorgemerkt, aber
  noch nicht umgesetzt.
