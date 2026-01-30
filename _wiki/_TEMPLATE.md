---
title: "Titel deines Wiki-Eintrags"
layout: wiki
category: "A"  # Buchstabe für die alphabetische Sortierung
description: "Kurze Beschreibung des Eintrags"
---

# {{ page.title }}

Hier kannst du den Inhalt deines Wiki-Eintrags schreiben.

## Abschnitt 1

Dein Inhalt...

## Abschnitt 2

Mehr Inhalt...

### Tipps zur Formatierung

- Verwende Markdown für die Formatierung
- Listen funktionieren wie gewohnt
- **Fettdruck** und *kursiv* sind möglich
- Links: [Link-Text](https://example.com)
- Code: `inline code` oder

```python
# Code-Block
def hello():
    print("Hello World")
```

### Bilder einfügen

![Alt-Text](/assets/images/bild.jpg)

### Interne Verlinkung

Du kannst auf andere Wiki-Einträge verlinken:
- [Anderer Eintrag]({% link _wiki/anderer-eintrag.md %})
- Oder einfach: [Anderer Eintrag](/anderer-eintrag/)
