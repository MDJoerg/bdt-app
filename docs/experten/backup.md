# Backup & Datensicherung

Deine Daten liegen lokal in deinem Browser bzw. auf deinem Rechner. Damit du sie nicht verlierst
(neuer Rechner, gelöschter Browser-Speicher, versehentliches Löschen), gibt es drei sich
ergänzende Wege.

## 1. Automatische lokale Snapshots

BDT legt in regelmäßigen Abständen automatisch eine Sicherungsdatei deines gesamten
Datenbestands an (alle Projekte, Einstellungen, Endpunkte – ohne Zugangsdaten im Klartext).
Einrichten unter Einstellungen → „Sicherung". Die Snapshots landen je nach Variante an
unterschiedlichen Orten (z. B. ein von dir gewählter lokaler Ordner).

## 2. Projekt-Export/-Import

Über Einstellungen → „Projekte" kannst du ein einzelnes Projekt vollständig als Datei
exportieren – inklusive Wissensablage und Assets. Diese Datei kannst du archivieren oder in ein
anderes BDT (z. B. auf einem anderen Rechner, oder bei einer Kollegin) importieren. Import
**ersetzt** ein bestehendes Projekt gleichen Namens vollständig, statt es zu vermischen – lies
den Bestätigungsdialog also genau, bevor du importierst.

## 3. BDT-Hub-Backup (Ende-zu-Ende-verschlüsselt, off-site)

Wenn du eine BDT-Hub-Verbindung eingerichtet hast (siehe [BDT Hub](bdt-hub.md)), kannst du
zusätzlich automatisch **außerhalb** deines Rechners sichern lassen – Einstellungen → „Sicherung"
→ „BDT-Hub-Backup". Dafür legst du eine eigene Backup-Passphrase an (getrennt von deinem
Vault-Passwort): BDT verschlüsselt den kompletten Snapshot **auf deinem Gerät**, bevor er zum
Hub geschickt wird – der Server sieht zu keinem Zeitpunkt den Klartext, nur du kannst die
Sicherung mit der Passphrase wieder lesbar machen. Beim Wiederherstellen fragt BDT diese
Passphrase deshalb immer erneut ab, unabhängig davon, ob dein Vault gerade entsperrt ist.

**Wichtig:** Verlierst du die Backup-Passphrase, ist die Sicherung nicht mehr lesbar – es gibt
keinen „Passphrase vergessen"-Weg. Notier sie dir an einem sicheren Ort.

## Was NICHT gesichert wird

Ein paar rein temporäre/lokale Datenbestände sind bewusst nicht Teil der Sicherung, weil sie
jederzeit neu entstehen können bzw. gerätespezifisch sind: Sammelkörbe, das Daten-Studio
(Datasets/Analysen), und der Suchindex für die KI-gestützte Suche (Vektorstore) – letzterer baut
sich nach einem Wiederherstellen automatisch wieder auf.
