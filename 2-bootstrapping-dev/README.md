# Bootstrapping the development environment

## Create a new Personal Access Token for GitHub

We will be using a personal access token (PAT) to access GitHub with the Flux CLI. This PAT needs to have all the repository level access set.

Link: https://github.com/settings/tokens

## Set token as environment variable

You need to have your PAT as an environment variable, or supply it when you run the bootstrap command. There are various ways of setting an environment variable, a few can be founder below.

``` bash
# bash / zsh / fish
export GITHUB_TOKEN=ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

``` powershell
# PowerShell
$ENV:GITHUB_TOKEN = "ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
```

## Run the bootstrap command

Now it is time to finally get Flux into our clusters. This is most commonly done by running the bootstrap subcommand.

``` bash
kubectl config use-context kind-dev

flux bootstrap github \
  --owner=roberthstrand \
  --repository=workshop-gitops-with-flux \
  --branch=main \
  --path=./clusters/dev \
  --personal

kubectl config use-context kind-prod

flux bootstrap github \
  --owner=roberthstrand \
  --repository=workshop-gitops-with-flux \
  --branch=main \
  --path=./clusters/prod \
  --personal
```

The `--personal` tag is necessary if you want to use a repository on your private GitHub user, not if you are using a repository under your organization.

_Note: Neither the repository or the path need doesn't have to exists. If you run this command without having created this first, it will be created in the process. The repository is private by default, but you can add `--private=false` to override that._
