# Betrieb als Web-App

BDT lässt sich auch als reine Web-App betreiben – ohne Browser-Erweiterung oder Installation,
einfach über eine URL erreichbar.

## Für Anwender:innen

Öffne die von deiner Organisation bereitgestellte URL im Browser. Über das Browser-Menü kannst
du die Seite als **PWA installieren** – dann bekommst du ein eigenes App-Icon und ein eigenes
Fenster, ähnlich einer Desktop-App, weiterhin auf Basis des Browsers.

Funktional ist die Web-App identisch zur Erweiterung. Ob sie direkten Zugriff auf dein
SAP-System hat oder eine Local Bridge dahinter läuft, hängt davon ab, wie die Instanz betrieben
wird (siehe [Deployment-Varianten](deployment.md)) – im Zweifel frag deinen Admin.

## Für Admins: Selbst hosten

Die Web-App lässt sich auf verschiedene Arten selbst betreiben:

- **Lokal zum Ausprobieren:** ein kleiner mitgelieferter Node-Server, ideal für Tests im eigenen
  Netz.
- **Docker:** ein Container-Image für einen dauerhaften internen Betrieb.
- **Als OAAP-Anwendung:** für Organisationen, die eine passende Plattform betreiben – analog zum
  „BDT Hub"-Backend. Dieser Weg ist in Vorbereitung; melde dich bei Brandeis Consulting, wenn du
  daran interessiert bist.

## Freigegebene/öffentliche Instanzen

Eine öffentlich erreichbare Web-App-Instanz sollte bewusst eingeschränkt betrieben werden: Ohne
zusätzliche Absicherung könnte eine mitgelieferte Local Bridge theoretisch als offener Proxy
missbraucht werden, und ein geteilter Server-Speicher hat ohne Weiteres keine Trennung zwischen
Anwender:innen. Für solche Instanzen gibt es einen „Public-Modus", der diese beiden Dinge gezielt
abschaltet. Sprich deinen Admin an, wenn du unsicher bist, ob eine Instanz dafür geeignet
konfiguriert ist.
