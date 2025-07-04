# open-k0rdent-ui Helm Chart

![Version: 0.1.0](https://img.shields.io/badge/Version-0.1.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: latest](https://img.shields.io/badge/AppVersion-latest-informational?style=flat-square)

A Helm chart for open-k0rdent-ui - Web interface for Mirantis k0rdent cluster management

## Description

open-k0rdent-ui is a web-based interface for managing k0rdent clusters. It provides an intuitive dashboard for creating, monitoring, and managing Kubernetes clusters using the k0rdent operators.

## Prerequisites

- Kubernetes 1.19+
- Helm 3.2.0+
- k0rdent installed in the cluster

## Installing the Chart

To install the chart with the release name `open-k0rdent-ui`:

```bash
helm repo add mirantis-field https://charts.mirantis.com
helm install open-k0rdent-ui mirantis-field/open-k0rdent-ui
```

## Uninstalling the Chart

To uninstall/delete the `open-k0rdent-ui` deployment:

```bash
helm delete open-k0rdent-ui
```

## Configuration

The following table lists the configurable parameters of the Open K0rdent UI chart and their default values.

### Global Parameters

| Name | Description | Value |
|------|-------------|-------|
| `replicaCount` | Number of replicas to deploy | `1` |
| `nameOverride` | String to partially override open-k0rdent-ui.fullname | `""` |
| `fullnameOverride` | String to fully override open-k0rdent-ui.fullname | `""` |

### Image Parameters

| Name | Description | Value |
|------|-------------|-------|
| `image.repository` | Open K0rdent UI image repository | `ghcr.io/mirantis-field/open-k0rdent-ui` |
| `image.pullPolicy` | Open K0rdent UI image pull policy | `Always` |
| `image.tag` | Overrides the image tag whose default is the chart appVersion | `"latest"` |
| `imagePullSecrets` | Open K0rdent UI image pull secrets | `[]` |

### Service Account Parameters

| Name | Description | Value |
|------|-------------|-------|
| `serviceAccount.create` | Specifies whether a service account should be created | `true` |
| `serviceAccount.annotations` | Annotations to add to the service account | `{}` |
| `serviceAccount.name` | The name of the service account to use | `""` |

### Service Parameters

| Name | Description | Value |
|------|-------------|-------|
| `service.type` | Open K0rdent UI service type | `ClusterIP` |
| `service.port` | Open K0rdent UI service HTTP port | `3000` |
| `service.targetPort` | Open K0rdent UI service target port | `3000` |
| `service.name` | Open K0rdent UI service port name | `http` |

### Ingress Parameters

| Name | Description | Value |
|------|-------------|-------|
| `ingress.enabled` | Enable ingress record generation for Open K0rdent UI | `false` |
| `ingress.className` | IngressClass that will be be used to implement the Ingress | `""` |
| `ingress.annotations` | Additional annotations for the Ingress resource | `{}` |
| `ingress.hosts` | An array with hostname(s) to be covered with the ingress record | `[{"host": "k0rdent-ui.local", "paths": [{"path": "/", "pathType": "Prefix"}]}]` |
| `ingress.tls` | TLS configuration for the Ingress resource | `[]` |

### Resource Parameters

| Name | Description | Value |
|------|-------------|-------|
| `resources.limits.cpu` | The CPU limit for the Open K0rdent UI containers | `500m` |
| `resources.limits.memory` | The memory limit for the Open K0rdent UI containers | `512Mi` |
| `resources.requests.cpu` | The requested CPU for the Open K0rdent UI containers | `100m` |
| `resources.requests.memory` | The requested memory for the Open K0rdent UI containers | `128Mi` |

### Autoscaling Parameters

| Name | Description | Value |
|------|-------------|-------|
| `autoscaling.enabled` | Enable Horizontal Pod Autoscaler (HPA) for Open K0rdent UI | `false` |
| `autoscaling.minReplicas` | Minimum number of Open K0rdent UI replicas | `1` |
| `autoscaling.maxReplicas` | Maximum number of Open K0rdent UI replicas | `100` |
| `autoscaling.targetCPUUtilizationPercentage` | Target CPU utilization percentage | `80` |

### Application Parameters

| Name | Description | Value |
|------|-------------|-------|
| `app.env.NODE_ENV` | Node.js environment | `"production"` |
| `app.env.HOSTNAME` | Application hostname | `"0.0.0.0"` |

### Namespace Parameters

| Name | Description | Value |
|------|-------------|-------|
| `namespace.create` | Create namespace for the application | `true` |
| `namespace.name` | Namespace name | `"k0rdent-ui"` |
| `namespace.labels` | Additional labels for the namespace | `{"name": "k0rdent-ui"}` |

### RBAC Parameters

| Name | Description | Value |
|------|-------------|-------|
| `rbac.create` | Specifies whether RBAC resources should be created | `true` |
| `rbac.clusterRole.customRules` | Additional custom rules for the cluster role | `[]` |

### Health Check Parameters

| Name | Description | Value |
|------|-------------|-------|
| `probes.readiness.httpGet.path` | Readiness probe HTTP path | `/` |
| `probes.readiness.httpGet.port` | Readiness probe HTTP port | `http` |
| `probes.readiness.initialDelaySeconds` | Initial delay seconds for readiness probe | `5` |
| `probes.readiness.periodSeconds` | Period seconds for readiness probe | `10` |
| `probes.liveness.httpGet.path` | Liveness probe HTTP path | `/` |
| `probes.liveness.httpGet.port` | Liveness probe HTTP port | `http` |
| `probes.liveness.initialDelaySeconds` | Initial delay seconds for liveness probe | `15` |
| `probes.liveness.periodSeconds` | Period seconds for liveness probe | `20` |

## Example Usage

### Basic Installation

```bash
helm install open-k0rdent-ui mirantis-field/open-k0rdent-ui
```

### Installation with Ingress

```bash
helm install open-k0rdent-ui mirantis-field/open-k0rdent-ui \
  --set ingress.enabled=true \
  --set ingress.hosts[0].host=k0rdent.example.com
```

### Installation with Custom Resources

```bash
helm install open-k0rdent-ui mirantis-field/open-k0rdent-ui \
  --set resources.limits.cpu=1000m \
  --set resources.limits.memory=1Gi \
  --set replicaCount=2
```

## Security Considerations

This chart creates cluster-wide RBAC permissions required for the open-k0rdent-ui to manage k0rdent resources. The application requires:

- Read access to namespaces, services, configmaps, and secrets cluster-wide
- Full access to all k0rdent.mirantis.com custom resources
- Ability to execute commands in pods

Ensure you understand these permissions before deploying in production environments.

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| Mirantis Field Team | <mirantis-field@mirantis.com> |  |

## Source Code

* <https://github.com/mirantis-field/open-k0rdent-ui>

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.11.0](https://github.com/norwoodj/helm-docs) 