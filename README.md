# repository-template

Template for app repositories that build a container image and deploy it
through the [helm](https://github.com/chris911e/helm) GitOps repo.

## Setup

### `HELM_DISPATCH_TOKEN` secret

After an image is pushed, the build workflow triggers the helm repo to bump the
image tag. That call needs a token, and **every repository created from this
template needs its own copy of the secret**:

1. Get the token from the cluster (`dev` and `prod`
   namespaces):

2. In the new repository, go to **Settings → Secrets and variables → Actions →
   New repository secret** and add it with the name `HELM_DISPATCH_TOKEN`.

The token is a fine-grained personal access token with access to only
`chris911e/helm` and **Actions: Read and write**.
