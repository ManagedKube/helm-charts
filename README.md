# ManagedKube

[![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/managedkube/helm-charts?style=for-the-badge)](https://github.com/managedkube/helm-charts/releases/latest)
[![License](https://img.shields.io/github/license/managedkube/helm-charts?style=for-the-badge)](https://opensource.org/licenses/AGPL-3.0)

Automated dependency updates. Multi-platform and multi-language.

This repository hosts ManagedKube's [Helm](https://helm.sh) charts. Chart documentation is automatically generated using [helm-docs](https://github.com/norwoodj/helm-docs)

## Add Helm repository

```bash
helm repo add managedkube https://helm-charts.managedkube.com
helm repo update
```
## Chart test
```
docker run -it \
-v ${PWD}:/opt/app \
quay.io/helmpack/chart-testing:v3.0.0-rc.1 sh
```

run linter:
```
cd /opt/app
ct lint --config /opt/app/.github/ct.yaml
```

## Run your own helm-chart repo

[https://jamiemagee.co.uk/blog/how-to-host-your-helm-chart-repository-on-github/](https://jamiemagee.co.uk/blog/how-to-host-your-helm-chart-repository-on-github/)

### Helm Doc
Helm-docs isn’t strictly a linting tool, but it makes sure that your documentation stays up-to-date with the current state of your chart. It requires that you create a README.md.gotmpl in each chart repository using the [https://github.com/norwoodj/helm-docs#available-templates](available templates), otherwise it will create a README.md for you using a default template.

This runs Helm-docs against each chart in your repository and generates the README.md for each one. Then, using git, you’ll fail the build if there are any differences. This ensures that you can’t check in any changes to your charts without also updating the documentation.

#### Updating doc

From the root of this repo, run:

```
./.github/helm-docs.sh
```

This will run the `README.md.gotmpl` and update the `README.md` file.
