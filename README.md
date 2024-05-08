# ArgoCD Bootstrap GitOps-Operator (Public Repo)

This is an Testing Repository for ArgoCD as an GitOps-Operator to automatically deploy and manage Applications.

[argoproj-labs/argocd-autopilot](https://github.com/argoproj-labs/argocd-autopilot)

- Repo pattern: Monorepo
- Operator pattern: Instance per Cluster / Hub and Spoke
- Operator: ArgoCD
- Boostrapping: argocd-autopilot
- Linking: kustomization.yaml, ArgoCD Application, ApplicationSet
- Features:
    - Operate ArgoCD with GitOps

installation guide for the argocd-autopilot CLI: https://argocd-autopilot.readthedocs.io/en/stable/Installation-Guide/

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

default password:
```shell
kubectl get secret argocd-initial-admin-secret -n argocd -o yaml
```

output should look something like this
```
apiVersion: v1
data:
  password: PASSWORD HERE
kind: Secret
metadata:
  creationTimestamp: "2024-05-06T09:29:02Z"
  name: argocd-initial-admin-secret
  namespace: argocd
  resourceVersion: "876"
  uid: 44489085-0b23-428a-9c59-280df01cd1c6
type: Opaque
```

## Deploy a new Application
```
 argocd app create test \      
  --repo <repo-url> \
  --path <path-to-manifests> \
  --dest-server <kubernetes-cluster-url> \
  --dest-namespace <kubernetes-namespace> \
  --project <project-name> \
  --sync-policy automated
```
