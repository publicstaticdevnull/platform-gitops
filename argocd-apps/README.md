# Argo config
This is used to install the ArgoCD gitops tool. 

## Install Argo Application Project

```bash
helm repo add argo-official https://argoproj.github.io/argo-helm ; helm repo update argo-official 
helm pull argo-official/argocd-apps -d ../      # Download the last  tar.gz
helm repo index ../                         # Update index
```
Now, commit and merge. You must do this, else, you won't be able to add this repo as a helm chart repo. Wait a couple of minutes till Github Refresh. 

```bash
helm repo add platform-gitops https://publicstaticdevnull.github.io/platform-gitops ; helm repo update platform-gitops # Install and update.
helm search repo platform-gitops # look for argo-official/argocd-apps Chart
helm install argocd-app-projects platform-gitops/argocd-apps -f ApplicationProjects/values.yaml --create-namespace=true --namespace=argocd
```

## Update Argo Application Project
Assuming you are on argocd-apps folder
```bash
helm upgrade argocd-app-projects platform-gitops/argocd-apps -f ApplicationProjects/values.yaml --namespace=argocd                                                               
```


## Install Argo applications
Install the platform apps apllications using helm

```bash
helm repo add argo-official https://argoproj.github.io/argo-helm ; helm repo update argo-official 
helm pull argo-official/argocd-apps -d ../      # Download the last  tar.gz
helm repo index ../                         # Update index
```
Now, commit and merge. You must do this, else, you won't be able to add this repo as a helm chart repo. Wait a couple of minutes till Github Refresh. 
```bash
helm repo add platform-gitops https://publicstaticdevnull.github.io/platform-gitops ; helm repo update platform-gitops # Install and update.
helm search repo platform-gitops # look for argo-official/argocd-apps Chart
helm install argocd-app-apps platform-gitops/argocd-apps -f Application/values.yaml --create-namespace=true --namespace=argocd
```