standard-application
====================
This `standard-application` Helm Chart can cover most needs for when you want to deploy your web application container to Kubernetes.  Instead of writing your own custom Helm Chart you can use this or use this as a starting point.

This chart will create these Kubernetes resources:
* Deployment
* Service
* Ingress

<Diagram here on what it will create you>

## Configuration
The following table lists the configurable parameters of the chart and their default values.

Parameter | Description | Default
--- | --- | ---
`fullnameOverride` | The full override of the default charts name | `standard-application`
`namespace` | The namespace that this chart will be deployed to | `default`
`nameOverride` | The name override | ``
`replicaCount` | The replica count for the deployment | `1`
`labels` | Labels to place on all of the resources | `{}`
`containers.[].name` | The name of the container | `container-name`
`containers.[].image.repository` | The Docker image repository name | `nginx`
`containers.[].image.tag` | The Docker tag | `xxxx`
`containers.[].image.pullPolicy` | The image pull policy | `IfNotPresent`
`containers.[].container.command` | The container command list to use | `[]`
`containers.[].container.args` | The container args list to use | `[]`
`containers.[].container.env.base` | The envars that applies to all environments | `[]`
`containers.[].container.env.perEnv` | The envars that applies to a certain environments | `[]`
`containers.[].container.ports[].name` | The port's name for this container | `[]`
`containers.[].container.ports[].protocol` | The port's protocol type for this container | `[]`
`containers.[].container.ports[].containerPort` | The port's container port number for this container | `[]`
`containers.[].container.livenessProbe` | The liveness probe for this container | `{}`
`containers.[].container.readinessProbe` | The readinessProbe probe for this container | `{}`
`strategy` | The update strategy settings for this deployment | `{}`
`containerSpecOptions` | The container spec options for this deployment | `{}`