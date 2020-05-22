# ManagedKube

[![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/managedkube/helm-charts?style=for-the-badge)](https://github.com/managedkube/helm-charts/releases/latest)
[![License](https://img.shields.io/github/license/managedkube/helm-charts?style=for-the-badge)](https://opensource.org/licenses/AGPL-3.0)

Automated dependency updates. Multi-platform and multi-language.

This repository hosts ManagedKube's [Helm](https://helm.sh) charts. Chart documentation is automatically generated using [helm-docs](https://github.com/norwoodj/helm-docs)

## Add Helm repository

```bash
helm repo add managedkube https://docs.managedkube.com/helm-charts
helm repo update
```

## Install chart

Using config from a file:

```bash
helm install --generate-name --set-file managedkube.config=config.json managedkube/generic-application
```

Using config from a string:

```bash
helm install --generate-name --set managedkube.config='\{\"token\":\"...\"\}' managedkube/generic-application
```

**NOTE**: `managedkube.config` must be a valid managedkube [self-hosted configuration](https://docs.managedkube.com/self-hosted-configuration/)

## Run your own helm-chart repo

[https://jamiemagee.co.uk/blog/how-to-host-your-helm-chart-repository-on-github/](https://jamiemagee.co.uk/blog/how-to-host-your-helm-chart-repository-on-github/)
