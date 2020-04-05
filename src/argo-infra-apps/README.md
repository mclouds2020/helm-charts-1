# `infra-apps` via Argo CD
## Install Argo CD
You need to have Argo CD installed with its CRDs/APIs functional:

1. `kubectl create ns argocd`
1. `helm install argocd argo/argo-cd -n argocd --values argo-00x.values.yaml`
1. `kubectl create secret generic github-ssh-key --from-file=sshPrivateKey=<path-to-ssh-private-key-file>`
1. `kubectl port-forward <argocd-server-pod-id> 8080`
1. Browse to http://localhost:8080 and login with username `admin` and password `<argocd-server-pod-id>`

Note that GitHub SSO won't work until Argo CD ingress is functional.

## Install `infra-apps`
```
export AWS_SECRET_ACCESS_KEY=<aws-secret-access-key>
helm install infra-apps-test . -n argocd \
  --set external_dns.spec.aws.credentials.secretKey=$AWS_SECRET_ACCESS_KEY
```

## Apply Additional CRDs
```
kubectl apply --validate=false \
  -f https://raw.githubusercontent.com/jetstack/cert-manager/release-0.12/deploy/manifests/00-crds.yaml
```

## Create Secrets
```
kubectl create secret generic route53-credentials \
  --from-literal=route53-credentials=$AWS_SECRET_ACCESS_KEY -n cert-manager

kubectl create secret generic gcp-velero-sa-key \
  --from-file=cloud=/Users/muradkurejo/Downloads/<path-to-velero-service-account-key> -n velero
```