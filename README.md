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
cd /opt/app/charts
ct lint --config /opt/app/.github/ct.yaml
```

## Run your own helm-chart repo

[https://jamiemagee.co.uk/blog/how-to-host-your-helm-chart-repository-on-github/](https://jamiemagee.co.uk/blog/how-to-host-your-helm-chart-repository-on-github/)
