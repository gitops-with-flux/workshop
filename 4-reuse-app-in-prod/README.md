# Re-use application base in prod

Since we spent some time making sure that we have a proper templated approach from the get-go, we can now pretty easily add the same application into a separate environment without having to copy/paste a bunch of Kubernetes manifests. The only thing we need to add is the Kustomization resource, and a new kustomize overlay for production.

Usually in production environments, you want to set a specific version of an app, set a different number of replicas, and such. We will add these changes to the Kustomize overlay.

## Production overlay

We will follow the same type of pattern that we already have in our development environment, but this time we will add a specific version of the container tag as part of the overlay.

``` yaml
apiVersion: kustomize.config.k8s.io/v1beta1
kind: Kustomization
namespace: podtato-head
resources:
  - ../../base/podtato-head
commonLabels:
  env: prod
images:
  - name: ghcr.io/podtato-head/entry
    newTag: 0.2.7
  - name: ghcr.io/podtato-head/hat
    newTag: 0.2.7
  - name: ghcr.io/podtato-head/left-arm
    newTag: 0.2.7
  - name: ghcr.io/podtato-head/right-arm
    newTag: 0.2.7
  - name: ghcr.io/podtato-head/left-leg
    newTag: 0.2.7
  - name: ghcr.io/podtato-head/right-leg
    newTag: 0.2.7
```

We go through all the images defined in our deployments throughout the base manifests file, and update the tag to be a _0.2.7_ instead of _latest_.
