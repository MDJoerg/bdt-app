# Wordcloud-Editor

Sammelt Wörter, gewichtet sie nach Häufigkeit oder von Hand und ordnet sie als Wordcloud an –
z. B. für eine Schlagwort-Übersicht aus einem Workshop oder als Export aus wiederkehrenden
Meldungstexten der [Log Analyse](log-analysis.md).

## Voraussetzungen

- Ein Projekt.
- Kein SAP-Endpunkt nötig.

## Typischer Ablauf

1. „Neues Objekt" öffnet eine leere Wordcloud.
2. Wörter eingeben oder Text importieren (die Häufigkeit im Text bestimmt die Gewichtung).
3. Layout/Optik anpassen, ggf. Stoppwörter über ein gespeichertes Profil ausschließen.
4. Speichern.

## Funktionen im Detail

- Stoppwörter-Listen lassen sich als eigenes Profil sichern und wiederverwenden.
- Nimmt Text-Übergaben aus anderen Kacheln entgegen (z. B. aus der Meldungs-Analyse der
  [Log Analyse](log-analysis.md)) und tokenisiert sie automatisch.

## Tipps & Grenzen

- Wörter, die häufiger vorkommen, werden automatisch größer dargestellt – für eine bewusst
  gleichmäßige Darstellung trägst du die Gewichte stattdessen von Hand ein.
