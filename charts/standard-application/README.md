# standard-application

A Helm chart for Kubernetes

Current Chart version: 1.0.22

This `standard-application` Helm Chart can cover most needs for when you want to deploy your web application container to Kubernetes.  Instead of writing your own custom Helm Chart you can use this or use this as a starting point.

This chart will create these Kubernetes resources:
* Deployment
* Service
* Ingress

<Diagram here on what it will create you>

## Why use this chart
Instead of having to figure out and write the Kubernetes `Deployment`, `Service`, and `Ingress` yaml files which at the minimum can be over a 100 lines, you can fill in the following and this Helm chart will generate all of the other necessary items necessary for a valid Kubernetes deployment.

```yaml
fullnameOverride: "test-app"
namespace: test1

deployment:
  containers:
  - name: container-name
    image:
      repository: gcr.io/google_containers/echoserver
      tag: "1.10"

    ports:
    - name: http
      protocol: TCP
      containerPort: 8080
      servicePort: 8080

ingress:
  enabled: true
  annotations:
    kubernetes.io/ingress.class: nginx-external
  paths:
    - path: /
      servicePort: http
  hosts:
    - api.example.com
  tls:
  - secretName: chart-example-tls
    hosts:
    - api.example.com
```

If you needed to make adjustments or turn various Kubernetes knobs, you can do that as well via the following configuration parameters.

## Installation

### Add Helm repository

```shell
helm repo add managedkube https://helm-charts.managedkube.com
helm repo update
```

## Configuration

The following table lists the configurable parameters of the chart and the default values.

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| automountServiceAccountToken | bool | `true` |  |
| deployment.affinity | object | `{}` |  |
| deployment.annotations | object | `{}` |  |
| deployment.containerSpecOptions | object | `{}` |  |
| deployment.containers[0].args | list | `[]` |  |
| deployment.containers[0].command | list | `[]` |  |
| deployment.containers[0].env.base | list | `[]` |  |
| deployment.containers[0].env.perEnv | list | `[]` |  |
| deployment.containers[0].envFrom | list | `[]` |  |
| deployment.containers[0].image.pullPolicy | string | `"IfNotPresent"` |  |
| deployment.containers[0].image.repository | string | `"gcr.io/google_containers/echoserver"` |  |
| deployment.containers[0].image.tag | string | `"1.10"` |  |
| deployment.containers[0].livenessProbe | object | `{}` |  |
| deployment.containers[0].name | string | `"container-name"` |  |
| deployment.containers[0].ports | list | `[]` |  |
| deployment.containers[0].readinessProbe | object | `{}` |  |
| deployment.containers[0].resources | object | `{}` |  |
| deployment.containers[0].securityContext | object | `{}` |  |
| deployment.containers[0].volumeMounts | list | `[]` |  |
| deployment.enable | bool | `true` |  |
| deployment.enableInitContainer | bool | `false` |  |
| deployment.imagePullSecrets | list | `[]` |  |
| deployment.initContainers[0].image | string | `"docker.io/my-container:foo"` |  |
| deployment.initContainers[0].name | string | `"init-container-name"` |  |
| deployment.nodeSelector | object | `{}` |  |
| deployment.strategy | object | `{}` |  |
| deployment.tolerations | list | `[]` |  |
| fullnameOverride | string | `""` |  |
| hpa.enabled | bool | `false` |  |
| hpa.spec.maxReplicas | int | `10` |  |
| hpa.spec.minReplicas | int | `1` |  |
| hpa.spec.scaleTargetRef.apiVersion | string | `"apps/v1"` |  |
| hpa.spec.scaleTargetRef.kind | string | `"Deployment"` |  |
| hpa.spec.scaleTargetRef.name | string | `"standard-application"` |  |
| hpa.spec.targetCPUUtilizationPercentage | int | `50` |  |
| ingress.annotations | object | `{}` |  |
| ingress.enabled | bool | `false` |  |
| ingress.hosts[0] | string | `"chart-example.local"` |  |
| ingress.paths | list | `[]` |  |
| ingress.tls | list | `[]` |  |
| labels | object | `{}` |  |
| nameOverride | string | `""` |  |
| replicaCount | int | `1` |  |
| service.port | int | `80` |  |
| service.type | string | `"ClusterIP"` |  |
| serviceaccount.annotations | object | `{}` |  |
| serviceaccount.enabled | bool | `false` |  |
| serviceaccount.labels | object | `{}` |  |
| servicemonitor.enabled | bool | `false` |  |
| statefulset.enable | bool | `false` |  |
| volumeClaimTemplates[0].metadata.name | string | `"www"` |  |
| volumeClaimTemplates[0].spec.accessModes[0] | string | `"ReadWriteOnce"` |  |
| volumeClaimTemplates[0].spec.resources.requests.storage | string | `"1Gi"` |  |
| volumeClaimTemplates[0].spec.storageClassName | string | `"my-storage-class"` |  |
| volumes | list | `[]` |  |

## Local Helm Testing

### Temlating out values:

Testing it out with the default values.
```
helm template --values values.yaml ./
```

Testing it out with a value from the `ci` folder:
```
helm template --values values.yaml --values ./ci/secrets-volumes-values.yaml ./
```
