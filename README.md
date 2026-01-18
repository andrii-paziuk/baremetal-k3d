# Baremetal k3d GitOps with Flux
## Command
```
flux bootstrap github \
  --owner=<your-github-username> \
  --repository=<your-github-repo-name> \
  --branch=main \
  --path=<your-repo-path> \
  --personal
```
## Verify State
● Check Flux status:
```
flux get kustomizations -A
```
● View what Flux manages:
```
flux tree kustomization flux-system -n flux-system
```