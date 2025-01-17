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
| `pre-commit`| Überprüfen der pre-commit Autokorrektur | Whitespace, end of file werden automatisch korrigiert  | OK | [Screenshot](../img/testing/pre_commit.png) |
| `pre-commit`| Überprüfen der pre-commit YAML Validierung | YAML lint gibt Warnung  | OK | [Screenshot](../img/testing/pre_commit.png) |
| `pre-commit` | Überprüfen des pre-commit YAML Validierung | YAML lint gibt Warnung "Line to Long" | OK | [Screenshot](../img/testing/yaml-lint.png) |
| `cSpell`| Überprüfen der cSpell Rechtschreibung | Rechtschreibfehler werden angezeigt  | OK | [Screenshot](../img/testing/cSpell.png) |
| `ss Replacement` | Überprüfen der ss Replacement | ss wird durch ss ersetzt  | OK | [Screenshot](../img/testing/ss_replace.png) |

### Pipeline Validierung

Die Pipeline wird auf GitLab CI/CD zusätzlich nach Best Practice vorgaben nochmals validiert, um die Konsistenz sicherzustellen.

```yaml
# Validation that the pipeline (https://docs.gitlab.com/ee/ci/components/#test-the-component)
ensure-jobs-added:
  stage: validate
  image: remote-docker.artifactory.swisscom.com/badouralix/curl-jq:latest
  variables:
    GIT_STRATEGY: none
  dependencies: []
  script:
    - |
      expectedJobs="sonar"
      route="${CI_API_V4_URL}/projects/$CI_PROJECT_ID/pipelines/$CI_PIPELINE_ID/jobs"
      # JobToken seems not allowed to download own child pipeline jobs (404), therefore using an api-token instead
      # curl -sS -H "JOB-TOKEN: $CI_JOB_TOKEN" $route -o jobs.json -w "%{http_code}"
      httpCode=$(curl -sS -H "Authorization: Bearer $GITLAB_TEST_TOKEN" $route -o jobs.json -w "%{http_code}")
      if [ "$httpCode" != "200" ]; then
        echo "Failed to load jobs from $route ($httpCode)"
        exit 1
      fi
      for job in $expectedJobs; do
        echo "Validate job: $job"
        count=`jq --arg job "$job" 'map(select(.name | contains($job))) | length' jobs.json`
        if [ "$count" != "1" ]; then
          echo "$job is missing"
          exit 1;
        fi
        status=`jq -r --arg job "$job" 'map(select(.name == $job)) | map(.status) | .[0]' jobs.json`
        if [ "$status" != "success" ]; then
          echo "$job was not successful"
          exit 1;
        fi
      done
```

### SonarQube Code Qualität

Hier eine Übersicht die Code Qualität des Gesamten Code des Repos

[SonarQube Übersicht](../img/testing/sonarqube_overview.png)

Die verschiedenen Issues die gefunden wurden.

[SonarQube Issues](../img/testing/sonarqube_issue.png)

Ein Beispiel eines gefundenen Issues.

[SonarQube Issue](../img/testing/sonarqube_issue_detail.png)
