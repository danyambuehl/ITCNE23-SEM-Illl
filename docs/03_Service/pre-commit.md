---
layout: default
title: Pre-Commit
parent: Service
nav_order: 3
---

## Pre-Commit

### Einführung

Ich habe `pre-commit` in dieses Projekt integriert, um sicherzustellen, dass alle Commits bestimmten Qualitätsstandards entsprechen. `pre-commit` ist ein Framework, das es ermöglicht, Hooks zu definieren, die vor jedem Commit ausgeführt werden. Diese Hooks können verschiedene Prüfungen und Formatierungen durchführen, um die Codequalität zu verbessern.

### Kombination mit `cspell` [^1]

Durch die Integration von `cspell` in `pre-commit` kann ich sicherstellen, dass alle Commits automatisch auf Rechtschreibfehler überprüft werden, bevor sie in das Repository gelangen.

### Konfiguration

Die Konfiguration für `pre-commit` befindet sich im Repository in der Datei `.pre-commit-config.yaml`.
Hier definiere ich die Hooks, die vor jedem Commit ausgeführt werden sollen.

```yaml
---
# "pre-commit run --files example.yml" to check a file
ci:
  # format compatible with commit lint
  autoupdate_commit_msg: "chore: pre-commit autoupdate"
  autoupdate_schedule: monthly
  autofix_commit_msg: |
    chore: auto fixes from pre-commit.com hooks
# https://cspell.org/docs/getting-started/
#default_language_version:
#    python: python3.11
repos:
  # Self defined hook to replace ss with ss
  - repo: local
    hooks:
      - id: replace-ss
        name: Replace ss with ss
        entry: sed -i 's/ss/ss/g'    # s=substitute, g=global(not just first) - Regular Expression Tool https://regex101.com/
        language: system
        exclude: ^(\.pre-commit-config|docs/03_Service/CSpell)$   # Exclude these files
  # Hook for spell checking with cspell config file cspell.config.yaml
  - repo: https://github.com/streetsidesoftware/cspell-cli
    rev: v8.15.2
    hooks:
      - id: cspell
        args: [--relative, --no-progress, --no-summary]
        name: Spell check with cspell
        # files: \.(md|txt|py|js|ts|html|css|json)$
  # Pre-commit hooks for checking code style
  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v5.0.0
    hooks:
      - id: trailing-whitespace           # Trims trailing whitespace
      - id: end-of-file-fixer             # Ensure files end with a newline
      - id: check-case-conflict           # Check for files with names that differ only in case
      - id: check-illegal-windows-names   # Check for files with illegal windows filenames
      - id: check-symlinks                # Check for symlinks which are broken
      - id: check-yaml                    # Check yaml files for syntax errors
  # Check if commit messages are formatted correctly
  - repo: https://github.com/Woile/commitizen
    rev: v3.30.0
    hooks:
      - id: commitizen
        stages: [commit-msg]
  #  exclude line from yamllint with following command on the end -> # yamllint disable-line
  - repo: https://github.com/adrienverge/yamllint
    rev: v1.26.3
    hooks:
      - id: yamllint
        args:
          [
            "-d {extends: relaxed, rules: {line-length: {max: 120}}}",
            "-s",
          ]
        files: \.(yaml|yml)$
        exclude: Playbooks_OLD/.*
```

### Verwendung

Um sicherzustellen, dass `pre-commit` vor jedem Commit ausgeführt wird, müssen Sie `pre-commit` installieren und die Hooks aktivieren:

1. Installieren Sie `pre-commit`:

   ```sh
   /c/Users/TAAAMDA6/AppData/Local/Microsoft/WindowsApps/python3.11.exe -m venv myenv   # Path to python 3.11
   source myenv/Scripts/activate      # Activate the virtual environment
   pip install pre-commit             # Install pre-commit

   or

   brew install pre-commit
   pre-commit --version
   ```

2. Führen Sie die Hooks manuell aus (optional):

   ```sh
   pre-commit run --all-files
   pre-commit run --files example.yml
   ```

### VSCode-Integration

In Visual Studio Code kann `pre-commit` über die Extension `Prettier - Code formatter` und andere ähnliche Extensions verwendet werden. Dabei wird auch die Konfiguration aus der Datei `.pre-commit-config.yaml` verwendet.

## Quellen und Referenzen

[^1]:pre-commit [Retrieved from](https://pre-commit.com/)
