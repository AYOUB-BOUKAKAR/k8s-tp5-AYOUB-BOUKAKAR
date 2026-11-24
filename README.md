# TP 5 Kubernetes - Configuration et donnees persistantes

ENSAH - GL - 2026/2027 - Ayoub Boukakar

Cluster kind tp-k8s (3 noeuds).

## Contenu
- web-config.yaml, web-config-prod.yaml, web-config-dev2.yaml : ConfigMaps (dev, prod, dev2)
- web.yaml : Deployment nginx lisant la ConfigMap (variable APP_ENV + fichier index.html)
- postgres.yaml : Service headless + StatefulSet PostgreSQL 17 avec volumeClaimTemplates
- quota.yaml : ResourceQuota (4 pods max)
- Compte_rendu_TP5_Kubernetes_Ayoub_Boukakar.pdf : compte rendu complet

## Secret
Le Secret db-cred est cree uniquement par commande et volontairement absent du depot.

## Ordre d'application
kubectl apply -f web-config.yaml -f web.yaml -n dev
kubectl create secret generic db-cred ... -n dev   (voir le compte rendu)
kubectl apply -f postgres.yaml -n dev
kubectl apply -f quota.yaml -n prod
