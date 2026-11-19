# Customizing-Spike

Wegwerf-Kachel für den geplanten Customizing-Extraktor. Sie beantwortet die Recherche-Aufgaben
R1–R7 aus dem Konzept automatisch gegen ein echtes SAP-System und erzeugt einen Bericht. Die Kachel
liest nur. Nach dem Spike wird sie wieder ausgebaut.

Nur im Expertenmodus sichtbar (Gruppe „Sonstige Werkzeuge“).

## Voraussetzungen

- Ein SAP-Endpunkt mit ADT (Freestyle-SQL wie in Data Preview), unten in der Fußzeile gewählt.
- Leserechte auf die abgefragten Tabellen. Fehlende Rechte erscheinen als Fehler je Abfrage, der
  Rest läuft weiter.
- ABAP Cloud ist ungeeignet: dort sind Systemtabellen per SQL gesperrt.

## Typischer Ablauf

1. Bereiche wählen (R7 System, R1 Zugriffsweg, R2 Tabellen, R3 CDS-Views, R4 Vorlagen, R6
   Transport-Spur). Optional **Nutzung zählen** (Belege je Verkaufsorganisation, Belegart,
   Bestellart).
2. **Proben ausführen**. Die Kachel zeigt den Fortschritt je Abfrage.
3. Optional R5: ein kopiertes SE16N-ALV und ein Ergebnis der Eclipse-SQL-Konsole einfügen. Geprüft
   werden nur Spaltenköpfe, Zeilenzahl und Zahlenformat.
4. Bericht prüfen und als **Markdown** oder **JSON** herunterladen oder kopieren.

Ohne Systemzugang liefert **Anweisungen für die SQL-Konsole** dieselben Abfragen als Markdown für
Eclipse.

## Was steht im Bericht?

- Standard: nur Metadaten und Zahlen (Systemart, Release, Mandantenrollen, lesbare Tabellen,
  Schlüsselfelder, Zeilenzahlen, CDS-Freigabe, Anzahl Organisationseinheiten, Treffer in den
  SAP-Referenzlisten, Zuordnungen, Transport-Spur).
- SAP-eigene Referenzschlüssel (z. B. Buchungskreis 1010/1710, Belegart TA) werden immer genannt.
- Schlüssel und Texte aus dem Kundensystem (eigene Buchungskreise, Werksnamen …) erscheinen nur,
  wenn **Schlüssel und Texte aufnehmen** gesetzt ist.

## Tipps & Grenzen

- Jede Abfrage ist höchstens 255 Zeichen lang; lange Listen werden auf mehrere Abfragen verteilt.
- „Nutzung zählen“ liest Bewegungsdaten (VBAK, EKKO) und kann in großen Systemen dauern.
- Nichts wird gespeichert; der Bericht bleibt im Browser, bis du ihn herunterlädst.
