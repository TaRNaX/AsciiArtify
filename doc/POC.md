### Create kubenetes cluster:

`k3d cluster create -a 3`
Check cluster
`kubectl cluster-info`

### Install Argo CD on cluster:

`kubectl create namespace argocd`
`kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml`

Check Argo CD:
`kubectl get po -n argocd`

Get Argo CD UI password:
`kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo`
Expose UI by port-forwarding:
`kubectl port-forward svc/argocd-server -n argocd 8080:443&`

Access Argo CD in browser:
`https://localhost:8080`

Argo CD setup demo:
[![asciicast](https://asciinema.org/a/589458.svg)](https://asciinema.org/a/589458)