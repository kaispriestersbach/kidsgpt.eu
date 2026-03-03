# KidsGPT.eu (Web)

Statische Website fuer Eltern, Lehrkraefte und Kinder mit KI-Prompts fuer Lernen, Schule und Alltag.

Produktivseite: [https://www.kidsgpt.eu/](https://www.kidsgpt.eu/)

## Was dieses Repository enthaelt

- `index.html`: Hauptseite mit Prompt-Auswahl, Filter, Vorschau und Weiterleitung zu Chatbots.
- `prompts.json`: Prompt-Bibliothek (aktuell 75 Eintraege in 10 Hauptkategorien).
- `leitfaden.html`: Ausfuehrlicher Prompting-Leitfaden fuer Eltern.
- `infografik.html`: Eigenstaendige Infografik-Seite.
- Assets: Logos, Favicons, Bilder sowie lokale Schriftdateien (`.woff`, `.woff2`).
- `site.webmanifest`: Web-App-Metadaten (Name, Icons, Theme-Farbe).

## Funktionsweise

- Die Seite laedt Prompts clientseitig aus `prompts.json` (`fetch('prompts.json')`).
- In Schritt 1 wird ein Prompt ausgewaehlt (Schnellstart + Bibliothek mit Suche/Filter).
- In Schritt 2 wird ein Ziel-Chatbot gewaehlt.
- In Schritt 3 wird ein finaler Prompt erzeugt und an den Chatbot uebergeben.
- ChatGPT, Claude, Mistral und Copilot werden mit URL-Query vorbefuellt.
- Bei Gemini und Duck.ai wird der Prompt zuerst in die Zwischenablage kopiert.

## Lokal starten

Wichtig: Nicht per `file://` oeffnen, da `prompts.json` per `fetch` geladen wird.

```bash
cd /Users/kai/Documents/work/KidsGPT/web
python3 -m http.server 8080
```

Dann im Browser:

- `http://localhost:8080/index.html`
- `http://localhost:8080/leitfaden.html`
- `http://localhost:8080/infografik.html`

## Deployment

Das Projekt ist rein statisch. Fuer den Server-Deploy wird der komplette Ordner als Document-Root (oder in den Zielpfad) kopiert.

Empfehlungen:

- Dateirechte fuer Webdateien auf `644` halten (keine unnoetigen Executable-Bits).
- MIME-Typen fuer Fonts (`.woff`, `.woff2`) und Manifest korrekt ausliefern.
- Nach Deployment `index.html` + `prompts.json` gemeinsam pruefen, damit Filter und Prompt-Generierung funktionieren.

## `prompts.json` pflegen

Mindestens diese Felder werden im Frontend erwartet:

- `id`
- `title`
- `promptText` (String oder Objekt)
- `mainCategory`

Uebliche weitere Felder:

- `description`
- `tags` (Array)
- `contextNeeded` (Array oder `false`)
- `subCategory`
- `ageGroup`

Kurzer Validierungscheck:

```bash
node -e "const fs=require('fs');const a=JSON.parse(fs.readFileSync('prompts.json','utf8'));console.log('prompts',a.length)"
```

## Hinweise

- Es gibt aktuell keinen Build-Schritt, kein Framework und keinen Package-Manager in diesem Repo.
- Falls ein Test-/Lint-Setup ergaenzt wird, sollte diese README entsprechend aktualisiert werden.
