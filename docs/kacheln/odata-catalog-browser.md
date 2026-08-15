# SAP OData Katalog Browser

Durchsucht den Service-Katalog deines SAP-Systems (V2 und V4) nach verfügbaren OData-Diensten –
bevor du weißt, WELCHER Dienst genau der richtige ist. Ein Treffer öffnet direkt im
[OData Browser](odata-browser.md).

## Voraussetzungen

- Ein eingerichteter SAP-Endpunkt.

## Typischer Ablauf

1. OData-Version wählen (V2 oder V4).
2. Suchbegriff eingeben (durchsucht wahlweise Titel/Beschreibung oder den technischen Namen
   getrennt).
3. Treffer über die Facetten eingrenzen (Typ, Freigabe, SAP-Standard, Paket,
   Anwendungskomponente).
4. Treffer öffnen → „In OData Browser öffnen" übernimmt den Service direkt.

## Funktionen im Detail

- Titel-/Beschreibungssuche und Suche im technischen Namen sind bewusst getrennt – so findest
  du gezielt eigene Z*-Entwicklungen, auch wenn SAP-Standardobjekte ähnlich benannt sind.
- Facetten sind rein clientseitig über die geladenen Treffer berechnet und zeigen live, wie
  viele Treffer je Wert übrig bleiben.

## Tipps & Grenzen

- Bei der V2-Katalogsuche ist die serverseitige Trefferzahl gedeckelt (sichtbar gekennzeichnet);
  V4 lädt den kompletten Katalog einmalig und filtert danach lokal.
- Rein lesend.
