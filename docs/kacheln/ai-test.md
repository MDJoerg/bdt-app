# KI-Testcenter

Misst die Zuverlässigkeit einer KI-Konfiguration: eine Erwartungshaltung wird mehrfach gegen
einen Agenten/Endpunkt oder direkt gegen einen MCP-Server getestet, mit Vergleichstabelle
(Laufzeiten, Werkzeugaufrufe) am Ende.

## Voraussetzungen

- Ein eingerichteter KI-Anbieter/Agent bzw. MCP-Server, den du testen möchtest.

## Typischer Ablauf

1. Test-Frage und erwartetes Ergebnis formulieren.
2. Ziel wählen: Agent/Endpunkt oder direkt ein MCP-Server.
3. Anzahl der Wiederholungen festlegen, Testlauf starten.
4. Vergleichstabelle durchsehen (Laufzeiten, tatsächlich aufgerufene Werkzeuge, Treffer/
   Fehltreffer).
5. Optional den Bericht in der Wissensablage aufheben.

## Funktionen im Detail

- Mehrfache Wiederholung deckt Schwankungen auf, die ein Einzeltest verbergen würde – gerade bei
  Werkzeugaufrufen ist das Verhalten nicht immer deterministisch.

## Tipps & Grenzen

- Ein Testlauf verbraucht reale KI-Anfragen (ggf. kostenpflichtig, je nach Anbieter) – wähle die
  Wiederholungszahl bewusst.
