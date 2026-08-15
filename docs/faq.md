# Häufige Fragen (FAQ)

**Ist BDT kostenlos?**
Ja. Die aktuellen Werkzeuge sind kostenlos nutzbar. Einzelne künftige Kacheln könnten als
kostenpflichtige Zusatzangebote markiert werden (`paid`) – das betrifft aktuell keine Kachel und
wird, falls es so weit kommt, klar gekennzeichnet.

**Brauche ich ein SAP-System, um BDT zu nutzen?**
Nein. Viele Kacheln – Wissensablage, Kreativ-Editoren (Whiteboard, Markdown, Mermaid, …),
Daten-Studio ohne OData-Anbindung, XR-Raum – funktionieren komplett ohne Endpunkt. Nur Kacheln,
die ausdrücklich mit einem SAP-System sprechen (Repository-Suche, CDS Explorer, Data Preview, …),
brauchen einen eingerichteten Endpunkt.

**Wo werden meine Daten gespeichert?**
Lokal – im Browser bzw. auf deinem Rechner (localStorage/IndexedDB), projektweise getrennt.
Nichts verlässt dein Gerät, außer du richtest selbst eine Synchronisierung ein (z. B. BDT Hub) oder
rufst aktiv einen Endpunkt auf. Details: [BDT Hub](experten/bdt-hub.md).

**Sendet BDT irgendwelche Daten an einen Server von Brandeis Consulting oder Dritte?**
Nein. BDT ruft nur Systeme auf, die du selbst als Endpunkt konfiguriert hast, und nur wenn du
eine Aktion auslöst (z. B. „Suchen" klicken). Es gibt keine Telemetrie und keine automatischen
Hintergrundaufrufe an fremde Server.

**Was ist der Unterschied zwischen Chrome-Erweiterung, VS-Code-Erweiterung, Desktop-App und
Web-App?**
Funktional sind sie fast identisch – der Unterschied liegt vor allem darin, wie BDT mit deinem
SAP-System spricht (direkter Browser-Zugriff vs. über eine „Local Bridge", die CORS-Beschränkungen
und Windows-Anmeldung löst). Details: [Deployment-Varianten](experten/deployment.md).

**Was bedeutet „Erweiterte Verwendung"?**
Ein paar Funktionen laden Inhalte von einer externen Quelle nach (z. B. ein eingebetteter
Diagramm-Editor oder der Import fremder 3D-Modelle). Das ist standardmäßig deaktiviert; du
schaltest es bewusst frei, bevor du eine solche Funktion zum ersten Mal nutzt.

**Warum sehe ich nicht alle Kacheln im Launchpad?**
BDT startet mit dem Sichtbarkeits-Regler auf „Fokus" – einer kleinen, kuratierten Auswahl. Unter
Einstellungen → „Launchpad-Gruppen" kannst du auf „Standard" oder „Experte" hochstellen. Details:
[Tipps](einstieg/tipps.md).

**Wie sichere ich meine Daten?**
Automatische lokale Snapshots, ein vollständiger Projekt-Export als Datei, oder – wenn du BDT Hub
nutzt – ein Ende-zu-Ende-verschlüsseltes Backup dorthin. Details: [Backup](experten/backup.md).

**Was ist die BDT Hub?**
Ein optionaler Server-Baustein für alles, was mehrere Geräte oder mehrere Personen betrifft:
Projekte zwischen Geräten synchronisieren, ein XR-Meeting mit anderen teilen, ein Off-Site-Backup.
Du brauchst ihn nicht, um BDT zu nutzen. Details: [BDT Hub](experten/bdt-hub.md).

**Funktioniert BDT, wenn ich offline bin?**
Alles, was keinen Endpunkt braucht, ja – deine Daten liegen lokal. Sobald eine Aktion einen
Endpunkt (SAP-System, KI-Anbieter, …) aufruft, brauchst du natürlich eine Verbindung dorthin.

**Ich habe einen Fehler gefunden oder eine Idee für ein neues Werkzeug – wie melde ich das?**
Ein eingebauter „Fehler oder Idee melden"-Weg ist in Vorbereitung. Bis dahin: wende dich direkt
an deinen Ansprechpartner bei Brandeis Consulting.

**Ich finde eine Kachel nicht mehr, an die ich mich erinnere.**
Prüf zuerst den Sichtbarkeits-Regler (siehe oben) – vielleicht ist sie nur ausgeblendet. Wurde
eine Kachel tatsächlich entfernt oder umbenannt, findest du das im Changelog (auf GitHub).
