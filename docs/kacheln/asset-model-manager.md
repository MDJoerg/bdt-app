# Semantische Typen & Datenmodelle

Pflegt die Bausteine, aus denen sich Asset-Typen zusammensetzen: Concept Descriptions
(semantische Typen, z. B. „Temperatur" oder „Seriennummer" mit einer eindeutigen Bedeutung) und
Submodel-Templates (wiederverwendbare Feldgruppen).

## Voraussetzungen

- Ein Projekt.
- Kein SAP-Endpunkt nötig.

## Typischer Ablauf

1. Semantischen Typ anlegen (Bezeichnung, Datentyp, Einheit).
2. Submodel-Template aus mehreren semantischen Typen zusammenstellen.
3. Das Template in der [Asset-Verwaltung](asset-manager.md) einem Asset-Typ zuordnen.

## Funktionen im Detail

- Semantische Typen sind wiederverwendbar über mehrere Asset-Typen/Universen hinweg – einmal
  „Seriennummer" definiert, überall gleich verwendbar.
- **Beschreibt die Datensicht von**: im Datenmodell-Editor hältst du fest, welches System dieses
  Datenmodell beiträgt – etwa „CRM" für die Vertriebsdaten zum Kunden, während ein anderes System
  den Kunden führt. Angeboten werden Systeme und Agenten (Beziehungstypen „führt", „ergänzt",
  „orchestriert" der Vorlage „Ist-Analyse"). Leer heißt systemneutral; die Angabe wirkt sofort.

## Vorlage „Vorgänge“ und eigener Namensraum

In Einstellungen → Assets legt „Universum aus Vorlage“ die Vorlage **Vorgänge** an: Aufgabe, Projekt, Termin, Ereignis und Person mit Zeitplan (Plan-/Ist-Start und -Ende), Status als Aufzählung und den Beziehungstypen „Vorgänger von“ (mit Abhängigkeitsart FS/SS/FF/SF und Versatz), „angefordert von“, „zuständig für“, „zugewiesen an“ und „enthält“. Die dabei angelegten **Begriffe** (semantische Typen) siehst du hier im Modell-Manager.

Weitere Vorlagen derselben Art: **Projektleiter** (Phase, Meilenstein, Risiko), **Servicetechniker** (Kunde, Gerät, Servicefall, Ersatzteil) und drei Sichten auf die Landschaft – **Anwendungen und Datenflüsse**, **Fachlichkeit** (Fähigkeiten, Prozesse) und **Technologie** (Komponenten, Plattformen). Eine Vorlage kann andere verlangen (Projektleiter und Servicetechniker verlangen „Vorgänge“, Fachlichkeit und Technologie verlangen „Anwendungen“): Der Dialog legt die verlangten Vorlagen mit an, ins selbe Universum. Gemeinsame Typen wie Aufgabe oder Anwendung entstehen dabei nur einmal.

Die semanticId eines eigenen Begriffs setzt sich aus einer Basis-Adresse, einem Pfad und einer Version zusammen. Die Basis steht in Einstellungen → Assets → „Namensraum für eigene Begriffe“ (Vorgabe `https://objid.info/`). Ändern gilt für neu angelegte Begriffe und für den nächsten Export zu BaSyx; bereits angelegte Begriffe behalten ihre semanticId.

## Profil: Teilmodelle automatisch anlegen, Pflicht-Beziehungen

Bei den Zuordnungen eines Datenmodells gibt es je Asset-Typ den Haken **„Teilmodelle bei neuen Instanzen automatisch anlegen“**. Ist er gesetzt, bekommt jede neu angelegte Instanz dieses Typs (Asset-Verwaltung, Asset-Explorer) ihre Teilmodelle sofort, leer ausgeprägt – das Feld „Titel“ trägt den Titel der Instanz. Die Vorlage **Vorgänge** setzt den Haken für alle ihre Typen. Bestehende Instanzen ändern sich nicht.

Zusätzlich kann ein Asset-Typ **Pflicht-Beziehungen** tragen (im Modell-Manager unter „Pflicht-Beziehungen“ je zugeordnetem Typ ankreuzbar) (die Vorlage Vorgänge verlangt bei „Aufgabe“ die Beziehung „zugewiesen an“). Fehlt sie, meldet die Konsistenzprüfung in Einstellungen → Assets einen Hinweis; automatisch repariert wird nichts.

## Tipps & Grenzen

- Eine Änderung an einem bereits genutzten Datenmodell wirkt sich auf alle Asset-Typen aus, die
  es verwenden – prüfe vorher, wo es schon im Einsatz ist.
