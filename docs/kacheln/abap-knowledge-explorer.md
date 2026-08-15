# ABAP Knowledge Explorer

Durchsucht dein SAP-Repository nach vorhandener Dokumentation – Knowledge Transfer Documents
sowie ABAP-Doc-Kommentare direkt aus dem Quelltext von Klassen/Interfaces – und macht sie in der
Wissensablage nutzbar.

## Voraussetzungen

- Ein eingerichteter SAP-Endpunkt.

## Typischer Ablauf

1. Quelle(n) auswählen: Knowledge Transfer Document und/oder ABAP Doc.
2. Suchbegriff, optional Paket-/Anwendungskomponenten-Filter.
3. Treffer markieren, „Auswahl extrahieren" lädt den passenden Markdown-Text je Quelle.
4. „In Wissensablage übernehmen" legt je Treffer ein eigenes Markdown-Infoobjekt an (mit
   quellengetrennter Dublettenerkennung).
5. Optional „Mit KI dokumentieren" – komponiert aus der markierten Auswahl eine Nachricht an
   den KI-Chat.

## Funktionen im Detail

- Ein Volltextfilter durchsucht den bereits geladenen Inhalt.
- Nicht extrahierte Objekte werden bei „Mit KI dokumentieren" als sichtbarer Hinweis
  mitgegeben, statt stillschweigend zu fehlen.

## Tipps & Grenzen

- Rein lesend.
- ABAP Doc findet nur Kommentare, die im Quelltext tatsächlich mit `"! ` geschrieben wurden.
