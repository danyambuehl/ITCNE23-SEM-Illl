---
layout: default
title: CSpell
parent: Service
nav_order: 4
---

## CSpell

### Einführung

Ich habe `cspell` in dieses Projekt integriert, um sicherzustellen, dass die Dokumentation und der Code frei von Rechtschreibfehlern sind. `cspell` ist ein leistungsstarkes Werkzeug zur Rechtschreibprüfung, das speziell für Entwickler entwickelt wurde. Es kann in die Entwicklungsumgebung integriert werden, um Rechtschreibfehler in Echtzeit zu überprüfen.

### Kombination mit `pre-commit` [^1]

Durch die Integration in `pre-commit` kann ich sicherstellen, dass alle Commits automatisch auf Rechtschreibfehler überprüft werden, bevor sie in das Repository gelangen.

### Installation

Die Installation von `cspell` erfolgt über `npm`:

```bash
brew install node                   # Install Node.js inkl. npm
npm install -g cspell               # Installation von cspell
npm install -g @cspell/dict-de-de   # Installation des deutschen Wörterbuchs
cspell link add @cspell/dict-de-de  # Verknüpfen des deutschen Wörterbuchs
cspell link list                    # Überprüfen, ob das Wörterbuch korrekt verknüpft ist
cspell --config cspell.config.yaml docs/02_Planung/evaluation_code.md  # Überprüfen einer Datei mit Config File
cspell check cspell.config.yaml            # Überprüfen der Konfiguration dictionaries: de_de genau gleich wie id in cspell link list
```

### Einstellungen Dokument

In einem Dokument kann die Rechtschreibprüfung für eine Zeile oder einen Abschnitt deaktiviert werden:

```bash
// cspell:disable-line                   # Deaktivieren der Rechtschreibprüfung in einer Linie
<!-- /* cSpell:disable */ -->            # Deaktiviert die Rechtschreibprüfung
<!-- /* cSpell:enable */ -->             # Aktiviert die Rechtschreibprüfung
```
<!-- /* cSpell:disable */ -->

### Konfiguration [^2] [^3] [^4]

Die Konfiguration für `cspell` befindet sich im Repository in der Datei `cspell.config.yaml`.
Hier definiere ich die Wörterbücher, die verwendet werden sollen, sowie die Pfade, die ignoriert werden sollen.
Zusätzlich haben ich ein Muster definiert, um das `ß`-Symbol zu verbieten.
Mit dem Muster `markdown_code_block` können Codeblöcke in Markdown-Dateien ignoriert werden.

```yaml
---
# https://cspell.org/docs/dictionaries-custom/
dictionaryDefinitions:
  - name: words
    path: .config/dictionary.txt
    addWords: true
dictionaries:
  # Use `cspell-cli trace word` to check where a work is defined
  # https://github.com/streetsidesoftware/cspell-dicts/blob/main/dictionaries/de_DE/README.md
  - en_US
  - de_de
  - bash
  - words
  - html
  - python
ignorePaths:
  - cspell.config.yaml
  - pre-commit-config.yaml
  - _config.yml
  - "*.svg"

# Match code blocks in markdown files
patterns:
  - name: markdown_code_block
    pattern: |
      /(^\s*```[\s\S]*?^\s*```)/gm

# https://cspell.org/configuration/patterns/#patterns
languageSettings:
  - languageId: markdown
    ignoreRegExpList:
      - /ß/
      - markdown_code_block

```

### VSCode-Integration

In Visual Studio Code kann `cspell` über die Extension `Code Spell Checker` verwendet werden.
Dabei wird auch die Konfiguration aus der Datei `cspell.config.yaml` verwendet.
Und man die Rechtschreibprüfung direkt in der Entwicklungsumgebung durchführen ohne zuerst commit zu müssen.

## Quellen und Referenzen

[^1]:pre-commit [Retrieved from](https://pre-commit.com/)
[^2]:Konfiguration [Retrieved from](https://cspell.org/configuration/)
[^3]:CSpell German Dictionary [Retrieved from](https://github.com/streetsidesoftware/cspell-dicts/blob/main/dictionaries/de_DE/README.md)
[^4]:Pattern [Retrieved from](https://cspell.org/configuration/patterns/#patterns)
