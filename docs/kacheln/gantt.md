# Gantt

Zeigt den Zeitplan der Vorgänge – Aufgaben, Projekte, Termine – als Balkendiagramm, mit
Klammer (Projekt enthält Aufgaben) und Abhängigkeiten zwischen den Vorgängen.

## Voraussetzungen

- Ein Projekt mit einem Asset-Universum, in dem die Vorlage „Vorgänge“ angewendet wurde
  (Einstellungen › Assets › Universum aus Vorlage). Sie liefert Aufgabe, Projekt, Termin,
  Ereignis und die Beziehungen „enthält“, „Vorgänger von“ und „betrifft“.
- Kein SAP-Endpunkt nötig.

## Typischer Ablauf

1. Projekt und Universum in der Fußzeile wählen.
2. Im [Asset-Explorer](asset-explorer.md) Aufgaben mit Plan-Start und Plan-Ende pflegen.
3. Das Gantt zeigt sie sofort; „Neu laden“ holt Änderungen nach.

## Funktionen im Detail

- **Balken:** Plan als Balken, Ist-Zeitraum als dünner orangefarbener Strich darunter, ein
  Vorgang ohne Dauer als Raute. Die rote gestrichelte Linie ist der heutige Tag.
- **Klammer:** Beziehungen „enthält“ ordnen Vorgänge unter ein Projekt. Hat das Projekt keinen
  eigenen Zeitplan, zeigt das Gantt die Summe seiner Teile. ▾/▸ klappt auf und zu.
- **Abhängigkeiten:** Pfeile für „Vorgänger von“. Art (Ende→Start, Start→Start, Ende→Ende,
  Start→Ende) und Versatz stehen an der Beziehung; rot ist eine unterschrittene Bedingung.
- **Hinweise (⚠):** Ende vor Start, unterschrittene Abhängigkeit, Zyklus, Plan-Ende überschritten
  ohne Ist-Ende. Sie sperren nichts.
- **Filter:** Typ, Suche, „Nur Zeilen mit Hinweisen“; Zeitskala automatisch oder Tage/Wochen/Monate.
- **Export:** Tabelle (CSV, Markdown u. a.) über die Aktionsleiste.
- **Aufgabe anlegen:** im Asset-Explorer am Objekt („Aufgabe anlegen“ in der Objektseite) – legt
  eine Aufgabe mit der Beziehung „betrifft“ auf das Objekt an.

## Tipps & Grenzen

- Das Gantt ist eine Sicht und ändert den Zeitplan nicht. Termine verschiebst du am Objekt.
- Der Versatz muss in Tagen, Stunden oder Minuten stehen (z. B. P2D); Monate haben keine feste Länge.
- Der Zeitregler im Architektur-Studio liest weiter den Lebenszyklus der Assets, nicht diesen Zeitplan.
