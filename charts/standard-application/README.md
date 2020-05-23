standard-application
====================
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

## Configuration
The following table lists the configurable parameters of the chart and their default values.

Parameter | Description | Default
--- | --- | ---
`fullnameOverride` | The full override of the default charts name | `standard-application`
`namespace` | The namespace that this chart will be deployed to | `default`
`nameOverride` | The name override | ``
`replicaCount` | The replica count for the deployment | `1`
`labels` | Labels to place on all of the resources | `{}`
`deployment.containers.[].name` | The name of the container | `container-name`
`deployment.containers.[].image.repository` | The Docker image repository name | `nginx`
`deployment.containers.[].image.tag` | The Docker tag | `xxxx`
`deployment.containers.[].image.pullPolicy` | The image pull policy | `IfNotPresent`
`deployment.containers.[].container.command` | The container command list to use | `[]`
`deployment.containers.[].container.args` | The container args list to use | `[]`
`deployment.containers.[].container.env.base` | The envars that applies to all environments | `[]`
`deployment.containers.[].container.env.perEnv` | The envars that applies to a certain environments | `[]`
`deployment.containers.[].container.ports[].name` | The port's name for this container | `[]`
`deployment.containers.[].container.ports[].protocol` | The port's protocol type for this container | `[]`
`deployment.containers.[].container.ports[].containerPort` | The port's container port number for this container | `[]`
`deployment.containers.[].container.livenessProbe` | The liveness probe for this container | `{}`
`deployment.containers.[].container.readinessProbe` | The readinessProbe probe for this container | `{}`
`deployment.containers.[].container.resources` | The resources (CPU/Memory) for this container | `{}`
`deployment.strategy` | The update strategy settings for this deployment | `{}`
`deployment.containerSpecOptions` | The container spec options for this deployment | `{}`
`deployment.nodeSelector` | The nodeSelectors for this deployment | `{}`
`deployment.tolerations` | The tolerations for this deployment | `[]`
`deployment.affinity` | The affinity for this deployment | `{}`
`servicemonitor.enabled` | Enable the Prometheus ServiceMonitor CRD | `false`
`service.type` | The type of service this is | `ClusterIP`
`service.port` | The port this service is on | `80`
`ingress.enabled` | To enable the ingress or not | `false`
`ingress.annotations` | The annotations for this ingress | `{}`
`ingress.paths` | The HTTP paths list for this ingress | `[]`
`ingress.hosts` | The hosts list for this ingress | `chart-example.local`
`ingress.tls` | The TLS list for this ingress | `[]`
