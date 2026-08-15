# Verwendungsnachweis

Zeigt, wo ein SAP-Objekt überall verwendet wird – als aufklappbarer Baum, den du Ebene für
Ebene tiefer öffnest. Hilfreich, bevor du ein Objekt änderst oder löschst: Wer wäre betroffen?

## Voraussetzungen

- Ein eingerichteter SAP-Endpunkt.

## Typischer Ablauf

1. Objekt eingeben (Name/Typ).
2. Verwendungsnachweis laden – die oberste Ebene der Verwender erscheint als Baum.
3. Einzelne Knoten aufklappen, um tiefer in die Verwendungskette zu gehen (wird bei Bedarf
   nachgeladen).
4. Ergebnis exportieren oder als Kontext an eine andere Kachel übergeben.

## Funktionen im Detail

- Nachladen passiert nur beim tatsächlichen Aufklappen eines Knotens – kein Vorab-Laden des
  ganzen Baums.

## Tipps & Grenzen

- Rein lesend.
- Bei sehr weit verzweigten Objekten (z. B. zentrale Basis-Klassen) kann der Baum entsprechend
  groß werden – arbeite dich gezielt Ebene für Ebene vor, statt alles auf einmal aufzuklappen.
