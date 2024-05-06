# ArgoCD Bootstrap GitOps-Operator

How to install the argocd-autopilot CLI see here: https://argocd-autopilot.readthedocs.io/en/stable/Installation-Guide/

## Recovery Repository for a new Instance

**MAC/UNIX**
```shell
export GIT_REPO=https://github.com/lambrech-hsrt/argocd-bootstrap
export GIT_TOKEN=PAT

argocd-autopilot repo bootstrap --recover
```

**Windows (Powershell)**
```shell
$env:GIT_REPO = "https://github.com/lambrech-hsrt/argocd-bootstrap"
$env:GIT_TOKEN = "PAT"

argocd-autopilot repo bootstrap --recover
```
