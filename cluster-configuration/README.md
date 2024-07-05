# Cluster Configuration

## Description
Ce dossier contient les fichiers nécessaires pour configurer un cluster Minikube multi-nœuds. Les configurations spécifiques pour chaque nœud sont incluses dans le sous-dossier `node-configurations`.

## Instructions

### 1. Initialiser Minikube
Pour initialiser le cluster Minikube avec trois nœuds, utilisez la commande suivante :

```bash
minikube start --nodes 3 --cni=calico
