# Adding an application to the development environment

## Structuring your repository for multiple environments

One common way of structuring a repository when using Flux, is to utilize Kustomize overlays and follow the following pattern.

``` text
├── apps
│   ├── base
│   ├── production
│   └── staging
├── infrastructure
│   ├── base
│   ├── production
│   └── staging
└── clusters
    ├── production
    └── staging
```

This is an example that I got from a guide on fluxcd.io, called [Ways of structuring your repositories](https://fluxcd.io/flux/guides/repository-structure/). However, you could follow whatever pattern that makes sense to you. Note that regular Kubernetes manifests also works fine, you do not have to use Kustomize at all.

For the purposes for this workshop, we will be adding at least the clusters directory, with our environments, and the apps directory.

## Adding an application

In the current folder we are in (`./3-adding-app-to-dev/`), we have an example of an app deployment. Within your `clusters/dev` directory, you would have a directory for the flux-system namespace that was generated by the Flux CLI, but you want to add a new Kustomization resource to set up the application reconciliation for the environment.
