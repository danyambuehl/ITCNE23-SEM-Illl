---
layout: default             #layout: minimal
title: Smart Ziele
nav_order: 2
parent: Planung
# Referenz nachtragen
# Weitere vorteile einer REST-API
---

## SMART-Ziele [^1]

<img src="../img/smart_ziele.webp" alt="Smart Ziele" style="width:75%;"/> [^2]

## Was sind SMART-Ziele?

SMART-Ziele sind spezifische, messbare, erreichbare, relevante und zeitgebundene Ziele, die dazu beitragen, den Erfolg eines Projekts zu definieren und zu messen.
Sie sind ein bewährtes Instrument, um sicherzustellen, dass die Ziele klar definiert sind und die Erwartungen erfüllt werden.

| **Spezifisch**               | **Messbar**              | **Erreichbar**      | **Relevant**              | **Zeitgebunden**      |
|------------------------------|--------------------------|---------------------|---------------            | --------------        |
| Klar definierte und präzise  | Quantifizierbare Aspekte | Realistische  Ziele | Bedeutung für das Projekt | klaren Zeitrahmens    |

### Implementierung einer Open-Source-Lösung für Codequalitätsprüfungen

Innerhalb des ersten Sprints soll eine Open-Source-Lösung auf einem Kubernetes-Cluster installiert und eingerichtet werden, um eine Überprüfung und Analyse der Codequalität von Ansible-Playbooks auf einem Git Repository zu ermöglichen.

### Anbindung an das Git-Repository und Einrichtung einer CI/CD-Pipeline

Bis zum Ende des zweiten Sprints wird eine Pipeline entwickelt, welche die Ansible-Playbooks im Git-Repository überprüft. Bei jedem neuen Merge Request in den «Main» Branch wird diese Pipeline automatisierte Qualitätschecks durchführen und die Ergebnisse dokumentieren.

### Automatisierte Syntax-Überprüfung und Ergebnispräsentation

Das System muss bis zum letzten Sprint eine Funktion integrieren, die die YAML- und Ansible-Syntax der Playbooks automatisiert überprüft und die Ergebnisse in einer Benutzeroberfläche darstellt.

### Integration eines Formatierungstools für YAML-Dateien

Bis zum letzten Sprint, soll ein Tool zur Automatisierung der Formatierung von YAML-Dateien implementiert und in die Entwicklungsumgebung integriert werden, um den Entwicklern die Einhaltung festgelegter Formatierungsstandards zu erleichtern.

### Quellen

[^1]: SMART-Ziele richtig formulieren [Retrieved from](https://asana.com/de/resources/smart-goals)
[^2]: Image depicting the concept of SMART goals [Generated by AI, OpenAI's DALL-E](https://openai.com/index/dall-e-2/)