# Datenquellen OP-Bericht-Assistent

Für diesen Use Case gibt es keinen passenden offenen Datensatz: Echte OP-Diktate sind Patientendaten, und ein frei nutzbares deutsches Korpus gesprochener OP-Berichte habe ich nicht gefunden. Gearbeitet wird deshalb mit selbst geschriebenen und selbst eingesprochenen Diktaten.

## Im Repo
| Datei | Inhalt | Herkunft und Lizenz |
|---|---|---|
| `diktat_01_skript.md` | Ein Diktat zum Vorlesen mit eingebauter Korrektur, dazu Prüffragen | Frei erfunden für den Hackathon, medizinisch nicht geprüft. Frei verwendbar. |

Tonaufnahmen liegen bewusst nicht im Repo. Das Diktat wird vor Ort vorgelesen, das ist näher an der echten Situation als eine Computerstimme.

## Wege zur Spracherkennung
| Weg | Was er kann | Aufwand | Hinweis |
|---|---|---|---|
| Spracherkennung des Browsers (Web Speech API) | Wandelt Sprache live in Text um, ohne Schlüssel und ohne Installation | gering, im Spickzettel Block 5 | Funktioniert nicht in jedem Browser. Der Ton geht je nach Browser an einen Dienst im Netz. |
| [Whisper](https://github.com/openai/whisper) | Offenes Spracherkennungsmodell, läuft lokal auf dem Laptop, gute Ergebnisse auf Deutsch | mittel, braucht Python | Kein Ton verlässt den Rechner. Lizenz auf der Projektseite. |
| [whisper.cpp](https://github.com/ggerganov/whisper.cpp) | Dieselben Modelle, schneller und ohne Python | mittel | Für Teams mit Technik-Erfahrung. Lizenz auf der Projektseite. |

### So bindet man Whisper an (in einfachen Worten)
1. Die Seite nimmt den Ton auf und schickt die Audiodatei an euren eigenen kleinen Server.
2. Der Server ruft das lokal installierte Whisper auf und bekommt den Text zurück.
3. Ab da ist alles wie beim Tippen: Der Text landet im Transkriptfeld und geht an die KI.

Prompt für Claude Code:
```
Ersetze die Spracherkennung des Browsers durch eine lokale Erkennung mit Whisper. Prüfe zuerst, was auf diesem Rechner dafür installiert werden muss, erkläre es mir in fünf Sätzen und warte auf meine Freigabe.
```

## Stilvorlagen für den Berichtsaufbau
Den Aufbau des OP-Berichts legt das Medizin-Team in `spec.md` selbst fest. Hausinterne Vorlagen nur verwenden, wenn die eigene Klinik zustimmt, und ohne Patientendaten.

## Empfehlung für den Hackathon
- Zwei bis drei Diktate reichen: eines zum Entwickeln, eines als Blind-Diktat, eines für die Demo.
- Unterschiedliche Sprecherinnen und Sprecher ausprobieren, auch mit Dialekt und in normalem Sprechtempo.
- Keine Namen echter Personen diktieren.
