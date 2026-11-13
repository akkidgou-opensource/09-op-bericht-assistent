# Spickzettel OP-Bericht-Assistent · 8 Stunden

Acht Blöcke. Jeden Prompt in Claude Code kopieren, das Ergebnis prüfen, dann weiter. Der Plan beginnt mit Text (sicher) und nimmt die Sprache erst danach dazu.

| Block | Zeit | Thema |
|---|---|---|
| 1 | 30 Min. | Setup |
| 2 | 45 Min. | Vorgaben: Aufbau des OP-Berichts |
| 3 | 45 Min. | Texteingabe und Anzeige |
| 4 | 60 Min. | KI strukturiert den Bericht |
| 5 | 75 Min. | Diktieren im Browser |
| 6 | 75 Min. | Mit Diktaten testen |
| 7 | 60 Min. | Bearbeiten, Export, Robustheit |
| 8 | 60 Min. | Ergebnis, Demo, Pitch |

Bleiben 30 Minuten Puffer.

## Block 1 · Setup
Schlüssel eintragen: `.env.example` zu `.env` kopieren und den ausgehändigten Schlüssel eintragen (im Texteditor, nicht über Claude Code).
```
Lies README.md und CLAUDE.md und sieh dir daten/diktat_01_skript.md an. Prüfe, ob Node.js ab Version 20 installiert ist, und lege die leeren Ordner prompt und ergebnisse an. Sag mir in drei Sätzen, was als Nächstes kommt.
```
**Fertig, wenn:** Node passt und `.env` existiert.

## Block 2 · Vorgaben (ohne Code)
In `spec.md` festlegen:
- Abschnitte des OP-Berichts in fester Reihenfolge (z. B. Diagnose, Eingriff, Seite, Team, Lagerung, Zugang, Vorgehen, Implantate, Verschluss, Besonderheiten, Procedere)
- Umgang mit Korrekturen im Diktat („Korrektur: …“ ersetzt die vorherige Angabe)
- Umgang mit Lücken: markieren als „[nicht diktiert]“, nie ergänzen
- Schreibweise: Zahlen, Einheiten, Seitenangaben

**Fertig, wenn:** der Aufbau von zwei Personen gegengelesen ist.

## Block 3 · Texteingabe und Anzeige
```
Baue die Grundversion: server.js und public/index.html. Links ein großes Textfeld „Diktat (Transkript)“, rechts der Bereich „OP-Bericht“. Ein Button „Beispieldiktat laden“ fügt den Diktattext aus daten/diktat_01_skript.md ein. Auf dem Handy stehen beide Bereiche untereinander. Der Hinweis aus CLAUDE.md ist immer sichtbar.
```
**Fertig, wenn:** die Seite auf Laptop und Handy läuft (noch ohne KI).

## Block 4 · KI strukturiert den Bericht
```
Ergänze den Button „Bericht erstellen“. Er schickt das Transkript an einen Endpunkt /api/bericht, der die Anthropic Messages API aufruft. Der System-Prompt wird bei jeder Anfrage frisch aus prompt/system.md gelesen und enthält Abschnitte und Regeln WORTGETREU aus spec.md. Antwort als JSON mit einem Feld je Abschnitt plus den Feldern unklare_stellen und korrekturen_angewendet. Die KI verwendet nur, was im Transkript steht. Schlüssel und Modell kommen nur aus .env.
```
**Fertig, wenn:** aus dem Beispieldiktat ein gegliederter Bericht entsteht.

## Block 5 · Diktieren im Browser
Einfacher Weg zuerst: die Spracherkennung des Browsers. Alternativen stehen in `daten/QUELLEN.md`.
```
Ergänze einen großen Aufnahmeknopf „Diktat starten / stoppen“. Nutze die Spracherkennung des Browsers (Web Speech API, Sprache Deutsch), der erkannte Text erscheint laufend im Transkriptfeld und bleibt editierbar. Wenn der Browser das nicht unterstützt, erscheint ein verständlicher Hinweis, welcher Browser funktioniert. Zeige während der Aufnahme deutlich an, dass das Mikrofon läuft.
```
**Wichtig:** Die Spracherkennung des Browsers schickt den Ton je nach Browser an einen Dienst im Netz. Deshalb nur simulierte Diktate ohne Namen echter Personen.

**Fertig, wenn:** ein vorgelesenes Diktat als Text im Feld steht.

## Block 6 · Mit Diktaten testen
Eine Person liest `daten/diktat_01_skript.md` vor, zuerst langsam, dann in normalem Tempo.
- Welche Fachbegriffe wurden falsch erkannt? Liste führen
- Stimmen im Bericht Seite, Implantat, Schraubenzahl? Wurde die Korrektur im Diktat richtig angewendet?
- Steht etwas im Bericht, das nicht diktiert wurde?

Pro Durchlauf **eine** Prompt-Änderung. Danach ein zweites Diktat selbst schreiben (anderer Eingriff) und als Blind-Diktat verwenden.

**Fertig, wenn:** drei dokumentierte Durchläufe vorliegen.

## Block 7 · Bearbeiten, Export, Robustheit
```
Mache jeden Abschnitt des Berichts direkt editierbar, hebe „[nicht diktiert]“ und unklare Stellen farbig hervor und ergänze „Kopieren“ und „Drucken/als PDF“. Lege prompt/begriffe.md an, eine Liste häufig falsch erkannter Fachbegriffe mit richtiger Schreibweise, die dem System-Prompt angehängt wird. Verständliche Meldungen bei fehlendem Mikrofon-Zugriff, fehlendem Netz und Zeitüberschreitung.
```
**Fertig, wenn:** der fertige Bericht gedruckt werden kann und Lücken sichtbar markiert sind.

## Block 8 · Ergebnis, Demo, Pitch
- Blind-Diktat **einmal** laufen lassen, Ergebnis nicht nachbessern
- `ergebnis.md`: Aufbau, Erkennungsfehler, Fehler im Bericht, Limitationen (ruhiger Raum statt OP-Saal, wenige Diktate)
- Demo: 60 Sekunden live diktieren, dann der fertige Bericht. Text-Variante als Backup
- Pitch: Problem, Live-Demo, wie getestet, nächste Schritte
