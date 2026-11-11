# Plateforme Kubernetes multi-environnements (dev / test / prod)

Projet d'infrastructure DevOps : mise en place, sur Minikube, de trois environnements isolés (development, testing, production) avec quotas de ressources, déploiement d'applications (WordPress et MySQL) et d'un serveur Jenkins pour le CI/CD.

## Contenu du dépôt

**environments/** : namespaces development, testing et production, avec ResourceQuotas et LimitRanges propres à chaque environnement.

**applications/** : manifestes Kubernetes (Deployment, Service, PVC) pour WordPress et MySQL.

**ci-cd/** : Jenkins (Deployment, Service, PVC) dans le namespace ci-cd-tools, et trois pipelines (dev, test, prod).

**cluster-configuration/** : configuration Minikube et trois profils de noeuds (frontend, backend, devops).

**monitoring/, security/, stress-testing/** : dossiers réservés, pas encore réalisés.

## État d'avancement

| Partie | État |
|---|---|
| Cluster Minikube et noeuds | Manifestes écrits |
| Environnements isolés (namespaces, quotas, limites) | Manifestes écrits |
| Applications WordPress et MySQL | Manifestes écrits |
| Jenkins dans le cluster | Manifestes écrits |
| Pipelines dev / test / prod | Squelettes : étapes Build, Test et Deploy à compléter |
| Monitoring | À faire |
| Sécurité | À faire |
| Tests de charge | À faire |

## Démarrage rapide

Prérequis : Minikube et kubectl installés.

```bash
minikube start
kubectl apply -f environments/namespaces.yaml
kubectl apply -f ci-cd/namespaces/ci-cd-tools.yaml
kubectl apply -f ci-cd/jenkins-pvc.yaml --namespace ci-cd-tools
kubectl apply -f ci-cd/jenkins-deployment.yaml --namespace ci-cd-tools
kubectl apply -f ci-cd/jenkins-service.yaml --namespace ci-cd-tools
```

Le détail de chaque partie se trouve dans le README de son dossier (ci-cd, environments, applications, cluster-configuration).

## Prochaines étapes

Compléter les pipelines Jenkins (build, tests, déploiement réels) et les nommer en Jenkinsfile.

Remplacer l'image bitnami/wordpress:latest par une version fixée.

Ajouter le monitoring, la sécurité (secrets, politiques réseau) et les tests de charge.

Valider l'ensemble sur un cluster Minikube à jour et noter les résultats ici.
