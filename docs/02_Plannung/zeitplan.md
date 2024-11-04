---
layout: default
title: Zeitplan
parent: Planung
nav_order: 1
mermaid: true
---

## Zeitplan

Für die Planung und Durchführung des Projektes wurde ein fixer Zeitplan vorgegeben.
Der Zeitplan ist in der folgenden Tabelle dargestellt.

```mermaid
gantt
    title Projektplan ITCNE23-SEM-llll
    dateFormat  DD.MM.YY
    axisFormat  %d.%m.%Y

    %% Define the sections
    section Zwischenbesprechung
    Abgabe Einreichungsformular               : done, milestone,   meet,         21.10.24, 1d
    Einzelbesprechung Zwischenstand           : milestone,   meet,         08.11.24, 1d
    Einzelbesprechung Zwischenstand           : milestone,   meet,         02.12.24, 1d
    Einzelbesprechung Zwischenstand           : milestone,   meet,         06.01.25, 1d

    %% Define the Abschluss
    section Abschluss
    Abgabe der Arbeit / Schlusspräsentationen : crit, present,  29.01.25, 1d
    Notenvorschlag                              : milestone, grade_suggestion, 07.02.25, 1d
    Mitteilung der Noten                        : milestone, grades_announcement, 28.02.25, 1d
```

Um den detaillierten Zeitplan einzusehen, öffnen Sie bitte das Projektmanagement-Tool auf ([Github Project](https://github.com/users/danyambuehl/projects/4)). Dort finden Sie alle Informationen zur Projektplanung.

| Datum                  | Aktivität                                            | Wer         | An       |
|-----------------------|----------------------                                 | ------------|----      |
|21.10.2024             | Abgabe Einreichungsformular Semesterarbeit            | Studierende | Expert   |
|08.11.2024             | Einzelbesprechung Zwischenstand                       | Studierende | Expert   |
|02.12.2024             | Einzelbesprechung Zwischenstand                       | Studierende | Expert   |
|06.01.2025             | Einzelbesprechung Zwischenstand                       | Studierende | Expert   |
|29.01.2025             | Abgabe der Arbeit / Schlusspräsentationen             | Studierende |          |
|07.02.2025               | Notenvorschlag                                        | Expert      | Lehrgangsleiter |
|28.02.2025               | Mitteilung der Noten                                  | Lehrgangsleiter | Studierende |
