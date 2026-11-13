# Projektregeln für Claude Code

Lies zuerst `README.md`. Dort steht, was in diesem Projekt gebaut wird.

- **Rahmen:** Prototyp für den AKKI Hackathon 2026. Die Nutzer sind Ärztinnen und Ärzte, viele ohne IT-Kenntnisse.
- **Sprache:** Antworte immer auf Deutsch, in einfachen Worten, ohne Fachjargon. Erkläre nach jeder Änderung in höchstens 3 Sätzen, was du getan hast und wie ich es prüfe.
- **Technik:** Node.js (ab Version 20), eine Datei `public/index.html` (HTML, CSS, JavaScript) und eine Datei `server.js`. Kein React, kein Build-Schritt, keine zusätzlichen npm-Pakete, solange es vermeidbar ist. Start mit `node --env-file=.env server.js`. Wenn das Team ausdrücklich eine andere Technik wünscht, ist das erlaubt.
- **Sicherheit:** API-Schlüssel stehen nur in `.env` und werden nur im Server verwendet, nie im Browser-Code, nie im Terminal-Log. `.env` gehört in `.gitignore`. Hochgeladene Bilder, Texte und Tonaufnahmen werden nicht gespeichert und nicht geloggt.
- **Daten:** Es werden nur öffentliche oder synthetische Testdaten verwendet, niemals echte Patientendaten.
- **Medizinische Inhalte** (Systemprompt, Ampel-Definitionen, Schwellenwerte, Algorithmen) niemals eigenmächtig ändern oder ergänzen. Nur wortgetreu übernehmen oder auf ausdrückliche Anweisung ändern.
- **Arbeitsweise:** Vor größeren Änderungen kurz sagen, was du vorhast. Nach Änderungen die App selbst starten und prüfen, ob sie läuft.
- **Hinweis in der App:** Jederzeit sichtbar muss stehen: „Prototyp – nur Testdaten. Kein Ersatz für ärztliche Beurteilung.“
