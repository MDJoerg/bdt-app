# KI-Chat

Ein Chat mit deinem konfigurierten KI-Anbieter – als eigene Kachel im Vollbild ODER als
Seitenleiste, die sich von praktisch jeder anderen Seite aus öffnen lässt. Viele Kacheln
übergeben dir dabei automatisch passenden Kontext (z. B. Suchtreffer, eine Objektauswahl).

## Voraussetzungen

- Ein eingerichteter KI-Anbieter (Einstellungen → „KI Funktionen") – entweder die im Browser
  eingebaute KI oder ein konfigurierter OpenAI-kompatibler Anbieter (z. B. LM Studio, Ollama, ein
  Cloud-Anbieter).
- Für die Werkzeugausführung gegen MCP-Server ist ausschließlich ein OpenAI-kompatibler Anbieter
  nutzbar.

## Typischer Ablauf

1. Chat öffnen – über die eigene Kachel (Vollbild) oder das KI-Symbol in der Fußzeile praktisch
   jeder Seite (Seitenleiste).
2. Frage stellen, optional Kontext von einer anderen Kachel mitbringen (z. B. „Zum KI-Chat" aus
   der [Suche](search.md)).
3. Optional ein Agenten-Preset wählen (vordefinierte Rolle/Anweisung).
4. Antwort erhält Markdown-Formatierung, Diagramme (Mermaid) und kopierbare Codeblöcke.

## Funktionen im Detail

- Skills wie `/translate`, `/analyze_mcp` oder `/wissen` lösen spezialisierte Abläufe aus.
- Bei aktivierter Werkzeugausführung kann die KI Werkzeuge eines verbundenen MCP-Servers
  tatsächlich aufrufen, um deine Frage zu beantworten.
- Antworten der KI werden ausschließlich als Text angezeigt, nie als ausführbares HTML.

## Tipps & Grenzen

- Die Qualität der Antworten hängt vom gewählten Modell/Anbieter ab – BDT selbst bewertet oder
  filtert KI-Antworten nicht inhaltlich.
- Ein KI-Anbieter ist bewusst eine bewusste, von dir konfigurierte Verbindung – BDT wählt nie
  selbstständig einen anderen Dienst.
