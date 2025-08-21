# Mirantis Field Team Helm Charts Repository

This is the Helm repository for charts maintained by the Mirantis Field Team.

## Usage

Add this repository to Helm:

```bash
helm repo add mirantis-field https://mirantis-field.github.io/helm-charts
helm repo update
```

Search for available charts:

```bash
helm search repo mirantis-field
```

Install a chart:

```bash
helm install my-release mirantis-field/aws-custom-hosted-cp
```

For more information about individual charts, visit the [source repository](https://github.com/mirantis-field/helm-charts).
