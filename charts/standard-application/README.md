standard-application
====================
A Helm chart for Kubernetes

Current chart version is `1.0.0`

Source code can be found [here](https://github.com/ManagedKube/helm-charts)

## Chart Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| deployment.affinity | object | `{}` |  |
| deployment.containerSpecOptions | object | `{}` |  |
| deployment.containers[0].args | list | `[]` |  |
| deployment.containers[0].command | list | `[]` |  |
| deployment.containers[0].env.base | list | `[]` |  |
| deployment.containers[0].env.perEnv | list | `[]` |  |
| deployment.containers[0].image.pullPolicy | string | `"IfNotPresent"` |  |
| deployment.containers[0].image.repository | string | `"nginx"` |  |
| deployment.containers[0].image.tag | string | `"xxxxx"` |  |
| deployment.containers[0].livenessProbe | object | `{}` |  |
| deployment.containers[0].name | string | `"container-name"` |  |
| deployment.containers[0].ports | list | `[]` |  |
| deployment.containers[0].readinessProbe | object | `{}` |  |
| deployment.containers[0].resources | object | `{}` |  |
| deployment.nodeSelector | object | `{}` |  |
| deployment.strategy | object | `{}` |  |
| deployment.tolerations | list | `[]` |  |
| fullnameOverride | string | `""` |  |
| ingress.annotations | object | `{}` |  |
| ingress.enabled | bool | `false` |  |
| ingress.hosts[0] | string | `"chart-example.local"` |  |
| ingress.paths | list | `[]` |  |
| ingress.tls | list | `[]` |  |
| labels | object | `{}` |  |
| nameOverride | string | `""` |  |
| namespace | string | `"default"` |  |
| replicaCount | int | `1` |  |
| service.port | int | `80` |  |
| service.type | string | `"ClusterIP"` |  |
| servicemonitor.enabled | bool | `false` |  |
