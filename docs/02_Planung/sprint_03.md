---
layout: default
title: Sprint 03
parent: Planung
nav_order: 12
---

## Sprint 03

| Datum       | Aktivität                                         |
|-------------|---------------------------------------------------|
| 21.10.2024  | Abgabe und Besprechung Einreichungsformular Semesterarbeit  |
| 08.11.2024  | Ergebnis 1. Sprint                                |
| 02.12.2024  | Ergebnis 2. Sprint                                |
| 06.01.2025  | Ergebnis 3. Sprint                                |
| 29.01.2025  | Abgabe der Arbeit / Abnahme                       |

```mermaid
gantt
    title Projektplan ITCNE24-SEM-llll
    dateFormat  DD.MM.YY
    axisFormat  %d.%m.%Y

    %% Define the sections
    section Zwischenbesprechung
    Abgabe Einreichungsformular               : done, milestone,   meet,         21.10.24, 1d
    Einzelbesprechung Zwischenstand           : done, milestone,   meet,         08.11.24, 1d
    Einzelbesprechung Zwischenstand           : done, milestone,   meet,         02.12.24, 1d
    Einzelbesprechung Zwischenstand           : milestone,   meet,         06.01.25, 1d

    %% Define the Sprints
    section Sprints
    Sprint 01                                   : done, sprint,  28.10.24, 12d
    Sprint 02                                   : done, sprint,  09.11.24, 24d
    Sprint 03                                   : active, sprint,  03.12.24, 35d
    Nacharbeiten                                : sprint,  07.01.25, 20d
    Abgabe der Arbeit / Schlusspräsentationen (online) : crit, present,  29.01.25, 1d
```

### Sprint Planning

Folgende Tasks wurden im Sprint 03 geplant:

![Sprint Planning](../img/sprint_03_2.png)

### Sprint Review

Folgende Tasks wurden im Sprint 03 bearbeitet:

![Sprint Planning](../img/sprint_03_ende.png)

### Sprint Retrospektive

#### GitLab CI/CD

Zunächst habe ich sehr komplexe Pipelines erstellt, die ich nach Tests und besserem Verständnis vereinfachen konnte. Dadurch habe ich begonnen, die Pipeline-Templates unseres Unternehmens zu verstehen und anzuwenden. Zudem habe ich die Möglichkeit entdeckt, Sub-Pipelines zu nutzen, um die Struktur der Pipelines weiter zu optimieren.

#### Pre-Commit Hooks

Ich habe viel Zeit investiert, um verschiedene Pre-Commit Hooks zu testen und zu implementieren. Dabei habe ich festgestellt, dass Pre-Commit Hooks sehr effizient sind, um die Codequalität zu verbessern. Allerdings kann die anfängliche Einrichtung sehr zeitaufwendig sein.
Ich verwende nun Pre-Commit Hooks in all meinen Projekten, um die Codequalität und Dokumentation zu verbessern.

#### CSpell

CSpell ist ein sehr nützliches Tool, um Rechtschreibfehler in Markdown-Dateien zu finden. Ich habe es in meine Pre-Commit Hooks integriert, um Rechtschreibfehler in meinen Dokumenten zu vermeiden.

**Keep** Was soll beibehalten werden?

- Templates nutzen
- Sub-Pipelines nutzen

**Drop** Mit was soll ich aufhören?

- Zu genau ins Detail gehen
- Zeit mit der Konfiguration von CSpell und Pre-Commit Hooks investieren

**Try** Was soll ich im nächsten Sprint ausprobieren?

- Weitere Hooks ausprobieren
- Pipeline-Templates entdecken
