---
layout: default
title: Three Ways
parent: Planung
nav_order: 4
---

## Three Ways [^1] [^2]

Dieses Projekt implementiert die "Three Ways of DevOps":

1. **Flow**: Automatisierte Pipeline für kontinuierliche Codequalitätsprüfungen
   - Ziel ist es, den gesamten Entwicklungsprozess zu optimieren und Engpässe zu vermeiden.
   - Durch die Automatisierung von Build-, Test- und Deployment-Prozessen wird ein schneller und reibungsloser Fluss von der Entwicklung bis zur Produktion gewährleistet.
   - Die integration von pre-commit Hooks ermöglicht es, dem Entwickler Aufgaben abzunehmen.
   - Sicherstellung der Sicherheit des Codes durch automatisierte Tests und Codeanalysen.

2. **Feedback**: Sofortige Validierung und Berichterstattung von Codequalitätsproblemen
   - Schnelles Feedback ermöglicht es Entwicklern, Fehler frühzeitig zu erkennen und zu beheben.
   - Automatisierte Tests und Codeanalysen liefern kontinuierlich Rückmeldungen zur Codequalität und helfen, die Stabilität und Sicherheit des Codes zu gewährleisten.
   - Durch die Integration von SonarQube wird die Qualität des Codes kontinuierlich überwacht und verbessert.
   - Die integration von pre-commit gibt dem Entwickler sofortiges Feedback.
   - CSpell gibt dem Entwickler sofortiges Feedback über Rechtschreibfehler.
   - Automatisierte testings mit Ansible-lint und yaml-lint.

3. **Kontinuierliches Lernen und Experimentieren**: Standardisierung und Dokumentation von Best Practices
   - Durch die Dokumentation und Standardisierung von Prozessen und Best Practices wird das Wissen im Team geteilt und die Qualität der Arbeit kontinuierlich verbessert.
   - Die Integration von SonarQube und pre-commit Hooks ermöglicht es, Best Practices zu dokumentieren und zu standardisieren.
   - SonarQube kann einfach für weitere Projekte wiederverwendet werden.
   - pre-commit Hooks können gut in anderen Projekten ergänzt werden.

## Quellen und Referenzen

[^1]:The Three Ways: The Principles Underpinning DevOps [Retrieved from](https://itrevolution.com/articles/the-three-ways-principles-underpinning-devops/)
[^2]:GitLab the three ways [Retrieved from](https://about.gitlab.com/blog/2022/06/15/gitlab-and-the-three-ways-of-devops/)
