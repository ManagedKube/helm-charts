standard-application
====================
A Helm chart for Kubernetes

Current chart version is `1.0.1`

Source code can be found [here](https://github.com/ManagedKube/helm-charts)

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
helm repo add managedkube https://docs.managedkube.com/helm-charts
helm repo update
```


## Configuration

The following table lists the configurable parameters of the chart and the default values.

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
| deployment.containers[0].image.repository | string | `"gcr.io/google_containers/echoserver"` |  |
| deployment.containers[0].image.tag | string | `"1.10"` |  |
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
| replicaCount | int | `1` |  |
| service.port | int | `80` |  |
| service.type | string | `"ClusterIP"` |  |
| servicemonitor.enabled | bool | `false` |  |
