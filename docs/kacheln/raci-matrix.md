# RACI-Matrix

Hier hältst du fest, **wer an welchem Use Case beteiligt ist**: Zeilen sind die Use Cases,
Spalten die Rollen, in jeder Zelle stehen die Buchstaben **R** (verantwortlich), **A**
(rechenschaftspflichtig), **C** (konsultiert) und **I** (informiert). Die Daten sind ganz
normale Assets und Beziehungen – du siehst sie auch im Asset-Explorer, im Graph und in der
Beziehungs-Verwaltung.

## Voraussetzungen

- Ein Projekt und ein Universum (beides unten in der Fußzeile).
- Am einfachsten: in den Einstellungen → Assets „Universum aus Vorlage …“ mit der Vorlage
  „Ist-Analyse“. Sie bringt Rollen, Use Cases, Prozesse, Organisationseinheiten und die
  Beziehungstypen R/A/C/I sowie „gehört zu“ mit.
- Kein SAP-Endpunkt nötig, läuft in allen Targets.

## Typischer Ablauf

1. Use Cases und Rollen anlegen (Asset-Verwaltung oder Asset-Explorer).
2. Optional gruppieren: Use Case „gehört zu“ Prozess, Prozess „gehört zu“ Prozessbereich,
   Rolle „gehört zu“ Organisationseinheit.
3. RACI-Matrix öffnen, oben in der Werkzeugleiste einen Buchstaben wählen und auf die
   passenden Zellen klicken. Ein zweiter Klick nimmt den Buchstaben wieder weg. Gespeichert
   wird sofort.
4. Hinweise prüfen: Zeilen mit ⚠ haben kein A, mehrere A oder kein R.

## Funktionen im Detail

- **Gruppen**: Prozessbereiche/Prozesse in den Zeilen, Organisationseinheiten in den
  Spalten, beliebig tief. ▾/▸ klappt eine Gruppe auf oder zu; zugeklappt zeigt die Zelle die
  Summe, z. B. „2×R A“.
- **Filter**: je eine Gruppe für Zeilen und Spalten, Suche über Use-Case- und Gruppentitel,
  „Nur Zeilen mit Hinweisen“.
- **Sichten**: oben wählst du „RACI“, „Systemunterstützung“, „Werkzeugkoffer“, „Datenhoheit“ oder „Frei“. Jede Sicht merkt
  sich ihre Einstellung je Universum.
- **Systemunterstützung**: Use Cases × Funktionen, die Spalten gruppiert nach System →
  Modul. Mit „U“ setzt ein Klick „unterstützt“. Markiert werden Use Cases ohne Funktion
  (Lücke) und Funktionen ohne Use Case. Use Cases mit Funktionen aus mehreren Systemen
  bekommen kein Warnsymbol, sondern „⇄“ mit der Anzahl der Systeme: systemübergreifende
  Use Cases sind erwünscht (z. B. orchestriert durch eine KI über MCP), verdienen aus
  Architektursicht aber einen genauen Blick. „Nur systemübergreifende Use Cases“ filtert sie.
- **Werkzeugkoffer**: wie „Systemunterstützung“, aber die Zelle zeigt den Schritt im Ablauf
  (1, 2, 3 …). Mit „Schritt“ setzt ein Klick auf eine belegte Zelle die Nummer. Unter der
  Matrix stehen die Abläufe je Use Case („1 Bestand prüfen ⇄ 2 Lagerauftrag einreichen“, ⇄ =
  Wechsel in ein anderes System) und wie oft jedes Werkzeug genutzt wird. Beides lässt sich als
  Markdown kopieren oder herunterladen, z. B. für eine Folie. Die Nummer ist das Attribut
  „Schritt“ an der Beziehung „unterstützt“; ältere Universen bekommen es über Einstellungen →
  Assets → „Universum aus Vorlage …“ ins selbe Universum.
