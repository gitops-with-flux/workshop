# GitOps with Flux Workshop

## Prerequisites

- Cloud managed Kubernetes, or...
- Local Kubernetes cluster
  - Container runtime: Docker, podman, Colima, or compatible alternative
  - KinD (Recommended for multi-cluster)
- kubectl
- Flux CLI

## Schedule

- Slides: Introduction to the workshop, 10 minutes
- [Task](0-prerequisites): Prerequisite check, 5 - 10 minutes
- [Task](1-setting-up-local-clusters): Setting up local clusters, 5-10 minutes
- Slides: Introduction to Flux, 10 minutes
- [Task](2-bootstrapping-flux): Bootstrapping both environments
- [Task](3-adding-app-to-dev): Adding an application to the dev environment
- [Task](4-reuse-app-in-prod): re-use application base in prod
- [Task](5-auto-image-update): Automatic image update in prod
