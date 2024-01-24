# Setting up the clusters

We want to create two clusters, one called dev and one called prod, to emulate a multi-environment set up. We can create a cluster with `kind create cluster`, and name the cluster by using the flag `-n`. Below is an example of a one-liner that creates the two clusters.

``` bash
kind create cluster -n dev && kind create cluster -n prod
```

## Switching between clusters

We can switch between the two clusters by running `kubectl config use-context kind-<name-of-cluster>`. In our scenario, the two commands would be `kubectl config use-context kind-dev` and `kubectl config use-context kind-prod`.
