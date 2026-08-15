# Daten-Studio

Übernimmt tabellarische Daten (aus [Data Preview](data-preview.md), dem
[OData Browser](odata-browser.md), Dateien, der Zwischenablage oder einem LeanIX-Import) und
lässt dich Felder klassifizieren, profilieren, in Charts/Kreuztabellen auswerten und in Segmente
aufteilen.

## Voraussetzungen

- Ein Projekt.
- Kein SAP-Endpunkt zwingend nötig – nur, wenn du Daten direkt aus einem OData-Dienst
  registrierst.

## Typischer Ablauf

1. Datensatz übernehmen (aus einer anderen Kachel, per Datei-Upload oder Zwischenablage).
2. Felder klassifizieren (Dimension, Zeit, Kennzahl, Text, …) – Voraussetzung für sinnvolle
   Charts/Auswertungen.
3. Profil eines Feldes ansehen (Datenqualität, häufigste Werte, Verteilung).
4. Auswerten: Charts, Kreuztabelle (OLAP), Segmente, Graph-Ansicht.
5. Ergebnis in Assets übernehmen oder weiterreichen.

## Funktionen im Detail

- **Abgeleitete Spalten:** aus vorhandenen Feldern berechnete neue Spalten (z. B. Wochentag aus
  einem Datum).
- **Daten-Navigator:** verknüpft mehrere Datasets über gemeinsame Schlüssel und lässt dich per
  Klick durch die Beziehung navigieren.
- **Segmente:** Filter-Ausschnitte eines Datasets, auch über Mengenoperationen (Vereinigung/
  Schnitt/Differenz) miteinander kombinierbar.
- **LeanIX-Import-Wizard:** übernimmt ein EA-Repository-Exportformat direkt als Datensatz.

## Tipps & Grenzen

- Für komplexere, wiederverwendbare Datenmengen-Logik (z. B. „Kunden mit UND ohne
  Ansprechpartner") ist das [Segmentierungs-Studio](segmentation-studio.md) oft der
  übersichtlichere Weg.
