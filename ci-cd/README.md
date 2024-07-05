# Orchestration et Automatisation avec Jenkins

## Description
Ce dossier contient les fichiers nécessaires pour déployer et configurer Jenkins dans le cluster Kubernetes. Jenkins est utilisé pour automatiser les processus de développement, de test et de déploiement (CI/CD) des applications.

## Instructions

### 1. Installation de Jenkins

1. **Créer un Persistent Volume Claim pour Jenkins** :
    - Utiliser le fichier `jenkins-pvc.yaml` pour créer un volume persistant où Jenkins stockera ses données.
    ```bash
    kubectl apply -f ci-cd/jenkins-pvc.yaml --namespace ci-cd-tools
    ```

2. **Déployer Jenkins** :
    - Utiliser le fichier `jenkins-deployment.yaml` pour déployer Jenkins dans le namespace `ci-cd-tools`.
    ```bash
    kubectl apply -f ci-cd/jenkins-deployment.yaml --namespace ci-cd-tools
    ```

3. **Exposer Jenkins avec un service** :
    - Utiliser le fichier `jenkins-service.yaml` pour créer un service qui expose Jenkins. Cela permet d'accéder à Jenkins depuis l'extérieur du cluster.
    ```bash
    kubectl apply -f ci-cd/jenkins-service.yaml --namespace ci-cd-tools
    ```

4. **Configurer Jenkins** :
    - Accédez à Jenkins via l'URL fournie par le service exposé (à l'adresse IP ou au nom de domaine attribué).
    - Installez les plugins nécessaires, tels que ceux pour Kubernetes et Git.
    - Configurez Jenkins pour se connecter au cluster Kubernetes et gérer les déploiements.

### 2. Configuration des Pipelines Jenkins

1. **Créer les Pipelines** :
    - Utilisez les fichiers YAML dans le sous-dossier `pipelines` pour définir les pipelines Jenkins pour chaque environnement.
    - Vous pouvez créer les pipelines via l'interface Jenkins en utilisant les fichiers `dev-pipeline.yaml`, `test-pipeline.yaml`, et `prod-pipeline.yaml`.

## Fichiers

- `jenkins-deployment.yaml` : Déploiement de Jenkins dans Kubernetes.
- `jenkins-service.yaml` : Service Kubernetes pour exposer Jenkins.
- `jenkins-pvc.yaml` : Persistent Volume Claim pour stocker les données de Jenkins.
- `pipelines/` :
    - `dev-pipeline.yaml` : Pipeline Jenkins pour l'environnement de développement.
    - `test-pipeline.yaml` : Pipeline Jenkins pour l'environnement de test.
    - `prod-pipeline.yaml` : Pipeline Jenkins pour l'environnement de production.

## Résultats Attendus

- Jenkins doit être correctement déployé et accessible.
- Les pipelines doivent être configurés pour automatiser les processus CI/CD pour les environnements de développement, de test, et de production.
