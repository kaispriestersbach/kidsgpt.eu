# KidsGPT.eu 🤖🎓

> Die sichere Prompt-Bibliothek für KI-gestütztes Lernen mit Kindern

Statische Website für Eltern, Lehrkräfte und Kinder mit KI-Prompts für Lernen, Schule und Alltag.

Produktivseite: [https://www.kidsgpt.eu/](https://www.kidsgpt.eu/)

## 🌟 Features

- **75+ kuratierte Prompts** in 10 Kategorien
- **Sichere Integration** mit Le Chat, ChatGPT, Claude, Copilot, Gemini und Duck.ai
- **DSGVO-orientiert** mit Fokus auf Datensparsamkeit
- **Keine Datensammlung** auf dieser Website - Interaktion findet beim gewählten Chatbot-Anbieter statt
- **Elternbegleitung** als zentrales Nutzungskonzept

## 📚 Kategorien

✅ Lernen & Schule (Mathe, Deutsch, Sprachen, etc.)  
✅ Lernstrategien & Coaching  
✅ Kreativität & Geschichten  
✅ Spiel & Spaß  
✅ Alltag & Organisation  
✅ Probleme lösen  
✅ Etwas Neues lernen  
✅ Auf der Höhe bleiben  
✅ Gelerntes anwenden  
✅ Veränderungen mitgestalten  

## 🛡️ Sicherheit & Datenschutz

- Empfehlung für EU-basierte KI (Le Chat von Mistral AI)
- Leitfaden für Eltern zur sicheren Nutzung von KI-Tools
- Keine persönlichen Daten für die Nutzung der Website erforderlich
- Transparente Weiterleitung zu externen KI-Anbietern

## 📖 Zum Buch

Begleitprojekt zu [„Kluge Köpfchen mit KI“ von Kai Spriestersbach & Leonie Lutz](https://kai.im/kidsgpt-buch)<sup>*</sup> - bereits erschienen und als Buch, E-Book oder Hörbuch erhältlich.

---

## Was dieses Repository enthält

- `index.html`: Hauptseite mit Prompt-Auswahl, Filter, Vorschau und Weiterleitung zu Chatbots.
- `prompts.json`: Prompt-Bibliothek (aktuell 75 Einträge in 10 Hauptkategorien).
- `leitfaden.html`: Ausführlicher Prompting-Leitfaden für Eltern.
- `infografik.html`: Eigenständige Infografik-Seite.
- Assets: Logos, Favicons, Bilder sowie lokale Schriftdateien (`.woff`, `.woff2`).
- `site.webmanifest`: Web-App-Metadaten (Name, Icons, Theme-Farbe).

## Funktionsweise

- Die Seite lädt Prompts clientseitig aus `prompts.json` (`fetch('prompts.json')`).
- In Schritt 1 wird ein Prompt ausgewählt (Schnellstart + Bibliothek mit Suche/Filter).
- In Schritt 2 wird ein Ziel-Chatbot gewählt.
- In Schritt 3 wird ein finaler Prompt erzeugt und an den Chatbot übergeben.
- ChatGPT, Claude, Mistral und Copilot werden mit URL-Query vorbefüllt.
- Bei Gemini und Duck.ai wird der Prompt zuerst in die Zwischenablage kopiert.

## Lokal starten

Wichtig: Nicht per `file://` öffnen, da `prompts.json` per `fetch` geladen wird.

```bash
cd /Users/kai/Documents/work/KidsGPT/web
python3 -m http.server 8080
```

Dann im Browser:

- `http://localhost:8080/index.html`
- `http://localhost:8080/leitfaden.html`
- `http://localhost:8080/infografik.html`

## Deployment

Das Projekt ist rein statisch. Für den Server-Deploy wird der komplette Ordner als Document-Root (oder in den Zielpfad) kopiert.

Empfehlungen:

- Dateirechte für Webdateien auf `644` halten (keine unnötigen Executable-Bits).
- MIME-Typen für Fonts (`.woff`, `.woff2`) und Manifest korrekt ausliefern.
- Nach Deployment `index.html` + `prompts.json` gemeinsam prüfen, damit Filter und Prompt-Generierung funktionieren.

## `prompts.json` pflegen

Mindestens diese Felder werden im Frontend erwartet:

- `id`
- `title`
- `promptText` (String oder Objekt)
- `mainCategory`

Übliche weitere Felder:

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
- Falls ein Test-/Lint-Setup ergänzt wird, sollte diese README entsprechend aktualisiert werden.

---

🔗 [kidsgpt.eu](https://kidsgpt.eu) | Made with ❤️ for digital education

<sup>*</sup> Partner-Link. Kaufst du darüber, erhalte ich ggf. eine Provision ohne Mehrkosten für dich. Danke!
