# Argo config
This is used to install or update the application project. 

## Kickstart
Ok, let's pretend you have nothing and you are starting fresh new. First of all you must add this CRDs... nevermins, later, when you install argoCD thi will recognize them.

```bash
helm repo add argo-official https://argoproj.github.io/argo-helm
helm repo add argo-local https://publicstaticdevnull.github.io/platform-gitops/continous-delivery-argo
cd argo-config
helm search repo argo-official            # look for argo-official/argocd-apps Chart
helm pull argo-official/argocd-apps       # Download the last  tar.gz
helm repo index .                         # Update index
helm repo update argo-local               # Update the local repository
# MERGE THE CHANGES #
helm search repo argo-local               # Look for changes
```
