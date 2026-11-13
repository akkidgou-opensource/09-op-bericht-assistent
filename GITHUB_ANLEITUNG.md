# Eure Arbeit auf GitHub bringen

Diese Anleitung funktioniert ohne Git-Kenntnisse. Ihr kopiert die Prompts in euren Coding-Agenten (Claude Code oder Codex), er erledigt die Technik. Nur die Anmeldung im Browser macht ihr selbst.

## In drei Sätzen
- **GitHub** ist der Ort im Netz, an dem euer Projekt liegt und den andere sehen können.
- **Sichern** (Fachwort: Commit) heißt, einen Zwischenstand festzuhalten.
- **Hochladen** (Fachwort: Push) heißt, diesen Stand zu GitHub zu schicken.

## Was ihr braucht
- Ein kostenloses GitHub-Konto für mindestens eine Person im Team (github.com, „Sign up“)
- Den Projektordner, in dem ihr mit dem Agenten arbeitet

## Schritt 1 · Einmal anmelden
Prompt:
```
Prüfe, ob git und die GitHub-CLI (gh) installiert sind. Falls etwas fehlt, erkläre mir die Installation Schritt für Schritt und warte. Prüfe dann mit „gh auth status“, ob ich bei GitHub angemeldet bin, und sag mir das Ergebnis in einem Satz.
```
Seid ihr noch nicht angemeldet, öffnet ein zweites Terminal-Fenster und tippt:
```
gh auth login
```
Wählt nacheinander: **GitHub.com**, **HTTPS**, **Yes**, **Login with a web browser**. Im Terminal erscheint ein Code aus acht Zeichen. Der Browser öffnet sich, dort gebt ihr den Code ein und bestätigt. Fertig, wenn im Terminal „Authentication complete“ steht.

## Schritt 2 · Eigenes Team-Repository anlegen und verbinden
Ersetzt `TEAMNAME` durch euren Teamnamen (ohne Leerzeichen).
```
Lege für diesen Ordner ein neues öffentliches Repository in meinem GitHub-Konto an, Name: 09-op-bericht-assistent-TEAMNAME. Prüfe vorher, dass .env in .gitignore steht und nicht hochgeladen wird. Falls der Ordner schon mit einem anderen Repository verbunden ist, ersetze die Verbindung durch das neue. Lade dann den aktuellen Stand hoch und nenne mir am Ende den Link.
```
**Fertig, wenn:** ihr den Link im Browser öffnen könnt und eure Dateien dort seht.

## Schritt 3 · Zwischenstände hochladen
Am besten nach jedem Block im Spickzettel:
```
Sichere den aktuellen Stand und lade ihn zu GitHub hoch. Beschreibe in einem Satz, was sich seit dem letzten Mal geändert hat. Prüfe vorher, dass keine Schlüssel oder .env-Dateien dabei sind.
```

## Schritt 4 · Zu mehreren arbeiten
Die Person mit dem Repository lädt die anderen ein:
```
Lade den GitHub-Nutzer BENUTZERNAME als Mitarbeitenden in dieses Repository ein.
```
Die anderen nehmen die Einladung per E-Mail an und holen sich das Projekt:
```
Lade das Repository https://github.com/KONTONAME/09-op-bericht-assistent-TEAMNAME in einen neuen Ordner herunter und richte es so ein, dass ich Änderungen hochladen kann.
```
Bevor jemand weiterarbeitet:
```
Hole den neuesten Stand von GitHub und führe ihn mit meinem zusammen, ohne meine Änderungen zu verlieren. Erkläre mir, falls es Konflikte gibt.
```

## Schritt 5 · Abgabe
Schickt den Link eures Team-Repositorys an die Organisator:innen. Im Repository sollten `ergebnis.md` und eine kurze Beschreibung in der `README.md` stehen.

**Alternative, falls ihr von den Organisator:innen direkt in das AKKI-Repository eingeladen wurdet:**
```
Verbinde diesen Ordner mit https://github.com/akkidgou-opensource/09-op-bericht-assistent und lade meinen Stand in einen neuen Zweig mit dem Namen team-TEAMNAME hoch. Ändere nichts am Hauptzweig.
```

## Wenn es hakt
| Was ihr seht | Was hilft |
|---|---|
| „Permission denied“ oder „403“ | Ihr seid nicht oder mit dem falschen Konto angemeldet. Schritt 1 wiederholen. |
| „rejected“ oder „non-fast-forward“ | Jemand anderes hat inzwischen hochgeladen. Den Prompt „Hole den neuesten Stand …“ aus Schritt 4 verwenden. |
| „gh: command not found“ | Die GitHub-CLI fehlt. Den Prompt aus Schritt 1 verwenden oder Mentor:in fragen. |
| Der Agent will ein Passwort oder einen Token von euch | Nicht eingeben. Stattdessen `gh auth login` wie in Schritt 1. |
| Die Datei `.env` oder ein Schlüssel ist auf GitHub gelandet | Sofort Mentor:in Bescheid geben, der Schlüssel wird gesperrt und ersetzt. Löschen allein reicht nicht. |

## Drei Regeln
1. Schlüssel stehen nur in `.env` und kommen nie auf GitHub.
2. Keine echten Patientendaten, auch nicht „nur kurz zum Testen“.
3. Lieber oft kleine Stände hochladen als einmal am Ende alles.
