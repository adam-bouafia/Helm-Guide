
# Helm Guide

A detailed resource on using [Helm](https://helm.sh), the Kubernetes package manager. This guide covers installation, chart architecture, templating, lifecycle management, and advanced topics like packaging, signing, and uploading charts. Ideal for developers and DevOps engineers looking to streamline Kubernetes deployments.

## Contents

- [Overview](#overview)
- [Getting Started with Helm](#getting-started-with-helm)
- [Helm Architecture](#helm-architecture)
- [Charts & Templating](#charts--templating)
- [Lifecycle Management](#lifecycle-management)
- [Packaging & Signing Charts](#packaging--signing-charts)
- [Customizing Charts](#customizing-charts)
- [Repository Management](#repository-management)
- [Helm Commands](#helm-commands)
- [Labs & Exercises](#labs--exercises)

## Overview

Helm is a powerful package manager for Kubernetes, simplifying the deployment of complex applications. This guide is structured to help you understand Helm's architecture, templating capabilities, and lifecycle management for effective Kubernetes cluster management.

## Getting Started with Helm

### Installation

To install Helm on various platforms:
```bash
# On Ubuntu
$ sudo snap install helm --classic

# On MacOS
$ brew install helm
```
For full installation instructions, see the [Helm installation documentation](https://helm.sh/docs/intro/install/).

### Basic Helm Commands
```bash
$ helm search repo wordpress    # Find WordPress charts
$ helm install my-release bitnami/wordpress   # Install a chart
$ helm list   # List installed charts
$ helm uninstall my-release    # Uninstall a chart
```

## Helm Architecture

Helm's architecture includes:
- **Charts**: The fundamental units of Helm packaging.
- **Releases**: Managed instances of a chart deployed on the cluster.
- **Repositories**: Locations where charts can be stored and shared.

## Charts & Templating

### Chart Structure
A typical Helm chart structure includes:
- `Chart.yaml`: Basic information about the chart
- `values.yaml`: Default configuration values for the chart
- `templates/`: Kubernetes manifests with Helm templating

Templating allows for powerful dynamic configuration of resources.

### Hooks & Lifecycle Management

Helm hooks allow you to manage complex operations during deployment, upgrade, or deletion processes. Supported hooks include:
- `pre-install`, `post-install`
- `pre-upgrade`, `post-upgrade`
- `pre-delete`, `post-delete`

## Packaging & Signing Charts

Helm provides tools to package and sign charts to ensure integrity:
```bash
$ helm package ./my-chart
$ helm package --sign --key 'Your Key' --keyring ~/.gnupg/secring.gpg ./my-chart
```

## Customizing Charts

Customize chart configurations using `values.yaml` or set parameters directly with the `--set` flag:
```bash
$ helm install my-release bitnami/wordpress --set wordpressUsername=admin,wordpressPassword=secret
```

## Repository Management

Manage Helm repositories easily:
```bash
$ helm repo add bitnami https://charts.bitnami.com/bitnami
$ helm repo update
```

## Helm Commands

A list of essential Helm commands for managing applications:
```bash
$ helm install [RELEASE_NAME] [CHART]    # Deploy a chart
$ helm upgrade [RELEASE_NAME] [CHART]    # Upgrade a deployed chart
$ helm rollback [RELEASE_NAME] [REVISION]    # Rollback to a previous version
$ helm uninstall [RELEASE_NAME]    # Remove a deployed release
```

## Labs & Exercises

To solidify your understanding, try deploying applications in a Kubernetes cluster with Helm, experimenting with custom values and hooks.

## Contributing

Feel free to open issues or submit pull requests to improve this guide!

## License

This project is licensed under the MIT License.
