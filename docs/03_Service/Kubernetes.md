---
layout: default
title: SonarQube Kubernetes
parent: Service
nav_order: 4
---

## SonarQube Kubernetes [^1]

SonarQube ist ein Open-Source-Tool zur statischen Codeanalyse, das Entwicklern hilft, die Qualität ihres Codes zu verbessern. Es bietet eine Vielzahl von Funktionen, darunter die Überprüfung von Code auf Sicherheitslücken, Bugs und Code-Stilprobleme.

Es wurde auf einen bestehenden Kubernetes-Cluster installiert.
Im endeffekt wurden Helm Charts verwendet um SonarQube auf dem Kubernetes Cluster zu installieren.

## SonarQube mit Helm installieren [^2] [^3]

SonarQube installation mit letzter stabiler Version, Ingress aktivieren und Storage Class setzen.

```bash
export KUBECONFIG=/etc/rancher/k3s/k3s.yaml         # Set Kube config for Helm
helm repo add sonarqube https://SonarSource.github.io/helm-chart-sonarqube
helm repo update
kubectl create namespace sonarqube
helm upgrade --install -n sonarqube --version '~8' sonarqube sonarqube/sonarqube \
  --set ingress-nginx.enabled=true \
  --set postgresql.persistence.storageClass="local-path"
```

## Ingress Erstellen

Es muss noch ein Ingress erstellt werden, um auf SonarQube zuzugreifen.

```bash
kubectl get ingress
No resources found in sonarqube namespace.  # No Ingress found
```

```yaml
#ingress.yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: sonarqube-ingress
  namespace: sonarqube
  annotations:
    nginx.ingress.kubernetes.io/rewrite-target: /
spec:
  rules:
    - host: smccrz1-vans901.mccip-test.local
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: sonarqube-sonarqube
                port:
                  number: 9000
```

## Troubleshooting SonarQube on Kubernetes PVC and PV

Weitere Informationen zu Herausforderungen und Lösungen [Herausforderungen](../04_Abschluss/herausforderungen.md).

## Helm Charts commands

```bash
helm list -a
helm delete sonarqube
helm get values sonarqube
helm status sonarqube
```

## Quellen und Referenzen

[^1]:SonarQube GitHub [Retrieved from](https://github.com/SonarSource/helm-chart-sonarqube/tree/master/charts/sonarqube#installing-the-sonarqube-99-lta-chart)
[^2]:SonarQube Helm Chart [Retrieved from](https://docs.sonarsource.com/sonarqube/latest/setup-and-upgrade/deploy-on-kubernetes/server/installing-helm-chart/)
[^3]:Artifact Hub [Retrieved from](https://artifacthub.io/packages/helm/sonarqube/sonarqube#production-use-case)