- **Priorisierung …** (in jeder Sicht): je Use Case Wünschbarkeit, Machbarkeit, Lebensfähigkeit
  und Nachhaltigkeit von 1 bis 5 und die gesparten Minuten pro Tag. Ein Blasen-Chart zeigt
  Machbarkeit gegen Nutzen, die Größe sind die Minuten, ein grüner Rand heißt nachhaltig.
  „Sweet Spot“ sind Use Cases mit Wünschbarkeit, Machbarkeit und Lebensfähigkeit je mindestens 4.
  Trägst du die Überstunden pro Tag ein, siehst du, wie viel davon Sweet Spot und Quick Wins
  abdecken. Die Werte stehen am Use Case; fehlen die Felder in einem älteren Universum, ergänzt
  sie Einstellungen → Assets → „Universum aus Vorlage …“. Ergebnis als Markdown kopierbar.
- **Tools aus Dialog ernten …** (in „Systemunterstützung“ und „Werkzeugkoffer“): du gibst einen
  Rollenspiel-Dialog zwischen Anwender und KI-Assistent ein oder übernimmst die Sprechblasen
  einer Story. Die KI (oder eine externe KI über „Prompt kopieren“) schlägt je Systemzugriff ein
  Werkzeug vor: Name, Parameter, System, Backend-Funktion, Beispielergebnis. Du hakst an, ordnest
  bei Bedarf das System zu und legst die Werkzeuge an – als Funktionen „MCP-Tool“ unter
  „<System> MCP“ mit Schritt 1, 2, 3 am gewählten Use Case und/oder als Entwurf im MCP Simulator,
  der sofort mit den Beispielergebnissen antwortet.
- **Datenhoheit**: Geschäftsobjekte (je Asset-Typ eine Gruppe, z. B. Kunde, Auftrag) ×
  Systeme. „F“ heißt: dieses System führt das Objekt (Schlüssel und Kernattribute), „E“: es
  ergänzt eine Datensicht. Markiert werden Objekte ohne führendes System, Konflikte (zwei
  führende Systeme) und Ergänzungen, für die kein Datenmodell mit diesem System als Quelle
  existiert („Beschreibt die Datensicht von“ in „Semantische Typen & Datenmodelle“). Der
  Tooltip einer Zeile nennt „führt: … · ergänzt: …“.
- **Use-Case-Steckbrief**: Klick auf den Namen eines Use Case (oder auf ⇄) öffnet rechts
  seinen Steckbrief – Systeme mit den unterstützenden Funktionen, Orchestrierung,
  gelesene/geschriebene Geschäftsobjekte mit führendem System und die Rollen mit ihrer
  Organisationseinheit. Oben stehen Architektur-Hinweise: Daten mit fremder Hoheit schreiben,
  Objekt ohne führendes System, R und A aus verschiedenen Organisationseinheiten,
  systemübergreifend ohne Orchestrierung. Die Orchestrierung (System oder Agent mit Art)
  trägst du direkt dort ein; der Steckbrief lässt sich als Markdown kopieren.
  „Agenten-Entwurf …" macht daraus einen KI-Chat-Agenten: System-Prompt aus dem Use Case,
  dazu vorgeschlagene MCP-Werkzeuge (das Asset-Universum und Server, deren Name zu einem
  beteiligten System oder Modul passt). Nach dem Speichern öffnet „Im KI-Chat öffnen" den
  Chat mit diesem Agenten.
- **Frei konfigurierbar**: in der Sicht „Frei“ sind Zeilen- und Spaltentyp sowie die
  Beziehungstypen wählbar – die Matrix funktioniert für jeden Beziehungstyp zwischen zwei
  Asset-Typen.
- **Kontext**: Beziehungen mit Kontext (z. B. je Projekt) lassen sich getrennt anzeigen.
- **Export**: Kopieren, CSV/Excel/Markdown, E-Mail, Sammelkorb; „Graph“ öffnet die
  Beziehungen im Graph-Viewer, „Daten-Studio“ übernimmt die Matrix als Datensatz.

## Tipps & Grenzen

- Die Prüfregeln sind Hinweise, nichts wird gesperrt.
- Gruppen entstehen nur aus Beziehungstypen mit dem Häkchen „Strukturbeziehung“ (Kachel
  „Beziehungen“). Gehört ein Use Case zu zwei Prozessen, erscheint er unter dem ersten mit
  einem Hinweis.
- In einem Template-Projekt (nur lesen) kannst du die Matrix ansehen, aber nicht ändern.
