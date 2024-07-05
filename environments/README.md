# Configuration des Environnements de Développement, Test, et Production

## Description
Ce dossier contient les fichiers nécessaires pour configurer des environnements isolés pour le développement, les tests, et la production dans un cluster Kubernetes. Chaque environnement est configuré avec des quotas de ressources et des policies de sécurité spécifiques.

## Instructions

### 1. Créer les Namespaces
Pour créer les namespaces `Development`, `Testing`, et `Production`, utilisez le fichier `namespaces.yaml` :

```bash
kubectl apply -f namespaces.yaml
