---
layout: default
title: Herausforderungen
parent: Abschluss
nav_order: 3
---

## Was waren die Herausforderungen?

### CSpell

Replace ss with ss
Replace Abschluss with Abschluss

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
