# Baremetal k3d GitOps with Flux

## Overview

GitOps tool: Flux CD

Cluster: k3d (local Kubernetes)

Configuration management: Kustomize

Ingress: ingress-nginx (via HelmRelease)

Example app: whoami

## Repository Structure
.
├── apps/
│   └── whoami/
│       ├── deployment.yaml
│       ├── service.yaml
│       ├── ingress.yaml
│       └── kustomization.yaml
│
├── infra/
│   └── ingress-nginx/
│       ├── namespace.yaml
│       ├── release.yaml
│       └── kustomization.yaml
│
├── clusters/
│   └── local-cluster/
│       ├── kustomization.yaml
│       ├── namespaces/
│       │   └── whoami.yaml
│       └── flux-system/
│           ├── gotk-components.yaml
│           ├── gotk-sync.yaml
│           └── kustomization.yaml
│
└── README.md

## Verify State

● Check Flux status:
```
flux get kustomizations -A
```
● View what Flux manages:
```
flux tree kustomization flux-system -n flux-system
```