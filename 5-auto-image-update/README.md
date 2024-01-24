# Automatic image update in prod

One of the additional components you can get for Flux is the _image reflector_ and _image automation_ controllers. These make it possible to set up some more advanced routines 

## Run bootstrap again, with additional components

```bash
kubectl config use-context kind-prod
flux bootstrap github \
  --components-extra=image-reflector-controller,image-automation-controller \
  --owner=roberthstrand \
  --repository=workshop-gitops-with-flux \
  --branch=main \
  --path=./clusters/prod \
  --read-write-key \
  --personal
```

We add one flag to make sure the extra controllers are installed, and one to deploy a _read-write_ ssh key instead of a read only, as that is the default. This enables the controllers to not only read any changes in the desired state, but also update files in the git repository based on any changes.

_Note: The bootstrap command is idempotent, which means that you can run it several times without it trying to re-do anything that has already been done. In other words, it's pretty safe to just run the bootstrap command again with just the few extra flags._
