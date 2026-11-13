# 09 · OP-Bericht-Assistent

> Prototyp für den AKKI Hackathon 2026. Nur simulierte Diktate, kein Medizinprodukt, kein Ersatz für den ärztlich geprüften OP-Bericht.

**Bereich:** OP

**Idee:** Eine sprachgesteuerte KI erstellt während oder direkt nach der OP aus Zuruf oder Diktat einen strukturierten OP-Bericht.

## Warum
OP-Berichte werden meist erst im Nachhinein aus dem Gedächtnis diktiert. Ein Live-Assistent kann Zeit sparen und die Vollständigkeit verbessern.

## Was am Ende stehen soll
- Audio-Aufnahme oder Upload eines simulierten OP-Diktats
- Transkription und Strukturierung im OP-Bericht-Format
- Editierbare Ausgabe des OP-Berichts

**Erfolgskriterium:** Aus einem simulierten Diktat entsteht ein vollständiger, strukturierter OP-Bericht.

## So startet ihr
1. Oben auf **Code → Download ZIP** klicken und entpacken.
2. Im entpackten Ordner ein Terminal öffnen und `claude` eingeben.
3. `SPICKZETTEL.md` öffnen und mit Block 1 beginnen.

## Was in diesem Repo liegt
| Datei | Wofür |
|---|---|
| `SPICKZETTEL.md` | Umsetzungsplan für 8 Stunden, Block für Block |
| `CLAUDE.md` | Regeln, an die sich Claude Code hält |
| `daten/QUELLEN.md` | Wege zur Spracherkennung und Hinweise zu den Testdaten |
| `daten/diktat_01_skript.md` | Ein frei erfundenes Diktat zum Vorlesen, mit Prüffragen |

## Stolpersteine
- Nur simulierte Diktate verwenden, keine Namen echter Personen
- Fachbegriffe werden von der Spracherkennung oft falsch geschrieben: Das Transkript bleibt sichtbar und korrigierbar
- Der Bericht enthält nur, was diktiert wurde. Lücken werden markiert, nicht gefüllt

## Für Erfahrene
- Live-Modus: Zurufe während der OP mit Zeitstempel sammeln und am Ende zum Bericht ordnen
- Spracherkennung lokal auf dem Laptop statt über einen Dienst im Netz
- Kodiervorschläge (OPS) als getrennte, klar gekennzeichnete Zusatzausgabe
