# Argo config
This is used to install the ArgoCD gitops tool. 

## Install Argo
Let's install ArgoCD on argocd namespace.

```bash
helm repo add argo-official https://argoproj.github.io/argo-helm
helm pull argo-official/argo-cd -d ../      # Download the last  tar.gz
helm repo index ../                         # Update index
```
Now, commit and merge. You must do this, else, you won't be able to add this repo as a helm chart repo

```bash
helm repo add platform-gitops https://publicstaticdevnull.github.io/platform-gitops
helm search repo platform-gitops # look for argo-official/argocd-apps Chart
helm install argocd platform-gitops/argo-cd -f values.yaml --create-namespace=true --namespace=argocd
```

### Configure Argo

To access Argo, as stated on the helm output:

```bash
kubectl port-forward service/argocd-server -n argocd 8080:443
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

## Update Argo CD
```bash
helm repo update platform-gitops
helm search repo platform-gitops # look for argo-official/argocd-apps Chart
helm upgrade argocd platform-gitops/argo-cd -f values.yaml --namespace=argocd
```

### Enable SSL
To do


