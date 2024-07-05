# Déploiement et Gestion des Applications

## Description
Ce dossier contient les fichiers nécessaires pour déployer et gérer WordPress et MySQL dans les environnements de développement, test, et production. Chaque application dispose de son propre dossier avec les configurations de déploiement, de service et de volumes persistants.

## Instructions

### 1. Déploiement de WordPress et MySQL

#### Déployer WordPress

1. Appliquez les Persistent Volume Claims (PVC) pour WordPress :

```bash
kubectl apply -f wordpress/pvc.yaml
