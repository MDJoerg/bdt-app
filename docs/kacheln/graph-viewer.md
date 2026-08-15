# Graph-Viewer

Zeigt Graphdaten aus anderen Kacheln als Knoten-Kanten-Diagramm an und lässt dich darin
navigieren – z. B. einen Verwendungsnachweis, Asset-Beziehungen oder einen RAP-Schichten-Graphen
aus dem Clean Core Radar.

## Voraussetzungen

- Ein Projekt.
- Wird in aller Regel über „An Graph-Viewer übergeben" aus einer anderen Kachel heraus geöffnet,
  nicht direkt für sich allein genutzt.

## Typischer Ablauf

1. Aus einer anderen Kachel heraus einen Graphen an den Graph-Viewer übergeben (öffnet
   automatisch ein neues Tab).
2. Knoten anklicken für Details, hinein-/herauszoomen.
3. Zwischen kompakter und Präsentations-Darstellung wechseln.

## Funktionen im Detail

- Gruppiert bei Bedarf Knoten zu Clustern, statt bei sehr großen Graphen unübersichtlich zu
  werden.
- Kanten-Beschriftungen erscheinen erst ab einer bestimmten Zoomstufe, Knoten-Beschriftungen
  sind immer sichtbar.

## Tipps & Grenzen

- Der Graph-Viewer ist bewusst produzentenunabhängig – jede Kachel, die einen Graphen liefert,
  nutzt denselben Viewer, statt eine eigene Darstellung zu bauen.
