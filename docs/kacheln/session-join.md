# An Sitzung teilnehmen

Mit einem Sitzungscode einer **Live-Sitzung** ODER eines **geteilten Dokuments über BDT Hub** beitreten –
ohne eigenes Projekt und ohne eigenes Konto. Jemand hat z. B. ein [Whiteboard](whiteboard-editor.md)
freigegeben oder dir ein Markdown-Dokument aus der [Wissensablage](info-explorer.md) geteilt und dir einen
Code wie `ABCD-EFGH-JKLM` genannt (oder einen QR-Code gezeigt); hier gibst du ihn ein.

## Voraussetzungen

- Die Adresse des BDT Hubs, auf dem die Freigabe läuft (nur die Server-URL, kein Zugang nötig) – du kannst
  sie direkt in der Kachel als „freien" Server hinterlegen.
- Der Sitzungscode bzw. die Meeting-ID, die dir der Koordinator mitgeteilt hat.
- Das Häkchen für BDT-Hub-Nutzung unter Einstellungen → „Erweiterte Verwendung".
- Für ein übernommenes Dokument zusätzlich: ein eigenes Projekt (unten in der Fußzeile wählbar).

## Typischer Ablauf

1. BDT-Hub-Server wählen oder über „+ Neuen Server hinzufügen" anlegen (nur URL).
2. Code eingeben, „Beitreten".
3. Je nach Art der Freigabe passiert Folgendes:
   - **Whiteboard** – du siehst das Whiteboard live, die Mauszeiger aller Teilnehmer sind sichtbar. Als
     *Visitor* schaust du zu, als *Editor* (wenn der Koordinator es erlaubt hat) zeichnest du mit.
     Vor dem Beitritt kannst du einen Anzeigenamen eingeben.
   - **Architektur-Studio** – du siehst das Sheet des Moderators nur lesend und folgst seinem
     Bildausschnitt; dein Mauszeiger ist für alle sichtbar. Ist die Ansicht nicht gesperrt,
     kannst du selbst schieben/zoomen und mit „Folgen" zurückkehren.
   - **XR-Raum/XR Meeting** – du wohnst der XR-Sitzung nur lesend bei (Karte „Meeting per Code beitreten").
   - **Geteiltes Dokument** – der Inhalt (Titel + gerendertes Markdown, inkl. eingebetteter Bilder) erscheint
     direkt auf dieser Seite; über „In Sammelkorb legen" oder „In Wissensablage übernehmen" landet es im
     unten gewählten Projekt.
4. Ist ein Warteraum aktiv (nur bei Live-Sitzungen), wartest du, bis der Koordinator dich zulässt.

## Funktionen im Detail

- Bei einer Live-Sitzung wird auf deinem Gerät **nichts gespeichert** – die Daten bleiben beim Koordinator,
  beim Schließen des Tabs ist alles weg. Ein übernommenes Dokument landet dagegen bewusst in deinem Projekt.
- Audio läuft nicht über BDT, sondern über euer Meeting (Teams/Zoom o. Ä.).
- Ob du bei einer Live-Sitzung eine Kopie exportieren darfst (Bild/Datei), entscheidet der Koordinator.
- Bei einem Dokument-Link steuert der Koordinator getrennt, ob du die Rohdatei (.md/.zip) herunterladen
  darfst – die Anzeige selbst ist immer möglich.

## Tipps & Grenzen

- Ohne BDT geht es auch: die Hub-Adresse gefolgt von `/session` im Browser öffnen und den Code dort eintippen
  (bei einem Dokument-Link zeigt die Hub-eigene Seite dort ebenfalls eine Vorschau + Downloadmöglichkeit).
- Bilder, die du als Whiteboard-Editor einfügst, erreichen die anderen Teilnehmer in dieser ersten Fassung
  noch nicht.
- Ein übernommenes Dokument wird ohne Dublettenprüfung importiert – ein zweiter Klick auf „Übernehmen" legt
  ein zweites Objekt an.
- Verwandt: [XR Meeting](xr-meeting.md) für den Beitritt mit eigenem Avatar und Projekt, [Wissensablage](info-explorer.md)
  für „Freigeben …" an einem eigenen Markdown-Dokument.
