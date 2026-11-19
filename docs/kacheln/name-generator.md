# Namensvorschläge

Schlägt mit KI passende Namen vor (z. B. für Felder, Objekte, Bausteine) – optional gegen ein
eigenes Regelwerk aus der Wissensablage geprüft, statt völlig freier Vorschläge.

## Voraussetzungen

- Ein eingerichteter KI-Anbieter.
- Für die Prüfung gegen ein eigenes Regelwerk: ein entsprechendes Infoobjekt in der
  Wissensablage.

## Typischer Ablauf

1. Beschreiben, wofür ein Name gebraucht wird.
2. Optional ein Regelwerk aus der Wissensablage auswählen (z. B. eine Namenskonvention).
3. Vorschläge durchsehen und übernehmen.

## Funktionen im Detail

- **Regelwerk (optional):** Markdown-Notizen aus der Wissensablage des aktuellen Projekts per
  Häkchen auswählen, mit Filter nach Namen. Die KI muss sie bei den Vorschlägen berücksichtigen.
- **Regelwerk-Profile:** eine Auswahl von Notizen als Profil speichern und später wieder anwenden.
- **Anzahl Vorschläge** einstellbar (Vorgabe 8); liefert die KI eine Begründung, steht sie unter dem Namen.
- **Aktionsleiste:** die nummerierte Liste als Text kopieren, herunterladen oder an den KI-Chat
  geben.
- **Anbieter-Hinweis oben:** Chromes lokale KI (Prompt API) oder ein konfigurierter KI-Anbieter.

## Tipps & Grenzen

- Ohne ausgewähltes Regelwerk schlägt die KI frei vor – für konsistente Namenskonventionen lohnt
  sich ein einmalig gepflegtes Regelwerk-Infoobjekt.
