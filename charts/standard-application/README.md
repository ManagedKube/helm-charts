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
`image.repository` | The Docker image repository name | `nginx`
`image.tag` | The Docker tag | `xxxx`
`image.pullPolicy` | The image pull policy | `IfNotPresent`
`labels` | Labels to place on all of the resources | `{}`
`container.command` | The container command to use | `[]`
