# ABAP Unit Cockpit

Führt die ABAP-Unit-Tests von Paketen, Klassen oder Programmen im gewählten SAP-System aus –
über dieselbe ADT-Schnittstelle, die auch Eclipse nutzt – und wertet das Ergebnis aus: eine
Übersicht mit Grafiken, die Liste aller Testmethoden, einen Explorer-Baum und je Testmethode ein
Detail mit Meldung, Aufrufstack, ADT-Link und Quelltext an der Fundstelle.

## Voraussetzungen

- Ein eingerichteter SAP-Endpunkt (ADT).
- Getestet werden können nur **eigene Objekte** (Z*/Y* bzw. eigene, registrierte Namensräume).
  Auf Kundensystemen schließt ABAP Unit SAP-Standard und Demo-Inhalte (/DMO/) stillschweigend aus.

## Typischer Ablauf

1. Endpunkt in der Fußzeile wählen.
2. Im Feld **Umfang** je Zeile ein Paket eintragen (z. B. `ZMEIN_PAKET`) – oder mit Präfix eine
   Klasse (`KLASSE:ZCL_MEINE_KLASSE`), ein Programm (`PROG:ZREPORT`) bzw. eine Funktionsgruppe
   (`FUGR:ZFG`). Die Suchhilfe neben dem Feld findet Objekte und fügt sie per Klick hinzu.
3. Testdauern wählen (Standard: kurz und mittel) und **Tests ausführen** klicken.
4. **Übersicht:** Ergebnis-Donut, Ergebnis je Programm, langsamste Testmethoden.
5. **Tests:** alle Testmethoden als Tabelle (filter-, sortier- und exportierbar), optional nur die
   nicht erfolgreichen. Klick auf eine Zeile öffnet das Detail.
6. **Detail:** Meldung, Detailtexte (z. B. „Expected [2] Actual [1]"), Aufrufstack, „In ADT öffnen"
   und „Quelltext an der Fundstelle laden" (Ausschnitt mit markierter Zeile).

## Funktionen im Detail

- **Sicherheit:** Ein Testlauf führt Testcode im System aus. Deshalb laufen hier nur Testklassen
  mit der Risikostufe **HARMLESS** – DANGEROUS und CRITICAL werden nie ausgeführt und erscheinen
  auch nicht im Ergebnis.
- **Unterpakete** werden bei Paket-Läufen immer mit einbezogen. Im Paket `$TMP` berücksichtigt das
  System nur Objekte des angemeldeten Benutzers.
- **Leeres Ergebnis:** Wurde keine Testmethode ausgeführt, erklärt die Kachel die möglichen Gründe,
  statt „alles grün" anzuzeigen.
- **Ergebnisarten:** Erfolgreich, Fehlgeschlagen (Assertion), Ausnahme (z. B. Division durch null),
  Warnung (tolerierbare Meldung).
- **Explorer:** Baum nach Programm → Testklasse → Methode oder nach Ergebnis → Programm, je Knoten
  eine gefilterte Testtabelle.
- **Prüfprofile:** merken sich Umfang, Testdauern und das Häkchen „Läufe automatisch aufheben".
- **Lauf aufheben:** speichert einen kompakten Ergebnis-Snapshot in der Wissensablage (über
  „Dashboard anzeigen" read-only wieder zu öffnen).
- **Verlauf:** zeigt alle aufgehobenen Läufe mit gleichem Umfang und gleichen Testdauern als
  Diagramm (Ergebnisse gestapelt, Erfolgsquote als Linie). Der aktuelle, noch nicht aufgehobene
  Lauf zählt mit. Darunter stehen die **instabilen Tests** – Testmethoden, die mal erfolgreich und
  mal nicht erfolgreich waren, mit ihrer Ergebnisfolge (✓ ✗). In der Tabelle „Tests" sind sie mit
  „instabil" markiert.
- **Test-Gap-Radar:** zählt je Paket (inkl. Unterpakete) die Klassen, ausführbaren Programme und
  Funktionsgruppen mit und ohne Testklasse – **ohne einen Test auszuführen**. Berücksichtigt werden
  alle Risikostufen; wie viele Testklassen nicht HARMLESS sind (und deshalb hier nie laufen), steht
  in einer eigenen Kennzahl. Diagramm „mit/ohne Tests je Paket", Tabelle mit Filter „Nur ohne Tests"
  und Export. Klick auf ein Objekt mit Tests übernimmt es in den Umfang.
- **Mit KI erklären:** im Detail einer Testmethode schickt der Knopf Meldung, Aufrufstack und den
  Quelltext um die Fundstelle an den KI-Chat.
- **Arbeitsauftrag (Markdown):** im Reiter „Tests" werden die fehlgeschlagenen Tests deiner Auswahl
  (oder der gefilterten Zeilen) als Taskliste je Programm aufbereitet – zum Kopieren in eine
  KI-Coding-Sitzung oder direkt an den KI-Chat.
- **Kanban-Backlog:** legt je fehlgeschlagener Testmethode eine Karte in der Wissensablage an.
  „Backlog-Taxonomie einrichten" erzeugt die Spalten Neu, In Analyse, In Korrektur und Erledigt
  fürs Kanban-Board. Bestehende Karten werden erkannt und nur geöffnet.
- **Testklasse vorschlagen:** im Test-Gap-Radar gibt es für Klassen und Programme ohne Tests den
  Knopf „Vorschlag". Er lädt den Quelltext, liest die öffentlichen Methoden und bereitet einen
  Prompt für ein Testklassen-Skelett auf.
- **Coverage:** mit dem Häkchen „Coverage messen" misst der Lauf mit, welche Anweisungen, Zweige und
  Methoden die Tests durchlaufen haben. Der Reiter „Coverage" zeigt die Abdeckung je Programm, Klasse
  und Methode. Ein Klick auf eine Zeile färbt den Quelltext ein: grün ausgeführt, rot nicht
  ausgeführt, orange nur teilweise (z. B. eine IF-Bedingung, bei der nur ein Zweig genommen wurde).

## Tipps & Grenzen

- Der Lauf ist synchron – bei großen Paketen mit vielen Tests kann die Antwort dauern. Zum Start
  lieber ein einzelnes Paket oder eine Klasse wählen.
- Für den ADT-Link braucht der Endpunkt eine Systemkennung und lokal ein Eclipse mit passender
  ABAP-Projekt-Verbindung.
- Für Verlauf und instabile Tests braucht es mindestens zwei Läufe mit gleichem Umfang – am
  einfachsten über ein Prüfprofil mit „Läufe automatisch aufheben".
- Im Test-Gap-Radar erscheinen Objekte aus SAP-Standard oder fremden Namensräumen immer als „ohne
  Tests" (ABAP Unit meldet deren Testklassen auf Kundensystemen nicht). In `$TMP` gilt das auch für
  Objekte anderer Benutzer.
- Die KI-Hilfen schreiben nie ins System: ein vorgeschlagenes Testklassen-Skelett übernimmst du
  selbst in Eclipse/ADT. Für Funktionsgruppen gibt es noch keinen Vorschlag.
- Den eingefärbten Quelltext gibt es nur direkt nach einem Lauf. Ein aufgehobener Lauf zeigt die
  Coverage-Kennzahlen und die Tabelle.
- Die Coverage gilt je Programm/Klasse – eine Auswertung je Paket gibt es nicht, weil das System die
  Paketzuordnung im Ergebnis nicht mitliefert.
- Ohne SAP-System: Das abapGit Studio zeigt für ein heruntergeladenes Archiv die Test-Quote im
  Paket-Dashboard und je Objekt in der Stückliste, ob Testklassen enthalten sind.
