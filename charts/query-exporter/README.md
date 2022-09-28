# query-exporter

A Helm chart for Kubernetes to run query-exporter

Current Chart version: 0.1.2

A Helm chart for Kubernetes to run query-exporter

**Homepage:** <https://github.com/albertodonato/query-exporter>

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` |  |
| env | object | `{}` |  |
| existingSecret | string | `""` |  |
| exporter_config | string | `"databases:\n  db1:\n    dsn: env:DB_CONNECTION_STRING\n\nmetrics:\n  metrics1:\n    type: gauge\n    description: Blocks count\n\nqueries:\n  query1:\n    interval: 5\n    databases: [db1]\n    metrics: [metric1]\n    sql: SELECT random() / 1000000000000000 AS metric1\n"` |  |
| extraVolumeMounts | object | `{}` |  |
| extraVolumes | object | `{}` |  |
| fullnameOverride | string | `"query-exporter"` |  |
| image.command[0] | string | `"query-exporter"` |  |
| image.command[1] | string | `"-H"` |  |
| image.command[2] | string | `"0.0.0.0"` |  |
| image.command[3] | string | `"--"` |  |
| image.command[4] | string | `"/config/config.yaml"` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"adonato/query-exporter"` |  |
| image.tag | string | `"2.7.0"` |  |
| livenessProbe.failureThreshold | int | `2` |  |
| livenessProbe.httpGet.path | string | `"/"` |  |
| livenessProbe.httpGet.port | int | `9560` |  |
| livenessProbe.httpGet.scheme | string | `"HTTP"` |  |
| livenessProbe.initialDelaySeconds | int | `60` |  |
| livenessProbe.periodSeconds | int | `30` |  |
| livenessProbe.successThreshold | int | `1` |  |
| livenessProbe.timeoutSeconds | int | `2` |  |
| metrics.serviceMonitor.enabled | bool | `false` |  |
| metrics.serviceMonitor.interval | string | `"10s"` |  |
| metrics.serviceMonitor.namespace | string | `"monitoring"` |  |
| metrics.serviceMonitor.selector | object | `{}` |  |
| nameOverride | string | `"query-exporter"` |  |
| nodeSelector | object | `{}` |  |
| readinessProbe.failureThreshold | int | `4` |  |
| readinessProbe.httpGet.path | string | `"/"` |  |
| readinessProbe.httpGet.port | int | `9560` |  |
| readinessProbe.httpGet.scheme | string | `"HTTP"` |  |
| readinessProbe.initialDelaySeconds | int | `60` |  |
| readinessProbe.periodSeconds | int | `30` |  |
| readinessProbe.successThreshold | int | `1` |  |
| readinessProbe.timeoutSeconds | int | `2` |  |
| replicaCount | int | `1` |  |
| resources.limits.memory | string | `"512Mi"` |  |
| resources.requests.cpu | string | `"10m"` |  |
| resources.requests.memory | string | `"128Mi"` |  |
| secrets | object | `{}` |  |
| service.port | int | `9560` |  |
| service.targetPort | int | `9560` |  |
| service.type | string | `"ClusterIP"` |  |
| serviceAccount.annotations | object | `{}` |  |
| serviceAccount.create | bool | `true` |  |
| serviceAccount.name | string | `""` |  |
| strategy.rollingUpdate.maxSurge | int | `1` |  |
| strategy.rollingUpdate.maxUnavailable | int | `0` |  |
| strategy.type | string | `"RollingUpdate"` |  |
| tolerations | list | `[]` |  |
