# ArgoCD Bootstrap GitOps-Operator

How to install the argocd-autopilot CLI see here: https://argocd-autopilot.readthedocs.io/en/stable/Installation-Guide/

## Recovery Repository in case of a new Cluster Instance

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

After that you can start the ArgoCD UI and login with the default credentials at http://localhost:8080
```shell
kubectl port-forward -n argocd svc/argocd-server 8080:80
```
