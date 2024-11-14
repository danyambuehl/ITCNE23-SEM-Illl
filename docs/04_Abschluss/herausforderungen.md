---
layout: default
title: Herausforderungen
parent: Abschluss
nav_order: 3
---

## Was waren die Herausforderungen?

### CSpell

Die patterns in der `cspell.config.yaml` Datei sind sehr mächtig und können sehr komplex sein.
Dabei habe ich viel Zeit damit verbracht, die richtigen patterns zu finden und zu testen.

[Regex tool](https://regex101.com/) können dabei sehr hilfreich sein.

```yaml
# Match code blocks in markdown files
patterns:
  - name: markdown_code_block
    pattern: |
      /(^\s*```[\s\S]*?^\s*```)/gm
```

### Troubleshooting SonarQube on Kubernetes PVC and PV

Ich habe viel Zeit damit verbracht, die Probleme mit den PVCs und PVs zu lösen.
Mir war nicht bewusst, dass die PVCs bei der Deinstallation des Helm-Charts nicht mit-gelöscht werden.
Dabei habe ich die Helm-Chart bei der ersten Installation noch nicht richtig konfiguriert und die StorageClass nicht gesetzt.
Da diese beim Löschen des Helm-Charts nicht gelöscht werden, wurden die alten PVCs beim erneuten Installieren des Helm-Charts verwendet.

```bash
# Get Pods Status NOT READY
kubectl get pods
NAME                     READY   STATUS     RESTARTS   AGE
sonarqube-postgresql-0   0/1     Pending    0          4m26s
sonarqube-sonarqube-0    0/1     Init:0/3   0          4m26s

# Get PVC Status Status Pending
$ kubectl get pvc -n sonarqube
NAME                          STATUS    VOLUME   CAPACITY   ACCESS MODES   STORAGECLASS   VOLUMEATTRIBUTESCLASS   AGE
data-sonarqube-postgresql-0   Pending                                                     <unset>                 10m

# Describe PVC Status StorageClass not set
$ kubectl describe pvc data-sonarqube-postgresql-0 -n sonarqube
Name:          data-sonarqube-postgresql-0
Namespace:     sonarqube
StorageClass:
Status:        Pending
Volume:
Labels:        app.kubernetes.io/instance=sonarqube
               app.kubernetes.io/name=postgresql
               role=primary
Annotations:   <none>
Finalizers:    [kubernetes.io/pvc-protection]
Capacity:
Access Modes:
VolumeMode:    Filesystem
Used By:       sonarqube-postgresql-0
Events:
  Type    Reason         Age                 From                         Message
  ----    ------         ----                ----                         -------
  Normal  FailedBinding  30s (x42 over 10m)  persistentvolume-controller  no persistent volumes available for this claim and no storage class is set
```

### Pipeline Unternehmen Beschraenkungen

Ich hatte immer wieder Probleme wegen internen vorschriften und Einschränkungen.
Dabei ist das vorgehen leider nicht immer klar Dokumentiert und ich habe viel Zeit damit verbracht, einfach auszuprobieren.

Nur Image von Artifactory sind erlaubt und dort nicht oder sehr schlecht dokumentiert.

```bash
ERROR: The "python:3.9-slim" image is not present on list of allowed images:
```

Nur Packages von Internen Artifactory URL sind erlaubt und dies ist nicht klar Dokumentiert.
Die Packages sind im Artifactory nur schwer zu finden.

```bash
pip3 config set global.index-url https://artifactory.swisscom.com/artifactory/api/pypi/pypi-remote/simple
```
