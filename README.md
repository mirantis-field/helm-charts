# Mirantis Field Team Helm Charts

This repository contains Helm charts developed and maintained by the Mirantis Field Team. These charts are designed to deploy and manage applications commonly used in customer environments and field demonstrations.

## TL;DR

```bash
$ helm repo add mirantis-field https://mirantis-field.github.io/helm-charts
$ helm repo update
$ helm search repo mirantis-field
$ helm install my-release mirantis-field/<chart-name>
```

## Before You Begin

### Setup a Kubernetes Cluster

For setting up Kubernetes on cloud platforms or bare-metal servers, refer to the [k0s documentation](https://docs.k0sproject.io/stable/).

### Install Helm

Helm is a tool for managing Kubernetes charts. Charts are packages of pre-configured Kubernetes resources.

To install Helm, refer to the [Helm install guide](https://helm.sh/docs/intro/install/) and ensure that the `helm` binary is in the `PATH` of your shell.

### Add Repository

The following command allows you to download and install all the charts from this repository:

```bash
$ helm repo add mirantis-field https://mirantis-field.github.io/helm-charts
```

### Using Helm

Once you have installed the Helm client, you can deploy a Mirantis Field Team Helm Chart into a Kubernetes cluster.

Please refer to the [Quick Start guide](https://helm.sh/docs/intro/quickstart/) if you wish to get running in just a few commands, otherwise the [Using Helm Guide](https://helm.sh/docs/intro/using_helm/) provides detailed instructions on how to use the Helm client to manage packages on your Kubernetes cluster.

## Available Charts

| Chart | Description | Version |
|-------|-------------|---------|
| [open-k0rdent-ui](./charts/open-k0rdent-ui) | Web interface for Mirantis k0rdent cluster management | 0.1.0 |
| [aws-custom-hosted-cp](./charts/openstack-hosted-cp) | KCM template to deploy k8s clusters on AWS with hosted control plane | 1.0.12 |
| [azure-custom-hosted-cp](./charts/openstack-hosted-cp) | KCM template to deploy k8s clusters on Azure with hosted control plane | 1.0.14 |

## Useful Helm Commands

- View available charts: `helm search repo mirantis-field`
- Install a chart: `helm install my-release mirantis-field/<chart-name>`
- Upgrade your application: `helm upgrade my-release mirantis-field/<chart-name>`
- Uninstall a release: `helm uninstall my-release`
- Get release status: `helm status my-release`

## Contributing

We welcome contributions to this repository! Please see our [Contributing Guidelines](CONTRIBUTING.md) for details on how to submit charts, report issues, and contribute to the project.

### Chart Development Guidelines

When contributing new charts or updating existing ones:

1. Follow the [Helm Best Practices](https://helm.sh/docs/chart_best_practices/)
2. Ensure your chart passes `helm lint`
3. Include comprehensive documentation in the chart's README.md
4. Update the chart version in Chart.yaml
5. Test your chart with `helm install --dry-run`

### Submitting Changes

1. Fork this repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## Support

For issues specific to individual charts, please check the chart's README for specific support information.

For general repository issues:
- Create an issue in this repository
- Contact the Mirantis Field Team

## License

Copyright (c) 2025 Mirantis, Inc.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

## About Mirantis

Mirantis helps organizations achieve digital self-determination by using open source software to provide complete application and data portability without vendor lock-in.