---
layout: default
title: Testing
parent: Service
nav_order: 6
---

## Manuelle Tests

Hier werden einige Manuelle Tests durchgeführt um die Funktionen zu überprüfen.

![Testing](../img/testing.png)

| Beschreibung | Test Schritt | Erwartetes Resultat | Status | Screen |
| ---         | ---       | ---             | ---    |  ---   |
| `pre-commit`| Überprüfen der pre-commit Autokorrektur | Whitespace, end of file werden automatisch korrigiert  | :white_check_mark: | [Screenshot](../img/testing/pre_commit.png) |
| `pre-commit`| Überprüfen der pre-commit YAML Validierung | YAML lint gibt Warnung  | :white_check_mark: | [Screenshot](../img/testing/pre_commit.png) |
| `pre-commit` | Überprüfen des pre-commit YAML Validierung | YAML lint gibt Warnung "Line to Long" | :white_check_mark: | [Screenshot](../img/testing/yaml-lint.png) |
| `cSpell`| Überprüfen der cSpell Rechtschreibung | Rechtschreibfehler werden angezeigt  | :white_check_mark: | [Screenshot](../img/testing/cSpell.png) |
| `ss Replacement` | Überprüfen der ss Replacement | ss wird durch ss ersetzt  | :white_check_mark: | [Screenshot](../img/testing/ss_replace.png) |


## Automatisches Testing

![Testing](../img/testing2.png)

Hier werden einige Automatische Tests durchgeführt um die Funktionen zu überprüfen.

### Pipeline Testing

### Pytest Testing

### Pytest Coverage Testing
