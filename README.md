# Baremetal k3d (Kubernetes cluster) GitOps with Flux
## Create k3d cluster
```
k3d cluster create <your_cluster_name> \
  -p "80:80@loadbalancer" \
  -p "443:443@loadbalancer"
```
## Connect Flux to GitHub
```
flux bootstrap github \
  --owner=<your-github-username> \
  --repository=<your-github-repo-name> \
  --branch=main \
  --path=<your-repo-path> \
  --personal
```
## Verify State
Is Flux healthy?
```
flux get kustomizations -A
```
What did Flux actually apply?
```
flux tree kustomization flux-system -n flux-system
```
Why is app not running?
```
kubectl get ns
kubectl get deploy -n whoami
kubectl get pods -n whoami
```
Check Pod Logs
```
kubectl describe pod -n whoami <pod-name>
```
Did Flux pick up Git change? (READY=True)
```
flux get sources git -n flux-system
```
if False
```
flux reconcile kustomization flux-system
```
