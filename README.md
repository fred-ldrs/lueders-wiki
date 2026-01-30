# lueders-wiki

Ein persönliches, themenoffenes Wissensarchiv – aufgebaut mit Jekyll.

## 🚀 Schnellstart

### Voraussetzungen

- Ruby (Version 2.7 oder höher)
- Bundler (`gem install bundler`)

### Installation & Lokale Entwicklung

```bash
# Dependencies installieren
bundle install

# Lokalen Server starten
bundle exec jekyll serve

# Wiki ist dann erreichbar unter: http://localhost:4000
```

## ✏️ Neue Inhalte hinzufügen

### Schnellste Methode: Template kopieren

1. Kopiere die Datei `_wiki/_TEMPLATE.md`
2. Benenne sie nach deinem Thema (z.B. `agilitaet.md`)
3. Bearbeite den Front Matter (Titel, Kategorie, Beschreibung)
4. Schreibe deinen Inhalt in Markdown

**Beispiel:**

```bash
# Neue Datei erstellen
cp _wiki/_TEMPLATE.md _wiki/agilitaet.md

# Datei bearbeiten
code _wiki/agilitaet.md
```

### Front Matter erklärt

```yaml
---
title: "Titel deines Eintrags"        # Wird als Überschrift angezeigt
layout: wiki                           # Immer "wiki" verwenden
category: "A"                          # Buchstabe für Index (A-Z)
description: "Kurze Beschreibung"      # Optional, für SEO
---
```

### Index aktualisieren

Bearbeite die Datei `index.md` und füge einen Link zu deinem neuen Eintrag hinzu:

```markdown
## A

- [Neuer Eintrag](/neuer-eintrag/)
- ...
```

## 📁 Projektstruktur

```
lueders-wiki/
├── _config.yml           # Jekyll-Konfiguration
├── _layouts/             # HTML-Templates
│   ├── default.html      # Basis-Layout
│   └── wiki.html         # Layout für Wiki-Einträge
├── _wiki/                # Deine Wiki-Inhalte
│   ├── _TEMPLATE.md      # Vorlage für neue Einträge
│   └── bitcoin.md        # Beispiel-Eintrag
├── index.md              # Startseite (alphabetisches Verzeichnis)
├── impressum.html        # Impressum & Datenschutz
├── Gemfile               # Ruby-Dependencies
└── README.md             # Diese Datei
```

## 🎨 Design anpassen

Das Design ist im Stil von lueders.app gehalten. Anpassungen kannst du in [`_layouts/default.html`](_layouts/default.html) vornehmen.

### CSS-Variablen anpassen

Im `<style>`-Block von `default.html`:
- Schriftarten
- Farben
- Abstände
- Layout-Breite

## 🔧 Erweiterte Funktionen

### Collections

Wiki-Einträge sind als Jekyll Collection konfiguriert (`_wiki/`). Das ermöglicht:
- Automatische Verlinkung
- Kategorisierung
- Eigene Metadaten
- Flexible Erweiterung

### Neue Collection hinzufügen

In `_config.yml`:

```yaml
collections:
  wiki:
    output: true
    permalink: /:name/
  projekte:          # Neue Collection
    output: true
    permalink: /projekte/:name/
```

## 📝 Markdown-Tipps

```markdown
# Überschrift 1
## Überschrift 2

**Fettdruck** und *kursiv*

- Listen
- Funktionieren
- Super

[Links](https://example.com)

`inline code`

​```python
# Code-Blöcke
print("Hello")
​```
```

## 🌐 Deployment

### GitHub Pages

1. Repository auf GitHub pushen
2. In Settings → Pages → Source: "GitHub Actions" wählen
3. `.github/workflows/jekyll.yml` erstellen:

```yaml
name: Deploy Jekyll site to Pages

on:
  push:
    branches: ["main"]

permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/configure-pages@v4
      - uses: actions/jekyll-build-pages@v1
      - uses: actions/upload-pages-artifact@v3

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - id: deployment
        uses: actions/deploy-pages@v4
```

### Netlify / Vercel

Einfach Repository verbinden, Build-Command: `bundle exec jekyll build`

## 🤝 Workflow-Empfehlung

1. Neues Thema? → Template kopieren und anpassen
2. Inhalt schreiben → Lokal testen mit `bundle exec jekyll serve`
3. Index aktualisieren → Link zur neuen Seite hinzufügen
4. Commiten & pushen → Automatisches Deployment

## 📄 Lizenz

Persönliches Projekt von Frederik Lüders