---
layout: default
title: Evaluation
parent: Planung
nav_order: 6
---

## Evaluation Open-Source-Lösung für Codequalitätsprüfungen

Die Wahl der richtigen Open-Source-Lösung für Codequalitätsprüfungen ist von grosser Bedeutung. In diesem Abschnitt werde ich die Vor- und Nachteile von drei Open-Source-Lösungen vergleichen, um eine nachvollziehbare Entscheidung für die beste Lösung für mein Projekt zu treffen. Am Ende werde ich eine Entscheidungsmatrix erstellen, um die verschiedenen Kriterien zu bewerten und eine endgültige Entscheidung zu treffen.

## 1. SonarQube [^1]

### Features

- Unterstützt mehrere Programmiersprachen.
- Statische Code-Analyse zur Erkennung von Code-Problemen, Bugs und Sicherheitslücken.
- Integration in CI/CD-Pipelines.
- Detaillierte Dashboards und Berichte.
- Verfügbar als Container: SonarQube Docker.

### Vorteile

- Umfassende Regelwerke für Codequalität und Sicherheit.
- Aktive Community und regelmässige Updates.
- Einfache Integration in bestehende Entwicklungsabläufe.

### Nachteile

- Benötigt Einrichtung und Wartung des SonarQube-Servers.
- Einige erweiterte Funktionen sind nur in der kostenpflichtigen Enterprise-Version verfügbar.

## 2. ESLint [^2]

### Features

- ESLint analysiert JavaScript und andere unterstützte Sprachen auf Code-Qualitätsprobleme und potenzielle Fehler.
- Anpassbare Regelwerke zur Durchsetzung von Coding-Standards.
- Unterstützt die Integration in CI/CD-Pipelines und verschiedene Entwicklungsumgebungen.
- Einige Fehler können automatisch behoben werden.

### Vorteile

- Hochgradig konfigurierbar und erweiterbar durch Plugins und benutzerdefinierte Regeln.
- Grosse Benutzerbasis und aktive Community mit zahlreichen verfügbaren Plugins.
- Unterstützung für Texteditoren wie VSCode, Sublime Text und andere.

### Nachteile

- Die Konfiguration kann für neue Benutzer komplex sein.
- Hauptsächlich auf JavaScript und verwandte Technologien beschränkt.

## 3. Pylint [^3]

### Features

- Pylint analysiert Python-Code auf Code-Qualitätsprobleme, potenzielle Fehler.
- Anpassbare Regelwerke zur Durchsetzung von Coding-Standards und Best Practices.
- Unterstützt die Integration in CI/CD-Pipelines und verschiedene Entwicklungsumgebungen.
- Generiert umfassende Berichte über gefundene Probleme und Vorschläge zur Verbesserung.

### Vorteile

- Erkennt eine Vielzahl von Problemen, einschliesslich, potenziellen Fehlern und Sicherheitsproblemen.
- Hochgradig konfigurierbar und erweiterbar durch benutzerdefinierte Regeln und Plugins.
- Grosse Benutzerbasis und aktive Community, die kontinuierlich zur Verbesserung und Erweiterung beiträgt.

### Nachteile

- Die Konfiguration kann für neue Benutzer komplex und zeitaufwendig sein.
- Wenig Unterstützung für andere Sprachen als Python.
- Keine Integration mit Ansible-Playbooks.

## Vergleich [^5] [^6]

Um die Lösungen zu vergleichen, werde ich die folgenden Kriterien verwenden:

### Anbindung an Pipeline

Die Lösung muss eine einfache Integration in eine CI/CD-Pipeline ermöglichen.

### Verfügbarkeit als Container

Die Lösung muss als Docker-Container verfügbar sein, um eine einfache Bereitstellung zu gewährleisten.

### Unterstützte Sprachen

Die Lösung sollte möglichst viele Programmiersprachen unterstützen.

### Benutzerfreundlichkeit

Die Lösung sollte einfach zu konfigurieren und zu verwenden sein.

### Community und Support

Die Lösung sollte eine aktive Community und guten Support bieten.

## Entscheidungsmatrix [^4]

Um die drei Lösungen zu bewerten, erstelle ich eine Entscheidungsmatrix mit den oben genannten Kriterien und gewichte sie entsprechend ihrer Bedeutung für mein Projekt.

| **Lösung**  (1-5)  | **Anbindung an Pipeline**    | **Verfügbarkeit als Container**  | **Unterstützte Sprachen** | **Benutzerfreundlichkeit**  | **Community und Support**      | **Gesamtpunktzahl**  |
|------------------- |----------------------------- |--------------------------------- |-------------------------- |---------------------------- |------------------------------- |---------------------- |
| Gewichtung         | 0.3                          | 0.2                             | 0.2                       | 0.2                         | 0.1                           |                      |
| SonarQube          | 5                            | 5                               | 5                         | 4                           | 5                             | **4.7**              |
| ESLint             | 4                            | 4                               | 3                         | 5                           | 4                             | **4.0**              |
| Pylint             | 3                            | 3                               | 2                         | 4                           | 3                             | **3.0**              |

## Fazit

Alle drei Lösungen haben ihre Vor- und Nachteile und eignen sich für unterschiedliche Anwendungsfälle. Anhand der Entscheidungsmatrix lässt sich jedoch feststellen, dass SonarQube insgesamt besser abschneidet und daher die beste Wahl für mein Projekt ist.
Spezifisch für die Anwendung in einem Kubernetes-Cluster und die Integration in eine CI/CD-Pipeline ist SonarQube die beste Lösung.

### Quellen

[^1]: SonarQube [Retrieved from](https://www.SonarQube.org/)
[^2]: ESLint [Retrieved from](https://eslint.org/)
[^3]: Pylint [Retrieved from](https://pylint.pycqa.org/)
[^4]: Entscheidungsmatrix [Retrieved from](https://de.wikipedia.org/wiki/Entscheidungsmatrix)
[^5]: ESLint vs SonarQube [Retrieved from](https://stackshare.io/stackups/eslint-vs-SonarQube)
[^6]: Pylint vs SonarQube [Retrieved from](https://stackshare.io/stackups/pylint-vs-SonarQube)
