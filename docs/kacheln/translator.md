# Übersetzer

Übersetzt eingegebenen Text mit der lokalen (browsereigenen) oder einer konfigurierten KI – ein
schnelles, allgemeines Übersetzungswerkzeug. Für das gezielte Übersetzen von SAP-Entwicklungs-
objekten (Datenelemente, Nachrichtenklassen, …) nutze stattdessen das
[Übersetzungswerkzeug](translation-tool.md).

## Voraussetzungen

- Ein eingerichteter KI-Anbieter (lokal oder OpenAI-kompatibel).

## Typischer Ablauf

1. Text eingeben, Zielsprache wählen.
2. Übersetzen lassen.
3. Ergebnis kopieren oder weiterverwenden.

## Funktionen im Detail

- **Quellsprache „Automatisch erkennen“** oder fest wählen; der Knopf zwischen den Feldern tauscht
  Quell- und Zielsprache. Die Zielsprache ist mit deiner Standard-Zielsprache vorbelegt.
- **Anbieter-Hinweis oben:** zeigt, ob Chromes lokale KI (Translator API, ohne Netzwerkzugriff)
  oder ein konfigurierter KI-Anbieter übersetzt – im zweiten Fall geht der Text an diesen Server.
- **Aktionsleiste unter der Übersetzung:** Kopieren, Download, E-Mail, Teilen und als Kontext an
  den KI-Chat.

## Tipps & Grenzen

- Die Qualität hängt vom gewählten KI-Anbieter/Modell ab.
