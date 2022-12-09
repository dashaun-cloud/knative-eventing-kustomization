# Knative Eventing Kustomization

For use with [FluxCD](https://fluxcd.io) to deploy [Knative Eventing](https://knative.dev)

## Add the GitRepository

```bash
flux create source git knative-eventing \
  --url=https://github.com/dashaun-cloud/knative-eventing-kustomization \
  --branch=main \
  --export > ./clusters/cluster00/knative-eventing-kustomization-source.yaml
```

## Add the Kustomization

```bash
flux create kustomization knative-eventing \
  --depends-on knative-operator \
  --source=knative-eventing \
  --path="./kustomize" \
  --prune=true \
  --export > ./clusters/cluster00/knative-eventing-kustomization.yaml
```