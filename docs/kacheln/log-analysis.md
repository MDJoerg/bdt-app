# Log Analyse

Liest klassische Application Logs (SLG1) über den SAP-Standarddienst aus – kein eigener
Z-Baustein im System nötig. Zeigt eine Übersicht mit Diagrammen, eine durchsuchbare Logs-
Tabelle, eine Meldungs-Analyse (wiederkehrende Meldungstexte) und einen Explorer.

## Voraussetzungen

- Ein eingerichteter SAP-Endpunkt mit aktiviertem Standarddienst `APL_LOG_MANAGEMENT_SRV`.

## Typischer Ablauf

1. Zeitraum wählen (Standard: letzte 24 Stunden), optional Severity/Objekt/Subobjekt/Benutzer/
   externe Referenz einschränken (Suchhilfe verfügbar).
2. Suchen.
3. Im Reiter „Übersicht" die Diagramme sichten (Severity, Zeitverlauf, Objekt, Heatmap, Trend).
4. Im Reiter „Logs" einzelne Meldungen mit Detailansicht durchsehen.
5. Im Reiter „Meldungs-Analyse" wiederkehrende Meldungstexte gruppiert sehen, optional als
   Wordcloud exportieren.
6. Optional „Lauf aufheben" speichert den kompletten Stand als Infoobjekt in deiner
   Wissensablage.

## Funktionen im Detail

- Der Explorer bietet drei Perspektiven zum Durchklicken der Logs.
- Die Meldungs-Analyse gruppiert nach Meldungstext, nicht nach SAP-Message-Class/-Nummer – dieser
  Dienst kennt beides nicht.

## Tipps & Grenzen

- Rein lesend.
- Eine vergleichbare Kachel für Hintergrund-Jobs (SM37) gibt es aktuell nicht – der dafür
  passende SAP-Standarddienst deckt nur einen Teil der klassischen Job-Arten ab.
