# Baremetal k3d GitOps with Flux
## Verify State

● Check Flux status:
```
flux get kustomizations -A
```
● View what Flux manages:
```
flux tree kustomization flux-system -n flux-system
```