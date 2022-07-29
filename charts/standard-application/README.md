# standard-application

A Helm chart for Kubernetes

Current Chart version: 1.0.33

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
| flux.flagger.apiVersion | string | `"flagger.app/v1beta1"` |  |
| flux.flagger.enabled | bool | `false` |  |
| flux.flagger.spec.analysis.interval | string | `"1m"` |  |
| flux.flagger.spec.analysis.maxWeight | int | `50` |  |
| flux.flagger.spec.analysis.stepWeight | int | `5` |  |
| flux.flagger.spec.analysis.threshold | int | `10` |  |
| flux.flagger.spec.analysis.webhooks[0].metadata.cmd | string | `"hey -z 1m -q 10 -c 2 http://example-app.example-app-namespace:8080/"` |  |
| flux.flagger.spec.analysis.webhooks[0].name | string | `"load-test"` |  |
| flux.flagger.spec.analysis.webhooks[0].timeout | string | `"5s"` |  |
| flux.flagger.spec.analysis.webhooks[0].type | string | `"rollout"` |  |
| flux.flagger.spec.analysis.webhooks[0].url | string | `"http://loadtester.flagger-test/"` |  |
| flux.flagger.spec.service.port | int | `8080` |  |
| flux.flagger.spec.targetRef.apiVersion | string | `"apps/v1"` |  |
| flux.flagger.spec.targetRef.kind | string | `"Deployment"` |  |
| flux.flagger.spec.targetRef.name | string | `"example-app"` |  |
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
| ingress.ingressClass.enabled | bool | `true` |  |
| ingress.ingressClass.spec.controller | string | `"istio.io/ingress-controller"` |  |
| ingress.paths | list | `[]` |  |
| ingress.tls | list | `[]` |  |
| istio.virtualService.apiVersion | string | `"networking.istio.io/v1alpha3"` |  |
| istio.virtualService.enabled | bool | `false` |  |
| istio.virtualService.spec.gateways[0] | string | `"istio-system/main-gateway"` |  |
| istio.virtualService.spec.hosts[0] | string | `"www.example.com"` |  |
| istio.virtualService.spec.hosts[1] | string | `"foo.com"` |  |
| istio.virtualService.spec.http[0].match[0].uri.prefix | string | `"/"` |  |
| istio.virtualService.spec.http[0].route[0].destination.host | string | `"example-app"` |  |
| istio.virtualService.spec.http[0].route[0].destination.port.number | int | `8080` |  |
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
